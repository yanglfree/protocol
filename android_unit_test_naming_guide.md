# Android单元测试用例方法命名规范

## 基本原则

### 1. 清晰性和可读性
- 测试方法名应该清楚地表达测试的目的和预期结果
- 使用易于理解的英文单词，避免缩写和模糊表达
- 方法名长度适中，通常在30-80个字符之间

### 2. 一致性
- 在同一项目中保持命名风格的一致性
- 遵循团队约定的命名规范

## 推荐命名模式

### 模式一：Given_When_Then 模式
```
given[前置条件]_when[执行动作]_then[预期结果]
```

**示例：**
```java
@Test
public void givenValidUser_whenLogin_thenReturnSuccess() { }

@Test
public void givenEmptyPassword_whenLogin_thenThrowException() { }

@Test
public void givenNetworkError_whenFetchData_thenReturnError() { }
```

### 模式二：Should_When 模式
```
should[预期行为]_when[条件或触发场景]
```

**示例：**
```java
@Test
public void shouldReturnTrue_whenEmailIsValid() { }

@Test
public void shouldThrowException_whenPasswordIsEmpty() { }

@Test
public void shouldNavigateToHome_whenLoginSuccessful() { }
```

### 模式三：方法名_场景_预期结果 模式
```
[被测试方法名]_[测试场景]_[预期结果]
```

**示例：**
```java
@Test
public void validateEmail_validFormat_returnsTrue() { }

@Test
public void calculateTotal_emptyList_returnsZero() { }

@Test
public void saveUser_duplicateEmail_throwsException() { }
```

### 模式四：What_When_Then 模式
```
[测试什么]_when[什么条件下]_then[预期什么结果]
```

**示例：**
```java
@Test
public void userLogin_whenCredentialsValid_thenReturnUserObject() { }

@Test
public void dataFetch_whenNetworkUnavailable_thenReturnCachedData() { }
```

## 具体场景命名示例

### 1. 正常流程测试
```java
@Test
public void shouldCreateUser_whenAllFieldsValid() { }

@Test
public void shouldCalculateDiscount_whenUserIsVip() { }

@Test
public void shouldSendNotification_whenOrderCompleted() { }
```

### 2. 异常情况测试
```java
@Test
public void shouldThrowIllegalArgumentException_whenEmailIsNull() { }

@Test
public void shouldReturnError_whenNetworkTimeout() { }

@Test
public void shouldHandleGracefully_whenDatabaseConnectionFails() { }
```

### 3. 边界值测试
```java
@Test
public void shouldReturnEmpty_whenListIsNull() { }

@Test
public void shouldAcceptMaxValue_whenAgeIs120() { }

@Test
public void shouldRejectNegativeValue_whenPriceIsNegative() { }
```

### 4. 状态验证测试
```java
@Test
public void shouldUpdateStatus_whenPaymentProcessed() { }

@Test
public void shouldMarkAsRead_whenMessageOpened() { }

@Test
public void shouldSetLoginTime_whenUserAuthenticated() { }
```

### 5. 集成测试
```java
@Test
public void shouldReturnUserProfile_whenValidTokenProvided() { }

@Test
public void shouldSaveToDatabase_whenUserRegistered() { }

@Test
public void shouldSendEmail_whenPasswordResetRequested() { }
```

## Android特定场景

### 1. Activity/Fragment 测试
```java
@Test
public void shouldDisplayWelcomeMessage_whenActivityCreated() { }

@Test
public void shouldNavigateToNextScreen_whenButtonClicked() { }

@Test
public void shouldShowErrorDialog_whenNetworkFails() { }
```

### 2. ViewModel 测试
```java
@Test
public void shouldUpdateLiveData_whenDataLoaded() { }

@Test
public void shouldTriggerLoading_whenRefreshCalled() { }

@Test
public void shouldClearData_whenLogoutTriggered() { }
```

### 3. Repository 测试
```java
@Test
public void shouldReturnCachedData_whenNetworkUnavailable() { }

@Test
public void shouldFetchFromRemote_whenCacheExpired() { }

@Test
public void shouldSaveToLocal_whenRemoteDataReceived() { }
```

### 4. Utility 类测试
```java
@Test
public void shouldFormatCurrency_whenAmountIsValid() { }

@Test
public void shouldValidatePhoneNumber_whenFormatIsCorrect() { }

@Test
public void shouldEncryptData_whenKeyIsProvided() { }
```

## 命名规范要点

### ✅ 好的实践
- 使用小驼峰命名法（camelCase）
- 描述测试的具体行为和预期结果
- 包含足够的上下文信息
- 使用主动语态
- 避免使用 `test` 前缀（@Test 注解已经表明这是测试）

### ❌ 避免的做法
- 使用模糊的名称：`testMethod1()`, `checkSomething()`
- 过于简短：`test()`, `valid()`
- 过于冗长：超过100个字符的方法名
- 使用技术术语替代业务术语
- 重复的测试名称

## 团队协作建议

### 1. 统一规范
- 团队选择一种命名模式并保持一致
- 制定代码审查清单，包括测试命名检查
- 使用工具进行静态代码分析

### 2. 文档化
- 在项目 README 中记录选择的命名规范
- 提供具体示例供团队成员参考
- 定期回顾和更新规范

### 3. 持续改进
- 定期审查现有测试的命名质量
- 收集团队反馈，优化命名规范
- 学习业界最佳实践，保持规范的先进性

## 总结

良好的测试方法命名不仅能提高代码的可读性和维护性，还能帮助其他开发者快速理解测试的目的和范围。选择适合团队的命名模式，并在项目中保持一致性，是确保测试代码质量的重要步骤。