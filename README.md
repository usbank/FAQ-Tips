# Frequently Asked Questions and Tips
Helpful Information for participating in hackathons
More to come

## General questions

### Q. Where do I find the U.S. Bank Developer Portal?
A. The developer portal for the *Yackety Hack, Get Caa$h Fast Hackathon* is located at: [hacktotrack-innovation.usbank.com](https://hacktotrack-innovation.usbank.com).

### Q. Do I need to register on the U.S. Bank Developer portal?
A. Yes, you will need to register for an account on the Developer Portal in order to view the API documentation and obtain an API key. Complete signup instructions are provided in this folder. Once you complete the signup process, a confirmation email will be sent to this address to activate your account.

### Q. Where can I get help during the hackathon event?
A. During the event, there will be on-site support from both U.S. Bank and Microsoft to help answer any technical or conceptual questions.

Furthermore, there will be U.S. Bank team members participating with each team.

### Q. How can I use one of the APIs?
A. In order to use any of the U.S. Bank APIs, you will need to first request an API key from the developer portal.

You will use this key, as well as any query data, to call these APIs.

## Test data related questions

### Q. The *accounts* API contains both the "/user/accounts" method and the "account/details" method. What is the difference?
A. The "/user/accounts" method provides a list of accounts for a specific user. It also includes the balances of each of these accounts. On the other hand, the "/account/details" API provides information about a single account. For certain types of accounts, this information will includes the owner's contact details.

### Q. Where do we find the available user accounts?
A. Within the *accounts* API, there is a GET method called "/users". This method will return a list of available user accounts that you can then use within the other APIs.

### Q. Can we update the balance of particular account?
A. Unfortunately, you cannot update any of the records within the U.S. Bank test data environment. If you need to show changes to a balance, you will need to perform those actions within your application itself.


### Q. Can I transfer money between test accounts?
A. All of the the test data is static and therefore the balances will not actually update to reflect any changes. If your application needs to show money movement, you will need to keep track of the available balances within your code.

### Q. I am trying to build an application that needs credit card transactions, which user has a lot of credit card transactions?
A. These following account has several card transactions at a variety of merchants:

{ "LegalParticipantIdentifier": "913996201744144603",
"OperatingCompanyIdentifier": "52",
"ProductCode": "CCD",
"PrimaryIdentifier": "00000004037670240271147" }


### Q. Will I have my own test accounts to use for the hackathon event?
A. All of the test accounts are available for all participants. Because the data is static, no one is able to make any updates to the test values (such as current balance).

## General questions about the data fields

### Q. What is the field name for account owner?
A.	The account owner is listed as the "LegalParticipantIdentifier".


### Q. What is the field name for the account number?
A. The account number is listed as the "PrimaryIdentifier" or as the "AccountPrimaryIdentifier".

### Q. What level of details is available for a credit card transaction?
A. The transaction data only provides basic information such as the merchant name, transaction amount, date and the transaction category. It does not provide detailed information. For example, a transaction for a hotel room would not include itemized details such as room rate, room tax and other fees like in-room dining. These details, known as Level 2/3 item details, are typically only available from the merchant itself.

### Q. Can I find the categories for a given credit card transaction? If so, where?
A. The general category of a credit card transaction is found in the data field named 'StandardIndustryCode'. In the U.S. Bank data, this value is given as a five-digit number where the last four digits correspond to the actual Merchant Category Code. The leading zero is only used internally.

### Q. What are MCC codes?
A. The Merchant Category Code (or MCC) is used to classify the business by the type of goods or services it provides. It is a four-digit standard number listed in ISO 18245 specifically for retail services.

### Q. How do I look up an MCC code?
A. We have the *merchant codes* API to look up merchant codes. You can either look up a specific MCC ("/mcc/{codes}") or query for all the MCC values associated with a general industry, such as "Food" or "Legal" ("/mcc/query"). Examples are given in the Postman collection about using the two methods.

### Q. What data do I need to retrieve the transactions for a given account?
A. In order to retrieve transaction history, you will need to a valid account number, its product code (type of account) and the corresponding company code.  

### Q. Where do I find account numbers, product codes and company codes?
A. The *accounts* API will provide all of these values for each account owned by a specific user. You can retrieve this list by using the API's POST "user/accounts" method.
