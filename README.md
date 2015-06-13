# callsuper-annotation

[![Build Status](http://kotcrab.com:8080/buildStatus/icon?job=callsuper)](http://kotcrab.com:8080/job/callsuper/)

Java annotation that forces you to call super method if it was annotated with CallSuper. Inspired by upcoming CallSuper annotation in Android shown at Google IO 2015. This library is currently provided as experimental version, please report any issues.

Current version: 0.1.2  
Current snapshot version: 0.1.3-SNAPSHOT

Maven:
```
<dependency>
     <groupId>com.kotcrab.annotation</groupId>
     <artifactId>callsuper</artifactId>
     <version>0.1.1-SNAPSHOT</version>
</dependency>
```

Don't forget to enable annotation processing in your IDE and build tools!

Maven:
```
<plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-compiler-plugin</artifactId>
        <version>3.3</version>
        <configuration>
                <source>1.8</source>
                <target>1.8</target>
                <annotationProcessors>
                     <annotationProcessor>com.kotcrab.annotation.callsuper.CallSuperProcessor</annotationProcessor>
                </annotationProcessors>
        </configuration>
</plugin>
```

### Usage:
```java
public class SuperClass {
	@CallSuper
	public void callMe () {
	}
}

class TestClass extends SuperClass {
	@Override //overriding method must be annotated with @Override
	public void callMe () {
		super.callMe(); //not calling super will cause error
	}
}
```

It is possible to override CallSuper check.
```java
public class SuperClass {
	@CallSuper
	public void callMe () {
	}
}

class TestClass extends SuperClass {
	@Override @OverrideCallSuper
	public void callMe () {
		//super.callMe(); //allowed, this method has @OverrideCallSuper annotation
	}
}
```
