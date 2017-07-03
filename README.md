#  Java gradle project with Junit and JaCoCo example

*Pre-requisite: gradle and java is installed on your machine.*

1. Create a gradle project (I used Eclipse IDE)

![Image](https://github.com/shankybnl/junit-jacoco-example/blob/master/images/1.png)

2. Inside the project you will see two folders **main** and **test** under src folder. Under main you write your development  code and under test  you write your unit (Junit) tests and integration tests.

![Image](https://github.com/shankybnl/junit-jacoco-example/blob/master/images/2.png)

3. Add the below lines of code to your **build.gradle** file present in the root directory.

```java
apply plugin: "jacoco" 
```

```java 
jacocoTestReport{
    reports {
            xml.enabled false
            csv.enabled false
            html.destination "${buildDir}/jacocoHtml"
    }
}
```

If Junit dependency is not present then add it:

```java
dependencies {
     testCompile 'junit:junit:4.12'
}
```

3. Create a **Example.java** class under main folder.

```java
public class Example {
	
	 public long someRandomMethod(int a, int b) {
	    	
	    	if (a > 10 && b > 10){
	    		return a+b;
	    	}
	    	else{
	    		return a-b;
	    	}
	       
	    }
}
```
4. To verify this method, we will be writing Junit test under test folder with name **ExampleTest.java**
    *@Test* annontation tells Junit that it is a test method to execute.

```java
public class ExampleTest {

    @Test
	public void verifySomeRandomMethod() {
		Example junitTest = new Example();
		junitTest.someRandomMethod(11, 12);
	}
}
```
5. Go to the root directory of your project. And execute the below command to execute Junit test.

```java
gradle clean test
```

6. Junit results report will be generated /JunitJacocoExample/build/reports/tests/test/classes/ExampleTest.html

![Image](https://github.com/shankybnl/junit-jacoco-example/blob/master/images/5.png)


7. To generate code coverage report, execute the below command.

```java
gradle jacocoTestReport
```

8. Code coverage report will be generated /JunitJacocoExample/build/jacocoHtml/index.html

![Image](https://github.com/shankybnl/junit-jacoco-example/blob/master/images/4.png)

Code coverage at class level can be verified by navigating to **Example.java**

![Image](https://github.com/shankybnl/junit-jacoco-example/blob/master/images/3.png)

