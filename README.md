# Customer Management System
<p align="center">
 <img src="https://i.ibb.co/rpDYbhw/Customer-Management-System.png" alt="Customer-Management-System" border="0" width="100%">
</p>

## Table of Contents
- [Description](#description)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage) 
- [Contributing](#contributing)
- [Documentation](#documentation)
- [License](#license)  
- [Demo](#demo)
- [Contact Information](#contact-information)

![GitHub commit activity](https://img.shields.io/github/commit-activity/y/terrychitter/customer-management-system) ![GitHub repo size](https://img.shields.io/github/repo-size/terrychitter/customer-management-system)


## Description
This project is a customer management system for a fictional business that sanitizes dustbins.

The program is responsible for managing customers details such as personal, contact and sanitizing details.  Comments may be added for customers for administration use. Additionally, payment-related features can be used such as viewing the customers' current balance, payments made by the customer, and generated invoices for the customer. Customer accounts may also be deactivated or activated.

The payment section allows for administration to record payments made by customers. The payments page handles duplicate payments, balance updating, payment reversal, and other validation.

The invoice section allows for administration to generate invoices for customers and holds many searching and filtering features to quickly find the customer or group of customers the user is looking for. Invoices may be generated in batch and also allows the user to tweak certain dates on the invoice such as issue, fee, and brought-forward dates. Lastly, invoices for customers may be downloaded in batch for selected months.

The settings page allows administration staff to change or set certain features such as adding or removing bank details to display on customer invoices.

The project makes use of programming languages such as HTML5, CSS3, JavaScript, NodeJS and PHP. Additionally Bootstrap is used for styling.


## Installation
See below instructions to quickly set up and install the project. The project makes use of all frameworks below.
### Composer
 1. Ensure you have [Composer](https://getcomposer.org/) installed.
 2. Navigate to the project directory: `cd cms`.
 3. Install PHP dependencies: `composer install`.
### Node.js
 4. Ensure you have [Node.js](https://nodejs.org/) installed.
 5. Navigate to the project directory: `cd cms`.
 6. Install Node.js dependencies: `npm install`.
### Bootstrap
 7. Bootstrap can be added to your project in several ways: 
-**Using npm:**  ```bash npm install bootstrap```
-**Using yarn:** ```bash yarn add bootstrap```

## Configuration
### Config Folder
You will find a folder in the repository labelled `config`. It is important that you place this folder in the previous directory of the repository. The project has been set up this way as it is good security practice.
#### db_conn.php
The `db_conn.php` file holds the database connection. See the [installation](##Installation) regarding database set up. Ensure that the `db_conn.php` file holds the correct details to successfully connect to your database.

<div align="center">
<img src="https://i.ibb.co/DMqGj49/Snap.png" alt="Snap" border="0">
</div>

#### keys.php
The `keys.php` file holds additional keys used in the site. The `$secretLoginToken` is used as the login token when accessing the token and you may set this to whatever you like.

The `$recaptchaKey` should be the secret key for your Google reCaptcha. See [here](https://www.youtube.com/watch?v=i3Uq3-ulW-k) how to setup your Google reCaptcha for the site. Please ensure to use reCaptcha v2 – "I am not a Robot" Checkbox. **Note**: Unfortunately as of the current version there is no work around to the Google reCaptcha and I apologise for the inconvenience this may cause in testing the project.

<div align="center">
<img src="https://i.ibb.co/ZXdbyGr/Snap-3.png" alt="Snap-3" border="0">
</div>

### Other Configurations
Lastly, in addition to providing your secret key for Google reCaptcha, ensure to provide your public key [here](https://github.com/terrychitter/customer-management-system/blob/9fb5185776cc95a50a35b9b13c9cbbd959bc7bae/login/login.php#L148C1-L148C108) in the `data-sitekey` attribute.

## Usage
This section goes through notable features of the site.

### Searching customers
The search feature is used on multiple pages since customer databases can easily grow to large numbers making it cumbersome to find the customer you are looking for. For this reason, the default search feature allows the user to provide a search term as well as choose a search field, for example, account number, surname, and street name. This search feature is further built apon on the invoice page which you may view [here](###Filters-for-customers-on-Invoice-Page)

### Editing Customers
Customer details are subject to change, thus, the site provides a quick and easy way to edit customer data. Validation such as length, email validation, and format and always considered.

### Activating/Deactivating Customers
<div align="center">
 <img src="https://pouch.jumpshare.com/preview/WGLAreGQPD7EJPEbysdAC6fC1H-ezKS1zwwYRjV75nMP1OAH-p_AZDQM6Kp7nGImWjOdKHc1R7DZt7DngmNUUyPq163HHNhJYDMOjgplZc8">
</div>

### Adding Comments/Contacts
In many cases administrators would add or edit comments as well as multiple contacts for individual customers.

<div align="center">
<img src="https://pouch.jumpshare.com/preview/IvMAFnDpetFiVxymAk2_YuQ02fEW-FPSV2BokUB37r87qnNIk0hP32dI6m2tFkE0WjOdKHc1R7DZt7DngmNUU0qT8Mpgoft53irnsAYrb9E">
 <img src="https://pouch.jumpshare.com/preview/xkKebk1OzgkiW46yRMuBgfIUNI5sE5f34ufmKRSJcYt-ovS11ffxy-94MMnrpINNWjOdKHc1R7DZt7DngmNUUyvie19N1LjeS7Zr_xj-WdU" >
</div>

### Adding Payments
Payments can be recorded on the payments page for each customer. Addition to recording payments, the customer's balance will also be updated and recorded in the balances table with all the neccessary details of the transaction.

### Payment Reversal
It is possible that human error can occur while recording payments. For this reason, payment reversal has been implemented. When a payment is reversed, the customer's payment record will be removed along with the balance recorded inserted into the balances table when the payment was recorded.

### Payment Duplication Checking
In addition to erroneous input when recording payments, a payment may be mistakingley inserted again. Each payment is checked before inserting it into the database to ensure there is not an existing payment with the same date, amount, and type.

### Invoice Generation
Invoice generation using the CMS allows you to select which customers you would like to generate invoices for as well as set certain dates for the invoices. From the search section the administrator can select which customers they would like to generate invoices for and they will be displayed in the "Selected Customers" sections. One all invoice details are filled in, the administrator may generate the invoices all at once as seen below. A progress bar along with updates will be displayed at the bottom. All invoices are stored as `.xlsx` files.

**Note**: The site is designed so that invoices are not accessable from the `htdocs` folder, instead, along with the `config` folder, all invoices are stored in the parent directory in the `invoices` folder. While invoices are easily accessible from the site, authorised users may access the invoices from the mentioned directory.

### Filters for customers on Invoice page
The search feature is expanded on in the invoices page for users to easily find groups of customers. It is important to mention that only active customers are displayed by default on the invoice page, however, this can be overriden using the filters. Administrators may choose to do the following:
- Display all active customers (defaut).
- Display all active customers with pending invoices (this refers to all customers that do not have an invoice for the current month yet).
- Display all inactive customers.
- Display all inactive customers with pending invoices.
From the group of customers returned from the above filters, administrators may still add a search term and search field.

### Checking Duplicate Invoices
With the risk of human error, it is possible that duplicate invoices may be generated. For this reason, duplication checking is run before generating the invoices. The administrator has the option to cancel the action, overwrite the current invoices, or remove those selected customers from the list and generate invoices for the remaining.

### Invoice Downloading
It is possible to download invoices from a customer's profile, however, this will quickly become tedious as the number of customers grow. On the invoices page administrators are able to download invoices in batch where it will be downloaded to their local device as a `.zip` file. Administrators can download invoices in batch from a certain month and year as seen below.

<div align="center">
 <img src="https://pouch.jumpshare.com/preview/f10iFEt0PWDTDNE-hOsiM_eU1-wz_e_CKoyKI7R5vPHrIDANtGvSeIq5E-Bgx1SU3zNxlmFfILdrqQcX1H2a-npVbJk8ZkGkgsIgnm3H944">
</div>

### Setting Default Bank Accounts
Administrators may set default bank accounts to avoid having to manually edit each customer's details. When changing the default bank account the administrator has additional options:
- All future customers will be linked with the selected bank account.
- All customers linked with the current default bank account will be linked to the new default bank account.
- All customers will be linked to the new default bank account.

## Contributing
Contributions from the community are most welcomed! Whether it's reporting a bug, submitting a feature request, or improving the documentation, your help is appreciated. To contribute to this project, please follow these guidelines:

### Issues and Bugs
If you encounter any issues or find a bug, please check the existing issues to see if it has already been reported. If not, please open a new issue, including the following details:

- A clear and descriptive title.
- A detailed description of the issue, including steps to reproduce.
- Screenshots or code snippets, if applicable.
- Information about your environment (operating system, browser, etc.).

### Feature Requests
You are welcome to suggest new features or improvements. Before submitting a feature request, please:
- Check the existing feature requests to avoid duplicates.
- Provide a clear and detailed description of the proposed feature.
- Discuss the feature with the community to gather feedback.

### Pull Requests
Pull requests for bug fixes, new features, and improvements are welcomed as well. To submit a pull request, follow these steps:

- Fork the repository and create a new branch for your contribution.
- Write clear and comprehensive commit messages.
- Test your changes thoroughly.
- Submit a pull request, referencing the relevant issue (if applicable).
- Be prepared to address feedback and iterate on your changes.

By contributing to this project, you agree that your contributions will be licensed under the project's license.
Thank you for contributing to the project! 🚀

## Documentation

## License
This project makes use of the [MIT License](LICENSE.md)

## Contact Information
For any questions and support, contact me at t.sikenaris@gmail.com
