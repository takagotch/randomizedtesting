### randomizedtesting
---
https://github.com/randomizedtesting/randomizedtesting

```java
// randomized-runner/src/test/java/com/carrotsearch/randomizedtesting/TestTargetMethod.java

public class TestTargetMethod extends WithNestedTestClass {
  public static class Nested extends RandomizedTest {
    @Before
    public void checkInHook() {
      assumeRunningNested();
    }
    
    @Test
    @Repeat(iterations = 3)
    public void testOne() {
      Assertions.assertThat(RandomizedContext.current().getTragetMethod().getName())
        .isEqualTo("testOne");
    }
    
    @Test
    public void testTwo() {
      Assertions.assertThat(RandomizedContext.current().getTargetMethod().getName())
        .isEqualTo("testTwo");
    }
    
    @AfterClass
    @BeforeClass
    public static void staticHooks() {
      Assertions.assertThat(RandomizedContext.current().getTargetMethod())
        .isNull();
    }
  }
  
  @Test
  public void testTargetMethodAvailable() {
    checkTestsOutput(4, 0, 0, 0, Nested.class);
  }
}
```

```
```

```
```


