# API Testing 🔌

## 📋 Table of Contents
1. [Introduction to API Testing](#chapter-1-introduction-to-api-testing)
2. [Fundamentals of API Testing](#chapter-2-fundamentals-of-api-testing)
3. [What to Test in API Testing](#chapter-3-what-to-test-in-api-testing)
4. [Writing Effective API Test Cases](#chapter-4-writing-effective-api-test-cases)
5. [Common API Testing Types](#chapter-5-common-api-testing-types)
6. [API Testing Tools Overview](#chapter-6-api-testing-tools-overview)
7. [Examples of API Test Cases](#chapter-7-examples-of-api-test-cases)
8. [API Testing with Postman](#chapter-8-api-testing-with-postman)
9. [API Testing with SoapUI](#chapter-9-api-testing-with-soapui)
10. [API Testing with REST Assured](#chapter-10-api-testing-with-rest-assured)
11. [Common API Testing Challenges and Solutions](#chapter-11-common-api-testing-challenges-and-solutions)
12. [API Security Testing](#chapter-12-api-security-testing)
13. [Advanced API Testing Techniques](#chapter-13-advanced-api-testing-techniques)

## Chapter 1: Introduction to API Testing 🚀
<details>
<summary>Click to expand</summary>

### 1.1 What's API testing, and why is it important? 🤔

API testing means testing Application Programming Interfaces (APIs) to test if they work as expected, meet performance standards, and handle errors. APIs handle the communication between software systems, enabling them to exchange data and functionality. 

#### Key Importance Points:

- **🎯 Logic Validation**: 
  - APIs can encapsulate the core business logic of an application
  - API testing finds out if that logic works as intended

- **🔄 Cascading Effect Prevention**: 
  - APIs often connect multiple systems
  - A failure in one API can disrupt the entire system
  - Example: In an e-commerce system, if the payment processing API fails, it affects:
    - Order confirmations
    - Inventory updates
    - Customer notifications
    - Financial records

- **🔗 Integration Validation**: 
  - APIs handle the interactions between different systems
  - Testing these interactions for correctness, reliability, performance and security is critical

- **🐛 Early Bug Detection**: 
  - Testing APIs before UI completion helps identify defects earlier
  - Reduces downstream issues

### 1.2 Primary Focus Areas of API Testing 🎯

#### Core Testing Areas:

| Focus Area | Description | Example |
|------------|-------------|----------|
| **Functionality** ⚙️ | Testing if API executes intended operations | getUserDetails API returns correct user data |
| **Performance** ⚡ | Validating speed and responsiveness | API responds within 300ms for 100 concurrent requests |
| **Security** 🔒 | Checking data protection mechanisms | Unauthorized users cannot access restricted endpoints |
| **Reliability** 💪 | Confirming consistent results | Weather API always returns accurate temperature |

### 1.3 Testing Classification 📊

#### Functional vs Non-Functional Testing

API testing encompasses both functional and non-functional aspects:

- **Functional Testing** ✅
  - Main objective: Validate API performs expected functions
  - Focus: Core functionality and business logic

- **Non-Functional Testing** 📈
  - **Performance Testing**:
    - Measures API responsiveness
    - Example: Load testing ticket booking API during flash sales
  - **Security Testing**:
    - Validates data confidentiality
    - Tests for vulnerabilities (SQL injection, unauthorized access)

### 1.4 API Testing vs UI Testing Comparison 🔄

| Aspect | API Testing 🔌 | UI Testing 🖥️ |
|--------|--------------|------------|
| Scope | Backend systems and business logic | User interface interactions |
| Speed | Faster (bypasses GUI) | Slower (rendering processes) |
| Reliability | More stable, less flaky | Prone to UI element changes |
| Example | Verifying createOrder API | Testing Place Order button |

### 1.5 Test Levels 📊

#### Integration Testing
- Primary classification for API testing
- Focus: Component interaction validation
- Example: Testing payment gateway integration
  - Communication verification
  - Data exchange accuracy
  - Alternate workflow handling

#### System Testing
- Secondary classification
- Focus: End-to-end workflow validation
- Example: Order management system
  - Inventory API
  - Payment API
  - Customer notification API

### 1.6 Importance of Classification 🎯

Proper classification helps determine:

- **Test Scope** 📋
  - Integration testing: Focus on inter-component communication
  - System testing: Test APIs in larger workflows

- **Test Approach** 🎯
  - Different strategies based on classification
  - Ensures comprehensive coverage

</details>

## Chapter 2: Fundamentals of API Testing 🔍
<details>
<summary>Click to expand</summary>

### 2.1 Key Concepts for QA Professionals 📚

#### 2.1.1 Endpoints 🎯
- URLs where APIs are accessed
- Example: `https://api.weather.com/v1/city/temperature`
- 💡 **Tip**: Document endpoints clearly, including:
  - Required parameters
  - Response formats
  - Authentication requirements

#### 2.1.2 HTTP Methods and Requests 🔄

| Method | Purpose | Example |
|--------|---------|----------|
| **GET** 📥 | Retrieve data | `GET /user/{id}` to fetch user details |
| **POST** ➕ | Create new data | `POST /user` to create new user |
| **PUT** 🔄 | Update existing data | `PUT /user/{id}` to update user details |
| **DELETE** ❌ | Remove data | `DELETE /user/{id}` to remove user |

💡 **Tip**: Always verify strict adherence to HTTP method conventions

#### 2.1.3 Request Components 📦

##### Parameters Types:
1. **Query Parameters** 🔍
   - Added to URL: `?userId=123`
   - Used mainly with GET requests
   
2. **Body Parameters** 📝
   - Sent in request body
   - Example: JSON payload for POST requests
   ```json
   {
     "username": "john_doe",
     "email": "john@example.com"
   }
   ```

💡 **Tip**: Test edge cases:
- Missing parameters
- Invalid values
- Boundary conditions

#### 2.1.4 Response and Status Codes 📊

| Status Code | Meaning | Scenario |
|-------------|---------|----------|
| **200** ✅ | OK | Successful request |
| **201** ➕ | Created | Resource created successfully |
| **400** ⚠️ | Bad Request | Client-side error |
| **401** 🔒 | Unauthorized | Invalid/missing authentication |
| **500** ❌ | Internal Server Error | API failure |

#### 2.1.5 Headers 📋
- Carry metadata for requests/responses
- Common headers:
  - `Authorization: Bearer <token>`
  - `Content-Type: application/json`
  - `Cache-Control: no-cache`

💡 **Tip**: Always validate:
- Header presence
- Correct format
- Required values

#### 2.1.6 Assertions ✅
Key validation points:
1. **Status Code Validation** 📊
   - Verify expected response codes
   - Handle error scenarios

2. **Response Body Checks** 📝
   - Data format validation
   - Content accuracy verification

3. **Performance Metrics** ⚡
   - Response time validation
   - Throughput verification

💡 **Tip**: Leverage testing frameworks:
- REST Assured
- Postman
- JUnit/TestNG

### 2.2 Importance in Modern Development 🌐

#### 2.2.1 Core Application Functionality 🎯
- APIs drive key features:
  - User authentication
  - Data retrieval
  - Payment processing
- **Example**: Banking app APIs:
  - Balance checking
  - Fund transfers
  - Transaction history

#### 2.2.2 System Integration 🔄
- **Purpose**: Connect multiple systems
- **Example**: Ride-sharing app integration:
  - User location API
  - Driver availability API
  - Payment processing API

#### 2.2.3 Early Testing Benefits ⏱️
- Test before UI completion
- Earlier bug detection
- Reduced development costs
- **Example**: E-commerce cart API testing before UI finalization

#### 2.2.4 Microservices Support 🔌
- Independent service testing
- Communication validation
- **Example**: Video streaming platform:
  - Authentication service
  - Content delivery API
  - Recommendation engine

#### 2.2.5 Performance and Scalability 📈
- High traffic handling
- Large dataset processing
- **Example**: E-commerce during sales:
  - Concurrent user management
  - Cart operation handling
  - Order processing

### 2.3 Best Practices and Tips 💡

#### 2.3.1 Testing Approach
1. **Use Mock Servers** 🔄
   - Test without production dependencies
   - Simulate various scenarios

2. **Comprehensive Testing** 🎯
   - Test happy paths
   - Validate negative scenarios
   - Check error handling

3. **Test Automation** ⚙️
   - Automate repetitive tests
   - Use tools:
     - REST Assured
     - Postman
     - SoapUI

#### 2.3.2 Documentation 📝
- Maintain clear API documentation
- Include test scenarios
- Document edge cases
- Keep examples updated

</details>

## Chapter 3: What to Test in API Testing 🎯
<details>
<summary>Click to expand</summary>

### 3.1 Functional Testing Approach 🔍

#### 3.1.1 Endpoint Validation ⚡
- Verify API endpoints respond as expected
- **Example**: 
  ```http
  GET /user/{id}
  ```
  - Validates correct user details retrieval
  - Checks response format
  - Verifies data accuracy

#### 3.1.2 Input Validation 📝
| Test Type | Description | Example |
|-----------|-------------|----------|
| **Valid Inputs** ✅ | Test with correct data | Valid email: `user@example.com` |
| **Invalid Inputs** ❌ | Test with incorrect data | Invalid date: `32-13-2025` |
| **Boundary Values** 🔄 | Test limits | Max string length: `255 characters` |

#### 3.1.3 Business Logic Testing 💼
- Validate business rules implementation
- **Example**: E-commerce coupon validation
  ```http
  POST /applyCoupon
  ```
  - Verify discount eligibility
  - Check product restrictions
  - Validate discount calculations

#### 3.1.4 Dependency Validation 🔗
- Test service interactions
- **Example**: Payment gateway integration
  - Success scenarios
  - Failure handling
  - Timeout management

💡 **Tip**: 
- Use Postman for functional test design
- Implement REST Assured for test automation

### 3.2 Response Validation 📊

#### 3.2.1 Status Code Verification ✨
| Code | Scenario | Validation |
|------|----------|------------|
| **200** ✅ | Success | Verify successful operations |
| **404** 🔍 | Not Found | Check resource existence |
| **500** ⚠️ | Server Error | Validate error handling |

#### 3.2.2 Response Body Analysis 📝
1. **Structure Validation**
   - Data type verification
   - Required fields presence
   ```json
   {
     "name": "string",
     "email": "string",
     "age": "integer"
   }
   ```

2. **Schema Validation** 📋
   - Use JSON Schema Validator
   - Automate validation process
   
3. **Data Accuracy** ✅
   - Compare with database records
   - Verify calculations
   - **Example**: Product price validation
     ```http
     GET /product/{id}
     ```

#### 3.2.3 Error Response Testing ⚠️
- Verify error message clarity
- Check consistency
- **Example**: Missing parameter
  ```json
  {
    "error": "Missing parameter 'email'",
    "code": "MISSING_PARAM"
  }
  ```

### 3.3 Security Testing 🔒

#### 3.3.1 Authentication & Authorization 🔑
- Test authentication methods
  - OAuth
  - API keys
  - JWT tokens
- Verify RBAC implementation
  ```http
  DELETE /user/{id}  // Admin only
  ```

#### 3.3.2 Security Measures 🛡️
| Test Type | Purpose | Example |
|-----------|---------|----------|
| **Input Sanitization** 🧹 | Prevent injections | Test: `'; DROP TABLE users;--` |
| **Data Encryption** 🔐 | Secure transmission | Verify HTTPS usage |
| **Rate Limiting** ⏱️ | Prevent abuse | Test: `429 Too Many Requests` |

#### 3.3.3 Token Management 🎟️
- Test token lifecycle
  - Expiration handling
  - Revocation process
  - Refresh mechanisms

💡 **Tip**: Utilize security tools:
- OWASP ZAP
- Burp Suite

### 3.4 Performance Testing ⚡

#### 3.4.1 Response Time Testing ⏱️
- Measure API speed
- **Target**: `< 200ms` for critical endpoints
- **Example**: Weather API
  ```http
  GET /currentWeather
  ```

#### 3.4.2 Load Testing Types 📈

| Test Type | Purpose | Example Scenario |
|-----------|---------|-----------------|
| **Load** 👥 | Normal conditions | 100 concurrent users |
| **Stress** 💪 | Breaking point | Gradual request increase |
| **Spike** ⚡ | Sudden surges | Flash sale simulation |

#### 3.4.3 Resource Monitoring 📊
- Track server metrics:
  - CPU usage
  - Memory consumption
  - Network utilization
- **Example**: Bulk operations
  ```http
  POST /uploadBulkData
  ```

#### 3.4.4 Caching Efficiency 🚀
- Verify caching implementation
- Test cache hit/miss rates
- **Example**: Product image caching
  ```http
  GET /product/image/{id}
  ```

💡 **Tip**: Performance testing tools:
- JMeter
- Gatling
- Monitor key metrics:
  - Latency
  - Throughput
  - Error rates

</details>

## Chapter 4: Writing Effective API Test Cases ✍️
<details>
<summary>Click to expand</summary>

### 4.1 Best Practices for Test Case Writing 📝

#### 4.1.1 Understanding API Specifications 📚
- Study API documentation thoroughly
- Review key components:
  - Endpoint definitions
  - Request/response formats
  - Authentication methods
- **Example**: `GET /user/{id}`
  ```http
  GET /user/{id}
  Authorization: Bearer {token}
  ```

#### 4.1.2 Test Scenario Identification 🎯

| Scenario Type | Purpose | Example |
|--------------|---------|----------|
| **Positive Tests** ✅ | Validate expected behavior | Valid user ID retrieval |
| **Negative Tests** ❌ | Check error handling | Invalid user ID handling |
| **Edge Cases** 🔄 | Test boundaries | Maximum page size testing |

💡 **Tip**: Create a test scenario matrix for comprehensive coverage

#### 4.1.3 Modular Approach 🧩
- Create reusable components
- **Example**: Authentication Module
  ```javascript
  function getAuthToken() {
    // Reusable authentication logic
    return authToken;
  }
  ```

#### 4.1.4 Assertion Implementation ✅
- Verify multiple aspects:
  - Status codes
  - Response times
  - Data accuracy
- **Example**: Response Time Check
  ```javascript
  assert.responseTime < 200; // Milliseconds
  ```

#### 4.1.5 Test Automation Strategy ⚙️
- Tools recommendation:
  - REST Assured
  - Postman
  - JUnit
- Focus on regression tests
- Implement CI/CD integration

### 4.2 Input and Output Definition 📊

#### 4.2.1 Input Parameters 📥

##### Mandatory Parameters
```json
{
  "required": {
    "name": "string",
    "email": "string"
  }
}
```

##### Optional Parameters
```json
{
  "optional": {
    "age": "integer",
    "phone": "string"
  }
}
```

#### 4.2.2 Input Types Testing 🔄

| Input Category | Test Cases | Examples |
|----------------|------------|----------|
| **Valid Data** ✅ | Correct formats | `email: "user@example.com"` |
| **Invalid Data** ❌ | Wrong formats | `email: "invalid-email"` |
| **Null Values** ⚠️ | Empty fields | `phone: null` |

#### 4.2.3 Expected Outputs 📤

##### Success Response
```json
{
  "status": 200,
  "body": {
    "id": 101,
    "message": "User created successfully"
  },
  "headers": {
    "Content-Type": "application/json"
  }
}
```

##### Error Response
```json
{
  "status": 400,
  "body": {
    "error": "Invalid email format",
    "code": "INVALID_INPUT"
  }
}
```

### 4.3 Test Case Template Structure 📋

#### 4.3.1 Basic Template Components

| Section | Description | Example |
|---------|-------------|----------|
| **Test ID** 🔢 | Unique identifier | `API_TC_001` |
| **Title** 📌 | Brief description | "Verify user creation" |
| **Preconditions** ⚡ | Required setup | "Valid auth token exists" |
| **Steps** 📝 | Test execution steps | 1. Call POST /user<br>2. Verify response |
| **Expected Results** ✅ | Success criteria | "User created, status 201" |
| **Actual Results** 📊 | Test outcomes | "Matches expected" |
| **Status** 🎯 | Test case state | "Passed/Failed" |

#### 4.3.2 Detailed Template Example

```markdown
### Test Case: API_TC_001 📝

**Title**: Create New User with Valid Data
**Priority**: High 🔴
**Category**: Functional

**Preconditions**:
- Valid authentication token
- Test database is accessible

**Test Data**:
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "age": 30
}
```

**Steps**:
1. Set request headers
2. Prepare request payload
3. Send POST request to /users
4. Verify response

**Expected Results**:
- Status Code: 201
- Response contains user ID
- User exists in database

**Notes**: 
- Verify email notification
- Check audit logs

💡 **Tips for Template Usage**:
- Maintain consistency across test cases
- Include all necessary details
- Use clear, concise language
- Add relevant screenshots/logs
- Link to requirements

#### 4.3.3 Test Management Tools 🛠️
- Recommended platforms:
  - Jira Test Management
  - TestRail
  - qTest
  - Zephyr

</details>

## Chapter 5: Common API Testing Types 🧪
<details>
<summary>Click to expand</summary>

### 5.1 Functional Testing 🎯

#### 5.1.1 Core Concepts
- Validates API functionality
- Tests expected behavior
- Verifies input/output accuracy

#### 5.1.2 Key Testing Areas

| Area | Description | Example |
|------|-------------|----------|
| **Endpoint Validation** 🔍 | Test endpoint functionality | `GET /user/{id}` returns correct user |
| **Parameter Testing** ⚙️ | Validate input parameters | Test missing username in login |
| **Response Validation** ✅ | Verify response structure | Check `Content-Type: application/json` |

💡 **Testing Tips**:
- Implement data-driven testing
- Automate with REST Assured/Postman
- Document test scenarios thoroughly

### 5.2 Load Testing ⚡

#### 5.2.1 Process Overview
1. **Benchmark Setting** 📊
   - Define performance targets
   - Example: 500 concurrent product searches

2. **Load Simulation** 👥
   ```javascript
   // JMeter Test Plan Example
   Thread Group {
     Users: 200
     Ramp-up: 30s
     Target: GET /products
   }
   ```

3. **Performance Monitoring** 📈
   | Metric | Target | Example |
   |--------|---------|----------|
   | Response Time | < 1s | Product search latency |
   | CPU Usage | < 80% | Server resource utilization |
   | Throughput | > 100 TPS | Transactions per second |

#### 5.2.2 Common Issues
- Slow database queries
- Server resource exhaustion
- Connection pool limits

💡 **Best Practices**:
- Test with realistic data
- Include peak load scenarios
- Monitor all system components

### 5.3 Security Testing 🔒

#### 5.3.1 Critical Security Areas

| Test Type | Purpose | Example |
|-----------|---------|----------|
| **Authentication** 🔑 | Verify access control | OAuth2 implementation |
| **Input Validation** 🛡️ | Prevent injections | SQL injection testing |
| **Data Privacy** 🔐 | Protect sensitive data | HTTPS implementation |
| **Rate Limiting** ⏱️ | Prevent abuse | Request throttling |

#### 5.3.2 Security Test Cases
```http
# Authentication Test
GET /admin/users
Authorization: Bearer invalid_token
Expected: 401 Unauthorized

# SQL Injection Test
POST /login
{
  "username": "' OR 1=1--",
  "password": "anything"
}
Expected: 400 Bad Request
```

💡 **Security Tools**:
- OWASP ZAP
- Burp Suite
- Custom security scripts

### 5.4 Interoperability Testing 🔄

#### 5.4.1 Testing Scope

| Aspect | Focus Area | Example |
|--------|------------|----------|
| **Protocol** 📡 | Format compatibility | JSON/XML support |
| **Integration** 🔌 | Third-party services | Payment gateway integration |
| **Platform** 💻 | Cross-platform support | Windows/Linux/macOS |

#### 5.4.2 Common Challenges
- Inconsistent data formats
- Version compatibility
- Platform-specific issues

💡 **Testing Tips**:
- Use mock servers
- Test all supported formats
- Validate cross-platform behavior

### 5.5 Contract Testing 📋

#### 5.5.1 Implementation Steps

1. **Contract Definition** 📝
   ```yaml
   # OpenAPI Specification Example
   /users:
     get:
       responses:
         200:
           schema:
             type: object
             properties:
               id: integer
               name: string
   ```

2. **Provider Validation** ✅
   - Verify API implementation
   - Check response structure
   - Validate data types

3. **Consumer Testing** 👥
   - Frontend compatibility
   - Data parsing verification
   - Display testing

#### 5.5.2 Testing Tools
- PACT Framework
- Postman
- Swagger Validator

💡 **Best Practices**:
- Keep contracts updated
- Automate in CI/CD
- Test both provider and consumer
- Document changes clearly

</details>

## Chapter 6: API Testing Tools Overview 🛠️
<details>
<summary>Click to expand</summary>

### 6.1 Postman Overview 📮

#### 6.1.1 Key Features
| Feature | Description | Example |
|---------|-------------|----------|
| **Collections** 📁 | Organize test cases | Group CRUD operations for user API |
| **Environments** 🌍 | Manage different configs | Dev, staging, production setups |
| **Scripting** 📝 | Pre-request & test scripts | Response validation with JavaScript |
| **Automation** ⚙️ | CI/CD integration | Newman for automated runs |

#### 6.1.2 Environment Management
```javascript
// Environment Variables Example
{
    "development": {
        "baseUrl": "https://dev-api.example.com",
        "authToken": "",
        "timeout": 5000
    },
    "production": {
        "baseUrl": "https://api.example.com",
        "authToken": "",
        "timeout": 3000
    }
}
```

#### 6.1.3 Initial API Test ✅
```http
GET {{baseUrl}}/health
Expected Response: 200 OK
{
    "status": "healthy",
    "timestamp": "2025-01-20T16:53:14Z"
}
```

💡 **Setup Tips**:
- Use version control for collections
- Share environments securely
- Never commit sensitive data
- Use variables for dynamic values

### 6.2 SoapUI Deep Dive 🧼

#### 6.2.1 Setup and Configuration
1. **Installation** 💿
   - Download SoapUI Open Source
   - Or install ReadyAPI for advanced features
   
2. **Project Creation** 🏗️
   - Import WSDL/OpenAPI specs
   - Configure project settings
   - Set up environments

#### 6.2.2 Test Components

| Component | Purpose | Example |
|-----------|---------|----------|
| **Test Steps** 📝 | Define test sequence | Login → Get Token → Access Resource |
| **Assertions** ✅ | Validate responses | Check status code, response time |
| **Data Sources** 📊 | External test data | Excel sheets, databases |

#### 6.2.3 Advanced Features
```groovy
// Groovy Script Example for Custom Logic
def response = context.expand('${LoginStep#Response}')
def token = new groovy.json.JsonSlurper().parseText(response).token
testRunner.testCase.setPropertyValue("authToken", token)
```

💡 **SoapUI Tips**:
- Use Groovy for complex scenarios
- Integrate with CI tools
- Keep specifications updated
- Implement security testing

### 6.3 REST Assured Framework 🤖

#### 6.3.1 Setup
```xml
<!-- Maven Dependency -->
<dependency>
    <groupId>io.rest-assured</groupId>
    <artifactId>rest-assured</artifactId>
    <version>5.3.0</version>
    <scope>test</scope>
</dependency>
```

#### 6.3.2 Test Structure
```java
// Basic Test Example
public class ApiTest {
    
    @Test
    public void getUserTest() {
        given()
            .baseUri("https://api.example.com")
            .header("Authorization", "Bearer " + token)
        .when()
            .get("/user/{id}", userId)
        .then()
            .statusCode(200)
            .body("name", equalTo("John Doe"))
            .body("email", notNullValue());
    }
}
```

#### 6.3.3 Advanced Features

| Feature | Description | Example |
|---------|-------------|----------|
| **Request Chaining** 🔗 | Link multiple requests | Login → Use token in next request |
| **Parameterization** 📊 | Dynamic test data | Path params, query params |
| **Response Extraction** 📤 | Parse response data | JSON path, XML path |
| **Authentication** 🔐 | Various auth methods | OAuth2, Basic Auth |

#### 6.3.4 Best Practices Framework
```java
// POM-based API Resource Class
public class UserApi {
    private static final String USERS_ENDPOINT = "/users";
    
    public Response createUser(User user) {
        return given()
            .body(user)
        .when()
            .post(USERS_ENDPOINT)
        .then()
            .extract().response();
    }
}
```

💡 **REST Assured Tips**:
- Enable request/response logging
  ```java
  RestAssured.enableLoggingOfRequestAndResponseIfValidationFails();
  ```
- Use specification builders
- Implement reusable components
- Follow POM design pattern

#### 6.3.5 Tool Comparison Matrix 📊

| Feature | Postman | SoapUI | REST Assured |
|---------|---------|--------|--------------|
| **UI Interface** 🖥️ | Excellent | Good | N/A (Code-based) |
| **Learning Curve** 📈 | Low | Medium | High |
| **Automation** ⚙️ | Good | Excellent | Excellent |
| **CI/CD Integration** 🔄 | Via Newman | Native | Native |
| **Enterprise Usage** 💼 | High | High | High |
| **Cost** 💰 | Free/Premium | Free/Premium | Free |

</details>

## Chapter 7: Examples of API Test Cases 📝
<details>
<summary>Click to expand</summary>

### 7.1 Common API Test Scenarios 🎯

#### 7.1.1 Status Code Validation ✅
```http
GET /user/123
Expected: 200 OK

GET /user/999
Expected: 404 Not Found
```

#### 7.1.2 Response Time Checks ⏱️
```javascript
pm.test("Response time check", () => {
    pm.expect(pm.response.responseTime).to.be.below(500);
});
```

#### 7.1.3 Header Validation 📋
| Header | Expected Value | Example |
|--------|---------------|----------|
| **Content-Type** 📄 | `application/json` | Response format verification |
| **Authorization** 🔑 | `Bearer <token>` | Authentication check |
| **Cache-Control** 🔄 | `no-cache` | Caching policy |

#### 7.1.4 Pagination Testing 📚
```http
GET /users?page=2&size=10
Expected Response:
{
    "users": [...],  // exactly 10 items
    "totalPages": 5,
    "currentPage": 2,
    "totalItems": 48
}
```

💡 **Testing Tips**:
- Validate first/last pages
- Check edge cases (page=0, negative size)
- Verify total count accuracy

### 7.2 Authentication Test Cases 🔐

#### 7.2.1 Login Scenarios

##### Successful Login 🟢
```json
// Request
POST /login
{
    "username": "testuser",
    "password": "password123"
}

// Expected Response
{
    "status": 200,
    "token": "eyJhbGciOiJIUzI1NiIs...",
    "expiresIn": 3600
}
```

##### Failed Login 🔴
```json
// Request
POST /login
{
    "username": "testuser",
    "password": "wrongpass"
}

// Expected Response
{
    "status": 401,
    "error": "Invalid credentials"
}
```

#### 7.2.2 Authorization Tests 🛡️

| Scenario | Request | Expected Result |
|----------|---------|-----------------|
| **Admin Access** 👑 | `POST /admin/users` | 200 OK for admin, 403 for others |
| **Guest Access** 👤 | `GET /public/data` | 200 OK for all users |
| **Expired Token** ⏰ | Any authenticated request | 401 Unauthorized |

#### 7.2.3 Logout Validation 🚪
```http
1. POST /logout
   Expected: 200 OK

2. GET /protected-resource
   Expected: 401 Unauthorized
```

### 7.3 CRUD Operations Examples ⚙️

#### 7.3.1 Create (POST) 📥
```json
// Request
POST /api/products
{
    "name": "New Product",
    "price": 99.99,
    "category": "electronics"
}

// Expected Response
{
    "id": "123",
    "name": "New Product",
    "price": 99.99,
    "category": "electronics",
    "createdAt": "2025-01-20T16:51:22Z"
}
```

#### 7.3.2 Read (GET) 📖
```http
GET /api/products/123

Expected Response:
{
    "id": "123",
    "name": "New Product",
    "price": 99.99,
    "category": "electronics"
}
```

#### 7.3.3 Update (PUT) 🔄
```json
// Request
PUT /api/products/123
{
    "name": "Updated Product",
    "price": 149.99,
    "category": "electronics"
}

// Validation Steps:
1. Verify 200 OK response
2. Check all fields are updated
3. Verify timestamp changes
```

#### 7.3.4 Partial Update (PATCH) 🔨
```json
// Request
PATCH /api/products/123
{
    "price": 179.99
}

// Expected:
1. Only price is updated
2. Other fields remain unchanged
```

#### 7.3.5 Delete (DELETE) 🗑️
```http
1. DELETE /api/products/123
   Expected: 204 No Content

2. GET /api/products/123
   Expected: 404 Not Found
```

💡 **CRUD Testing Best Practices**:
- Use test environments
- Verify database state
- Check related entities
- Test cascade operations
- Maintain test data integrity

#### 7.3.6 Test Data Matrix 📊

| Operation | Success Case | Error Case | Edge Case |
|-----------|-------------|------------|------------|
| **CREATE** ➕ | Valid data | Duplicate entry | Max field lengths |
| **READ** 👀 | Existing ID | Non-existent ID | Special characters |
| **UPDATE** 🔄 | Full update | Invalid fields | Concurrent updates |
| **PATCH** 🔨 | Partial update | Invalid patch | Empty patch |
| **DELETE** ❌ | Existing record | Already deleted | Cascade delete |

</details>

## Chapter 8: API Testing with Postman 📨
<details>
<summary>Click to expand</summary>

### 8.1 Setting Up Postman 🛠️

#### 8.1.1 Installation and Setup Steps 📥
1. Download and install Postman
2. Create an account
3. Set up workspace
4. Import API specifications
5. Configure environments

#### 8.1.2 Environment Configuration 🌍
```json
{
    "development": {
        "baseUrl": "https://dev-api.example.com",
        "authToken": "",
        "timeout": 5000
    },
    "production": {
        "baseUrl": "https://api.example.com",
        "authToken": "",
        "timeout": 3000
    }
}
```

#### 8.1.3 Initial API Test ✅
```http
GET {{baseUrl}}/health
Expected Response: 200 OK
{
    "status": "healthy",
    "timestamp": "2025-01-20T16:53:14Z"
}
```

💡 **Setup Tips**:
- Use version control for collections
- Share environments securely
- Never commit sensitive data
- Use variables for dynamic values

### 8.2 Test Script Automation 🤖

#### 8.2.1 Basic Assertions
```javascript
// Status Code Check
pm.test("Status code is 200", () => {
    pm.response.to.have.status(200);
});

// Response Time Check
pm.test("Response time is acceptable", () => {
    pm.expect(pm.response.responseTime).to.be.below(500);
});
```

#### 8.2.2 Response Validation
```javascript
// Body Content Check
pm.test("Verify user data", () => {
    const response = pm.response.json();
    pm.expect(response.user).to.be.an('object');
    pm.expect(response.user.name).to.eql("John Doe");
    pm.expect(response.user.email).to.match(/@.*\./);
});

// Header Validation
pm.test("Content-Type is present", () => {
    pm.response.to.have.header("Content-Type");
    pm.expect(pm.response.headers.get("Content-Type"))
        .to.include("application/json");
});
```

#### 8.2.3 Dynamic Data Handling 🔄
```javascript
// Extract and Store Token
const response = pm.response.json();
pm.environment.set("authToken", response.token);

// Use Token in Request
pm.request.headers.add({
    key: "Authorization",
    value: `Bearer ${pm.environment.get("authToken")}`
});
```

#### 8.2.4 Error Handling
```javascript
try {
    const response = pm.response.json();
    pm.test("Data validation", () => {
        pm.expect(response.data).to.be.an('array');
        pm.expect(response.data.length).to.be.above(0);
    });
} catch (e) {
    console.error("Error in test script:", e.message);
    pm.test("Test failed due to error", () => {
        pm.expect.fail(e.message);
    });
}
```

### 8.3 Collection Management 📚

#### 8.3.1 Collection Structure 🗂️
```
User Management APIs/
├── Authentication/
│   ├── Login
│   └── Logout
├── Users/
│   ├── Get All Users
│   ├── Get User by ID
│   ├── Create User
│   ├── Update User
│   └── Delete User
└── Settings/
    └── Environment Variables
```

#### 8.3.2 Pre-request Scripts
```javascript
// Add Authentication Header
if (pm.environment.get("authToken")) {
    pm.request.headers.add({
        key: "Authorization",
        value: `Bearer ${pm.environment.get("authToken")}`
    });
}

// Add Timestamp
pm.request.headers.add({
    key: "X-Request-Time",
    value: new Date().toISOString()
});
```

#### 8.3.3 Collection Runner Configuration 🏃
| Setting | Value | Description |
|---------|-------|-------------|
| **Iterations** 🔄 | 1-n | Number of test runs |
| **Delay** ⏱️ | 500ms | Time between requests |
| **Data File** 📄 | `test-data.csv` | Test data source |
| **Environment** 🌍 | Development | Target environment |

#### 8.3.4 Newman CLI Commands 💻
```bash
# Run Collection with Environment
newman run MyCollection.json -e Dev.json

# Generate HTML Report
newman run MyCollection.json -r html,cli

# Run with Data File
newman run MyCollection.json -d testData.csv
```

💡 **Collection Management Best Practices**:
- Use descriptive request names
- Group related requests in folders
- Include example responses
- Document request parameters
- Keep collections up-to-date
- Share collections via version control

#### 8.3.5 Collection Documentation 📝
| Section | Content | Purpose |
|---------|----------|---------|
| **Overview** 📋 | Collection purpose | Quick introduction |
| **Prerequisites** ⚙️ | Setup requirements | Environment setup |
| **Authentication** 🔐 | Auth methods | Security setup |
| **Examples** 💡 | Request/Response | Usage examples |
| **Variables** 🔄 | Environment vars | Configuration |

</details>

## Chapter 9: API Testing with SoapUI 🚿
<details>
<summary>Click to expand</summary>

### 9.1 Introduction to SoapUI 🌟

#### 9.1.1 Key Features
| Feature | Description | Benefit |
|---------|-------------|----------|
| **Dual Protocol Support** 🔄 | SOAP and REST APIs | Test legacy and modern APIs |
| **GUI Interface** 🖥️ | User-friendly interface | Easy learning curve |
| **Advanced Assertions** ✅ | Built-in validation tools | Comprehensive testing |
| **Data Drive Testing** 📊 | External data sources | Scalable test scenarios |
| **CI/CD Integration** 🔄 | Jenkins, TeamCity support | Automated pipelines |

💡 **Why Choose SoapUI**:
- Comprehensive testing capabilities
- Strong community support
- Enterprise-grade features
- Extensive documentation
- Cross-platform compatibility

### 9.2 Creating Test Cases 📝

#### 9.2.1 Project Setup Steps
1. Launch SoapUI
2. Create new project:
   ```
   File > New SOAP/REST Project
   Base URL: https://api.example.com
   ```
3. Import API definition (WSDL/OpenAPI)
4. Configure project settings

#### 9.2.2 Test Suite Structure 🗂️
```
MyAPI Project/
├── TestSuite_Authentication/
│   ├── TestCase_Login
│   │   ├── Request: POST /login
│   │   └── Assertions: Status, Token
│   └── TestCase_Logout
├── TestSuite_Users/
│   ├── TestCase_CreateUser
│   ├── TestCase_GetUser
│   └── TestCase_UpdateUser
└── TestSuite_Products/
    └── TestCase_SearchProducts
```

#### 9.2.3 Request Configuration
```json
// POST /users Request
{
    "method": "POST",
    "endpoint": "/users",
    "headers": {
        "Content-Type": "application/json",
        "Authorization": "${#TestCase#authToken}"
    },
    "body": {
        "name": "Jane Doe",
        "email": "jane.doe@example.com",
        "role": "user"
    }
}
```

#### 9.2.4 Assertions Examples
```groovy
// Status Code Assertion
assert response.statusCode == 200

// JSON Content Assertion
def json = new groovy.json.JsonSlurper().parseText(response)
assert json.email == "jane.doe@example.com"

// Response Time Assertion
assert response.time < 1000
```

### 9.3 Test Automation 🤖

#### 9.3.1 Groovy Scripts
```groovy
// Extract and Store Token
def extractToken() {
    def response = context.expand('${LoginStep#Response}')
    def json = new groovy.json.JsonSlurper().parseText(response)
    testRunner.testCase.setPropertyValue("authToken", json.token)
}

// Custom Validation
def validateUserData() {
    def response = context.response
    def json = new groovy.json.JsonSlurper().parseText(response)
    
    assert json.name != null : "Name is required"
    assert json.email.contains("@") : "Invalid email format"
    log.info "User validation passed"
}
```

#### 9.3.2 Property Transfer
```groovy
// Transfer auth token between requests
def sourceStep = testRunner.testCase.getTestStepByName("Login")
def targetStep = testRunner.testCase.getTestStepByName("GetUserProfile")
def token = sourceStep.getPropertyValue("Response.token")
targetStep.setPropertyValue("Request.header.Authorization", "Bearer " + token)
```

#### 9.3.3 Test Runner Commands 💻
```bash
# Run Specific Test Suite
testrunner.sh -s"Authentication_TestSuite" MyProject.xml

# Run with Environment
testrunner.sh -e"Development" -r -f"./reports" MyProject.xml

# Run Multiple Test Cases
testrunner.sh -c"Login,CreateUser" -r MyProject.xml
```

#### 9.3.4 CI/CD Integration
```yaml
# Jenkins Pipeline Example
pipeline {
    agent any
    stages {
        stage('API Tests') {
            steps {
                sh '''
                    /opt/SoapUI/bin/testrunner.sh \
                    -s"Regression_TestSuite" \
                    -r -j \
                    -f"./test-reports" \
                    MyProject.xml
                '''
            }
        }
    }
    
    post {
        always {
            cleanWs()
        }
        failure {
            slackSend channel: '#api-testing',
                      message: "Pipeline Failed: ${env.JOB_NAME} [${env.BUILD_NUMBER}]"
        }
    }
}
```

#### 9.3.5 Test Report Structure 📊
| Section | Content | Purpose |
|---------|----------|---------|
| **Summary** 📈 | Pass/Fail counts | Quick overview |
| **Timeline** ⏱️ | Execution times | Performance analysis |
| **Details** 📝 | Step-by-step results | Debugging |
| **Logs** 📄 | Error messages | Troubleshooting |
| **Coverage** 🎯 | API coverage metrics | Quality metrics |

💡 **Automation Best Practices**:
- Use environment-specific properties
- Implement proper error handling
- Create reusable test components
- Maintain clear naming conventions
- Regular backup of project files
- Document complex test scenarios

#### 9.3.6 Test Data Management 📊
| Section | Content | Purpose |
|---------|----------|---------|
| **Data Sources** 📄 | External data files | Data-driven testing |
| **Data Profiles** 📈 | Environment-specific data | Configuration management |
| **Data Encryption** 🔐 | Secure data storage | Data protection |

💡 **Data Management Tips**:
- Use version control for data files
- Implement data masking
- Regularly update data sources
- Use data validation
- Document data sources

</details>

## Chapter 10: API Testing with REST Assured 🤖
<details>
<summary>Click to expand</summary>

### 10.1 Introduction to REST Assured 🌟

#### 10.1.1 Key Features
| Feature | Description | Benefit |
|---------|-------------|----------|
| **Fluent API** 📝 | BDD-style syntax | Readable test code |
| **Built-in Validation** ✅ | Comprehensive assertions | Robust testing |
| **Format Support** 📄 | JSON/XML handling | Versatile testing |
| **CI/CD Ready** 🔄 | Pipeline integration | Automated testing |
| **Auth Support** 🔐 | Multiple auth methods | Secure testing |

#### 10.1.2 Maven Dependencies
```xml
<!-- REST Assured Core -->
<dependency>
    <groupId>io.rest-assured</groupId>
    <artifactId>rest-assured</artifactId>
    <version>5.3.0</version>
    <scope>test</scope>
</dependency>

<!-- JSON Schema Validation -->
<dependency>
    <groupId>io.rest-assured</groupId>
    <artifactId>json-schema-validator</artifactId>
    <version>5.3.0</version>
    <scope>test</scope>
</dependency>

<!-- TestNG for Testing Framework -->
<dependency>
    <groupId>org.testng</groupId>
    <artifactId>testng</artifactId>
    <version>7.7.1</version>
    <scope>test</scope>
</dependency>
```

### 10.2 Writing Test Scripts 📝

#### 10.2.1 Basic Test Structure
```java
import io.restassured.RestAssured;
import org.testng.annotations.BeforeClass;
import org.testng.annotations.Test;
import static io.restassured.RestAssured.*;
import static org.hamcrest.Matchers.*;

public class ApiTests {
    
    @BeforeClass
    public void setup() {
        RestAssured.baseURI = "https://api.example.com";
        RestAssured.basePath = "/v1";
    }
    
    @Test
    public void testGetUsers() {
        given()
            .header("Accept", "application/json")
        .when()
            .get("/users")
        .then()
            .statusCode(200)
            .body("users.size()", greaterThan(0))
            .body("users[0].name", notNullValue());
    }
}
```

#### 10.2.2 Authentication Examples
```java
// Basic Auth
given()
    .auth().basic("username", "password")
    .get("/secure/resource");

// OAuth2
given()
    .auth().oauth2("your-token")
    .get("/protected/resource");

// Bearer Token
given()
    .header("Authorization", "Bearer " + token)
    .get("/api/resource");
```

### 10.3 Request/Response Handling 🔄

#### 10.3.1 POST Request Example
```java
@Test
public void testLogin() {
    // Request payload
    JSONObject requestParams = new JSONObject();
    requestParams.put("username", "testuser");
    requestParams.put("password", "password123");
    
    // Send request and validate
    given()
        .contentType("application/json")
        .body(requestParams.toString())
    .when()
        .post("/login")
    .then()
        .statusCode(200)
        .body("token", notNullValue())
        .body("expiresIn", greaterThan(0));
}
```

#### 10.3.2 JSON Response Validation
```java
@Test
public void testGetProducts() {
    // Complex JSON validation
    given()
        .queryParam("category", "electronics")
    .when()
        .get("/products")
    .then()
        .statusCode(200)
        .body("products.size()", greaterThan(0))
        .body("products.findAll { it.price > 100 }.size()", greaterThan(0))
        .body("products.collect { it.name }", hasItems("Laptop", "Phone"))
        .body("products.every { it.id != null }", is(true));
}
```

#### 10.3.3 XML Response Handling
```java
@Test
public void testXmlResponse() {
    given()
        .header("Accept", "application/xml")
    .when()
        .get("/orders")
    .then()
        .statusCode(200)
        .body(hasXPath("/orders/order[1]/id"))
        .body(hasXPath("/orders/order[status='COMPLETED']"))
        .body(matchesXsdInClasspath("order-schema.xsd"));
}
```

### 10.4 Advanced Features 🚀

#### 10.4.1 Response Extraction
```java
// Extract single value
String token = 
    given()
        .contentType("application/json")
        .body(loginPayload)
    .when()
        .post("/login")
    .then()
        .extract()
        .path("token");

// Extract complex data
List<String> productNames = 
    given()
        .get("/products")
    .then()
        .extract()
        .path("products.name");
```

#### 10.4.2 Schema Validation
```java
@Test
public void testJsonSchemaValidation() {
    given()
        .get("/user/1")
    .then()
        .assertThat()
        .body(matchesJsonSchemaInClasspath("user-schema.json"));
}
```

#### 10.4.3 Request/Response Logging
```java
given()
    .log().all()  // Log request details
.when()
    .get("/api/resource")
.then()
    .log().body() // Log response body
    .statusCode(200);
```

💡 **Best Practices**:
- Use proper test organization
- Implement test data management
- Handle environment configuration
- Log requests and responses
- Implement proper error handling
- Use schema validation
- Create reusable components

#### 10.4.4 Test Configuration Matrix 📊

| Component | Best Practice | Example |
|-----------|--------------|----------|
| **Base URL** 🌐 | Use configuration file | `config.properties` |
| **Auth** 🔐 | Centralize auth logic | Auth helper class |
| **Test Data** 📊 | External data sources | JSON/CSV files |
| **Assertions** ✅ | Custom matchers | Response validators |
| **Logging** 📝 | Conditional logging | Debug mode only |

</details>

## Chapter 11: Common API Testing Challenges and Solutions 🔍
<details>
<summary>Click to expand</summary>

### 11.1 Common Testing Issues 🐛

#### 11.1.1 Issue Categories and Solutions
| Issue | Symptoms | Solution |
|-------|----------|----------|
| **Invalid Endpoints** 🔗 | 404 Not Found | Verify API documentation |
| **Header Problems** 📋 | 400 Bad Request | Validate header format |
| **Auth Failures** 🔐 | 401/403 Errors | Check token validity |
| **Payload Issues** 📦 | Parse errors | Schema validation |
| **Timeouts** ⏱️ | Connection drops | Implement retries |

#### 11.1.2 Debugging Examples
```http
# Invalid Endpoint Debug
GET /api/v1/users  ❌ 404 Not Found
GET /api/v2/users  ✅ 200 OK

# Header Validation
POST /api/login
Content-Type: application/json  ✅
Authorization: Bearer invalid-token  ❌
```

### 11.2 Error Handling Strategies 🛠️

#### 11.2.1 Response Validation
```java
@Test
public void testInvalidUserCreation() {
    // Test payload with missing required field
    JSONObject payload = new JSONObject();
    payload.put("email", "test@example.com");
    // Missing required 'name' field
    
    given()
        .contentType("application/json")
        .body(payload.toString())
    .when()
        .post("/users")
    .then()
        .statusCode(400)
        .body("error", equalTo("Name is required"))
        .body("code", equalTo("VALIDATION_ERROR"))
        .log().ifValidationFails();
}
```

#### 11.2.2 Retry Mechanism
```java
public Response sendRequestWithRetry(String endpoint, int maxRetries) {
    int attempts = 0;
    Response response = null;
    
    while (attempts < maxRetries) {
        try {
            response = given()
                .get(endpoint)
                .then()
                .extract().response();
                
            if (response.getStatusCode() == 200) {
                return response;
            }
        } catch (Exception e) {
            log.error("Attempt " + (attempts + 1) + " failed: " + e.getMessage());
        }
        
        attempts++;
        // Exponential backoff
        sleep(Math.pow(2, attempts) * 1000);
    }
    
    throw new RuntimeException("Max retries exceeded");
}
```

#### 11.2.3 Error Logging
```java
public class TestLogger {
    public static void logFailedRequest(Response response) {
        System.err.println("=== Failed Request Details ===");
        System.err.println("URL: " + response.getUrl());
        System.err.println("Method: " + response.getMethod());
        System.err.println("Status: " + response.getStatusCode());
        System.err.println("Response Body: " + response.getBody().asPrettyString());
        System.err.println("Headers: " + response.getHeaders().asList());
    }
}
```

### 11.3 Test Suite Maintenance 📚

#### 11.3.1 Project Structure
```
api-tests/
├── src/
│   ├── test/
│   │   ├── java/
│   │   │   ├── auth/
│   │   │   ├── users/
│   │   │   └── products/
│   │   └── resources/
│   │       ├── test-data/
│   │       └── schemas/
└── config/
    ├── dev.properties
    ├── staging.properties
    └── prod.properties
```

#### 11.3.2 Reusable Components
```java
public class AuthHelper {
    private static String cachedToken;
    
    public static String getAuthToken() {
        if (isTokenValid(cachedToken)) {
            return cachedToken;
        }
        
        // Generate new token
        Response response = given()
            .contentType("application/json")
            .body(getLoginPayload())
            .post("/login");
            
        cachedToken = response.path("token");
        return cachedToken;
    }
}
```

#### 11.3.3 Configuration Management
```properties
# environment.properties
api.baseUrl=https://api.example.com
api.version=v2
api.timeout=5000
api.retry.max=3
api.auth.enabled=true
```

#### 11.3.4 Test Execution Strategy 📊
| Component | Strategy | Tool |
|-----------|----------|------|
| **Parallel Execution** 🔄 | TestNG XML Suite | `testng.xml` |
| **Data Provider** 📊 | External CSV/JSON | TestNG `@DataProvider` |
| **Environment Switch** 🌍 | Properties File | Maven Profiles |
| **Reporting** 📈 | HTML Reports | Extent Reports |

💡 **Maintenance Best Practices**:
- Use version control
- Implement CI/CD pipelines
- Regular dependency updates
- Code review process
- Documentation updates
- Test data management
- Performance monitoring

#### 11.3.5 Documentation Template 📝
```markdown
# Test Case: [ID] - [Name]

## Purpose
[Brief description of what this test verifies]

## Prerequisites
- Required environment
- Data setup
- Authentication

## Steps
1. [Step 1 description]
2. [Step 2 description]
   ...

## Expected Results
- [Expected outcome 1]
- [Expected outcome 2]

## Notes
- Known issues
- Dependencies
- Special considerations
```

</details>

## Chapter 12: API Security Testing 🔒
<details>
<summary>Click to expand</summary>

### 12.1 HTTP Status Codes Overview 🔢

#### 12.1.1 Status Code Categories
| Code Range | Category | Purpose | Examples |
|------------|----------|---------|-----------|
| **1xx** 📡 | Informational | Request received | `100 Continue` |
| **2xx** ✅ | Success | Request successful | `200 OK`, `201 Created` |
| **3xx** 🔄 | Redirection | Further action needed | `301 Moved`, `302 Found` |
| **4xx** ❌ | Client Error | Client-side issues | `400 Bad Request`, `404 Not Found` |
| **5xx** 💥 | Server Error | Server-side issues | `500 Internal Error`, `503 Unavailable` |

#### 12.1.2 Common Success Codes
```http
# 200 OK - Successful request
GET /api/users/123
Response: 200 OK
{
    "id": 123,
    "name": "John Doe"
}

# 201 Created - Resource created
POST /api/users
Response: 201 Created
Location: /api/users/124
```

### 12.2 Error Code Handling 🛠️

#### 12.2.1 Client Error Codes (4xx)
```java
@Test
public void testBadRequest() {
    // Test 400 Bad Request
    JSONObject invalidPayload = new JSONObject();
    invalidPayload.put("email", "invalid-email");  // Missing required fields
    
    given()
        .contentType("application/json")
        .body(invalidPayload.toString())
    .when()
        .post("/api/users")
    .then()
        .statusCode(400)
        .body("error", equalTo("Validation failed"))
        .body("details", hasItems("Email format invalid", "Name is required"));
}

@Test
public void testUnauthorized() {
    // Test 401 Unauthorized
    given()
        .header("Authorization", "Bearer invalid-token")
    .when()
        .get("/api/secure-resource")
    .then()
        .statusCode(401)
        .body("message", equalTo("Invalid or expired token"));
}
```

#### 12.2.2 Server Error Codes (5xx)
```java
@Test
public void testServerError() {
    // Test 500 Internal Server Error
    given()
        .header("Trigger-Error", "true")  // Custom header to simulate error
    .when()
        .get("/api/problematic-endpoint")
    .then()
        .statusCode(500)
        .body("error", equalTo("Internal Server Error"))
        .body("requestId", notNullValue());
}
```

### 12.3 Error Validation Scenarios 🎯

#### 12.3.1 Input Validation Tests
```java
public class InputValidationTests {
    @Test
    public void testInvalidDataTypes() {
        // Test string where number expected
        given()
            .queryParam("age", "not-a-number")
        .when()
            .get("/api/users")
        .then()
            .statusCode(400)
            .body("error", equalTo("Invalid parameter type"));
    }
    
    @Test
    public void testMissingRequiredFields() {
        JSONObject payload = new JSONObject();
        // Missing required 'name' field
        payload.put("email", "test@example.com");
        
        given()
            .body(payload.toString())
        .when()
            .post("/api/users")
        .then()
            .statusCode(400)
            .body("error", equalTo("Missing required field: name"));
    }
}
```

#### 12.3.2 Authentication Tests
```java
@Test
public void testAuthScenarios() {
    // Test expired token
    given()
        .header("Authorization", "Bearer " + getExpiredToken())
    .when()
        .get("/api/secure")
    .then()
        .statusCode(401)
        .body("error", equalTo("Token expired"));
        
    // Test invalid permissions
    given()
        .header("Authorization", "Bearer " + getUserToken())
    .when()
        .post("/api/admin/action")
    .then()
        .statusCode(403)
        .body("error", equalTo("Insufficient permissions"));
}
```

#### 12.3.3 Rate Limiting Tests
```java
@Test
public void testRateLimiting() {
    // Send multiple requests rapidly
    IntStream.range(0, 100).forEach(i -> {
        Response response = given()
            .get("/api/resource");
            
        if (i < 50) {
            response.then().statusCode(200);
        } else {
            response.then()
                .statusCode(429)
                .header("Retry-After", notNullValue());
        }
    });
}
```

💡 **Error Testing Best Practices**:
- Test both positive and negative scenarios
- Validate error message content
- Check error response structure
- Verify appropriate status codes
- Test rate limiting behavior
- Validate security responses
- Document error scenarios

#### 12.3.4 Error Test Matrix 📊
| Scenario | Expected Code | Validation Points |
|----------|---------------|-------------------|
| **Invalid Input** 📝 | 400 | Field validation messages |
| **Auth Failure** 🔐 | 401/403 | Error description, WWW-Authenticate |
| **Not Found** 🔍 | 404 | Resource identifier in message |
| **Rate Limit** ⏱️ | 429 | Retry-After header, limit info |
| **Server Error** 💥 | 500 | Generic message, no sensitive data |

#### 12.3.5 Error Response Template
```json
{
    "status": 400,
    "error": "Validation Error",
    "message": "Request validation failed",
    "details": [
        {
            "field": "email",
            "error": "Invalid email format"
        }
    ],
    "timestamp": "2025-01-20T17:08:30Z",
    "requestId": "req-123-abc",
    "documentation": "https://api.example.com/docs/errors"
}
```

</details>

## Chapter 13: Advanced API Testing Techniques 🔍
<details>
<summary>Click to expand</summary>

### 13.1 Data Parameterization 📊

#### 13.1.1 Test Data Management
```json
// test-data.json
{
    "valid_users": [
        {
            "username": "user1",
            "password": "pass123",
            "expected_status": 200
        },
        {
            "username": "admin",
            "password": "admin123",
            "expected_status": 200
        }
    ],
    "invalid_users": [
        {
            "username": "invalid",
            "password": "",
            "expected_status": 400
        }
    ]
}
```

#### 13.1.2 Parameterized Tests
```java
@Test
@Parameters({"username", "password", "expected_status"})
public void testLogin(String username, String password, int expectedStatus) {
    given()
        .contentType("application/json")
        .body(new LoginRequest(username, password))
    .when()
        .post("/login")
    .then()
        .statusCode(expectedStatus);
}

// Data Provider
@DataProvider(name = "loginData")
public Object[][] getLoginData() {
    return new Object[][] {
        {"user1", "pass123", 200},
        {"admin", "admin123", 200},
        {"invalid", "", 400}
    };
}
```

### 13.2 API Mocking and Stubbing 🎭

#### 13.2.1 Mock Server Setup
```javascript
// Postman Mock Server Example
pm.test("Setup Mock Response", () => {
    const mockResponse = {
        status: 200,
        body: {
            "id": "123",
            "name": "Test User",
            "email": "test@example.com"
        }
    };
    
    pm.sendRequest({
        url: pm.environment.get("mockServerUrl") + "/users/123",
        method: 'GET',
        headers: {
            'Content-Type': 'application/json'
        }
    }, (err, res) => {
        pm.expect(res.json()).to.eql(mockResponse.body);
    });
});
```

#### 13.2.2 WireMock Example
```java
@Test
public void testWithMock() {
    // Setup mock
    stubFor(get(urlEqualTo("/api/users/123"))
        .willReturn(aResponse()
            .withStatus(200)
            .withHeader("Content-Type", "application/json")
            .withBody("{\"id\":\"123\",\"name\":\"Test User\"}")
        ));
    
    // Test using mock
    given()
        .when()
        .get("/api/users/123")
        .then()
        .statusCode(200)
        .body("name", equalTo("Test User"));
}
```

### 13.3 CI/CD Integration 🔄

#### 13.3.1 Jenkins Pipeline
```groovy
// Jenkinsfile
pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/your/api-tests.git'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                sh 'npm install'  // For Newman/Postman
                sh 'mvn clean install -DskipTests'  // For Java/REST Assured
            }
        }
        
        stage('Run API Tests') {
            parallel {
                stage('Smoke Tests') {
                    steps {
                        sh 'newman run collection.json -e env.json --folder "Smoke"'
                    }
                }
                stage('Regression Tests') {
                    steps {
                        sh 'mvn test -Dtest=RegressionSuite'
                    }
                }
            }
        }
        
        stage('Generate Reports') {
            steps {
                publishHTML([
                    allowMissing: false,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: 'target/site/allure-report',
                    reportFiles: 'index.html',
                    reportName: 'API Test Report'
                ])
            }
        }
    }
    
    post {
        always {
            cleanWs()
        }
        failure {
            slackSend channel: '#api-testing',
                      message: "Pipeline Failed: ${env.JOB_NAME} [${env.BUILD_NUMBER}]"
        }
    }
}
```

#### 13.3.2 Environment Configuration
```yaml
# docker-compose.yml
version: '3'
services:
  api-tests:
    build: .
    environment:
      - API_BASE_URL=http://api.example.com
      - API_TOKEN=${API_TOKEN}
    volumes:
      - ./reports:/app/reports
    command: ["npm", "test"]
```

#### 13.3.3 Test Execution Strategy 📊
| Stage | Tests | Trigger | Environment |
|-------|-------|---------|-------------|
| **Build** 🏗️ | Smoke | Every commit | Development |
| **Deploy** 🚀 | Integration | PR merge | Staging |
| **Release** 📦 | Full suite | Release | Production |

💡 **Advanced Testing Tips**:
- Use data-driven approach
- Implement mock services
- Automate test data setup
- Configure parallel execution
- Set up proper reporting
- Monitor test metrics
- Implement retry logic
- Use environment variables

#### 13.3.4 CI/CD Metrics Dashboard 📈
```json
{
    "test_metrics": {
        "total_tests": 250,
        "passed": 245,
        "failed": 5,
        "skipped": 0,
        "execution_time": "45m",
        "coverage": {
            "endpoints": "95%",
            "scenarios": "88%"
        },
        "trends": {
            "last_7_days": {
                "success_rate": "98%",
                "avg_duration": "42m"
            }
        }
    }
}
```

</details>
