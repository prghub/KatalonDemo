# KatalonDemo - Web Automation Testing

This project demonstrates automated testing of a web application using **Katalon Studio**. It includes testing the login functionality of a web page with sample test cases, written in Groovy, and using the Katalon framework for execution and reporting.

## Project Overview

This project tests the login functionality on **https://the-internet.herokuapp.com/login**. The test performs the following steps:

- Navigates to the login page.
- Enters valid credentials for the user (`tomsmith`).
- Verifies that the login is successful.
- Asserts the success message.

## Technologies Used

- **Katalon Studio**: A test automation platform for web, API, mobile, and desktop applications.
- **Selenium WebDriver**: Utilized by Katalon Studio for browser automation.
- **JUnit/TestNG**: Frameworks used for test execution in Katalon.
- **Git**: Version control for the project.

## Project Structure

The project consists of the following key components:

- **Test Cases**: Contains the individual test scripts that test specific features or functionality.
- **Test Data**: Includes test data used by the test cases, if any.
- **Test Objects**: Stores locators for interacting with elements on the web page (such as buttons, input fields).
- **Keywords**: Contains custom keywords for reusable actions across test cases.
- **Reports**: Contains execution logs, screenshots, and detailed test results.
- **Global Variables**: Stores reusable variables across test cases.

## File Overview

### Test Case Implementation (`LoginTest`)

This test case automates the process of logging into the application.

#### Code Sample:

```groovy
// Open the browser
WebUI.openBrowser('')

// Navigate to the login page
WebUI.navigateToUrl('https://the-internet.herokuapp.com/login')

// Set the username and password
WebUI.setText(findTestObject('Object Repository/Page_The Internet/input_Username_username'), 'tomsmith')
WebUI.setEncryptedText(findTestObject('Object Repository/Page_The Internet/input_Password_password'), 'T6bVo8B8lVC7U1u1L64B7tu+ltX9y9HI')

// Click the login button
WebUI.click(findTestObject('Object Repository/Page_The Internet/i_Login'))

// Verify the success message
WebUI.verifyElementPresent(findTestObject('Object Repository/Page_The Internet/div_You logged into a secure area'), 0)

// Get the text from the success message
String actualText = WebUI.getText(findTestObject('Object Repository/Page_The Internet/div_You logged into a secure area'))

// Clean up the message text
actualText = actualText.replace('×', '').trim()

// Assert that the actual text matches the expected text
assert actualText == 'You logged into a secure area!'

// Close the browser
WebUI.closeBrowser()
