# API Automation REST Project

This project demonstrates automated API testing using Java, TestNG, and RestAssured. It will validate the structure and content of the responses.

## Features
- Automated tests for addresses, books, companies, and products endpoints
- Validation of response status, content type, and data structure
- Use of TestNG for test organization and execution
- Readable and maintainable test code

## Project Structure
```
pom.xml
src/
  main/
    java/
      org/
        example/
          Main.java
  test/
    java/
      dummyApi.java
      fakerApi.java
```

## Getting Started

### Prerequisites
- Java 8 or higher
- Maven

### Setup
1. Clone the repository:
   ```sh
   git clone https://github.com/thomsq/api-automation-rest.git
   ```
2. Install dependencies:
   ```sh
   mvn clean install
   ```

### Running Tests
Execute all tests using Maven:
```sh
mvn test
```

## Example Test
A sample test for the addresses' endpoint:
```java
@Test
public void testSingleAddress() {
    given()
        .basePath("addresses")
        .param("_quantity", "1")
        .param("_locale", "en_US")
        .contentType(ContentType.JSON)
    .when()
        .get()
    .then()
        .statusCode(200)
        .body("status", equalTo("OK"))
        .body("locale", equalTo("en_US"))
        .body("data", hasSize(1))
        .body("data[0]", hasKey("street"));
}
```

## Dependencies
- [RestAssured](https://rest-assured.io/)
- [TestNG](https://testng.org/)

## License
This project is licensed under the MIT License - see the LICENSE file for details.