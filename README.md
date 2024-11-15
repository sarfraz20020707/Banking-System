# Banking-System-OOP-Python :bank::desktop_computer:

This project simulates a basic banking system with functionalities similar to an ATM machine. It allows users to register, log in, and perform common banking operations such as depositing, withdrawing money, and checking their balance.

---

## Table of Contents

1. [Code Description](#codedescription)
   - [Banking System Features](#bankingsystemfeatures)
   - [Bank-related Operations (bank.py)](#bankrelatedoperations)
   - [User-related Operations (user.py)](#userrelatedoperations)
   - [Bank Database (account_database.csv)](#bankdatabase)
   - [Windy Banks (windy_banks.py)](#windybanks)
2. [Output](#output)
   - [Registration](#registration)
   - [Login and Running Transactions](#loginandrunningtransactions)
3. [Thoughts After the Project](#thoughts)

---

## Code Description <a name="codedescription"></a>

### 1. Banking System Features <a name="bankingsystemfeatures"></a>

This version of the Banking System includes:

- **User Registration:** Allows users to create a new account.
- **Login System:** Users can log in with a valid username and password.
- **Banking Operations:**
   - **Deposit:** Users can deposit money into their account.
   - **Withdrawal:** Users can withdraw money (subject to a max withdrawal limit).
   - **View Balance:** Users can view their current account balance.

---

### 2. Bank-related Operations (bank.py) <a name="bankrelatedoperations"></a>

This file handles bank-related operations like user registration and managing the account database.

- **`UserDatabase` Class:** Manages the user accounts stored in a CSV file.
- **Important Methods:**
  - **`__init__(self)`:** Initializes the database from the `account_database.csv` file.
  - **`get_users(self)`:** Converts the CSV into a list of `User` objects.
  - **`registeration()`:** Registers a new user and appends them to the database.
  - **`users`:** A list variable storing all users as `User` objects for easy manipulation.

---

### 3. User-related Operations (user.py) <a name="userrelatedoperations"></a>

This file defines the `User` class, which contains methods for managing individual user accounts.

- **`User` Class:** Represents an individual bank account, containing attributes like the user's name, password, and balance.
- **Important Methods:**
  - **`__init__(self)`:** Initializes a `User` object with name, password, and balance.
  - **`view_balance(self)`:** Displays the current balance.
  - **`withdraw(self)`:** Handles the withdrawal of funds from the user's account.
  - **`deposit(self)`:** Handles deposits into the user's account.
  - **`as_dict(self)`:** Converts the `User` object into a dictionary to update the CSV file.

---

### 4. Bank Database (account_database.csv) <a name="bankdatabase"></a>

The account data is stored in a CSV file, which includes users' names, passwords, and account balances. Here’s an example of how the file looks:

```
name,password,amount
john,john66,10000
mary,m@ry23,22500
tim,timmy8989,50000
jacob,windyhammer,30000
susan,suziesusan,39000
thebest,thebest,10000000000000000
james,jamesbond,1
windjammer,breezerestricter,0
```

When a new user registers, their information is added to this CSV file.

---

### 5. Windy Banks (windy_banks.py) <a name="windybanks"></a>

This is the main program file where the user interacts with the system. It imports the necessary functionalities from `bank.py` and `user.py`.

- **Important Libraries Used:**
  - **`pandas`**: For loading and manipulating the CSV file.
  - **`sys`**: For system-level operations like exiting the program.
  - **`time`**: For adding delays to make the user experience smoother.
  
- **Main Variables:**
  - **`user_database`**: A pandas DataFrame containing all user account data.
  - **`database_user_list`**: A list of `User` objects, allowing easy manipulation of data.

- **Core Functions:**
  - **`main()`**: The main function running the banking system.
  - **`name_login()`**: Handles user login by checking the username.
  - **`password_login()`**: Validates the password entered by the user.

- **Database Update Process:**
  - After each transaction (deposit or withdrawal), the system updates the user data by converting the list of `User` objects to a dictionary and then saving it back to the CSV file using pandas.

---

## Output <a name="output"></a>

### Registration <a name="registration"></a>

Here’s what happens when a user registers a new account:

```
Welcome to Windy Banks!

Do you have an account or are looking to register an account? (Please enter the corresponding number)
1. Log in
2. Registration
2
We will need some of your personal information to set up an account for you.
Please enter the name you want for the account: thomas
Please set your password (must be at least 7 characters): 99     
Please set your password with at least 7 characters!
Please set your password (must be at least 7 characters): thomaswayne99
Your account has been successfully created!

Account name: thomas
Password: thomaswayne99
Amount: $0

Please rerun the program and log in to start making transactions!
```

Once registration is complete, the user's account is added to the `account_database.csv`:

```
name,password,amount
john,john66,10000
mary,m@ry23,22500
tim,timmy8989,50000
jacob,windyhammer,30000
susan,suziesusan,39000
thebest,thebest,10000000000000000
james,jamesbond,1
windjammer,breezerestricter,0
thomas,thomaswayne99,0
```

---

### Login and Running Transactions <a name="loginandrunningtransactions"></a>

After logging in, users can perform various transactions:

```
Welcome to Windy Banks!

Do you have an account or are looking to register an account? (Please enter the corresponding number)
1. Log in
2. Registration
1
This is the login page, please enter your name and password to login.
Name: thoma 
This name does not have a bank account here! Please try again.
(If you wish to exit, please enter "exit")
Name: thomas 

Hello, thomas

Please enter the password: thomaswayne
Incorrect password!
Please enter the password: thomaswayne99
You have successfully logged in!

Welcome, thomas, what would you like to do today? (Please select the corresponding number)
1. Deposit
2. Withdraw
3. View Balance
4. Exit
1
How much would you like to deposit: 2000
Transaction successful. Thank you for using Windy Banks, you have deposited $2000, and now have $2000 in your account.

Would you like to make another transaction? (Please enter the corresponding number)
1. Yes.
2. No, please log me out.
1
Welcome, thomas, what would you like to do today? (Please select the corresponding number)
1. Deposit
2. Withdraw
3. View Balance
4. Exit
2
How much would you like to withdraw (max $1000): 10000
Insufficient funds!
How much would you like to withdraw (max $1000): 1000
Transaction successful. Thank you for using Windy Banks, you have withdrawn $1000, and have $1000 left in your account.

Would you like to make another transaction? (Please enter the corresponding number)
1. Yes.
2. No, please log me out.
2
Thank you for using Windy Banks services!
```

The database is updated with the new balance:

```
name,password,amount
john,john66,10000
mary,m@ry23,22500
tim,timmy8989,50000
jacob,windyhammer,30000
susan,suziesusan,39000
thebest,thebest,10000000000000000
james,jamesbond,1
windjammer,breezerestricter,0
thomas,thomaswayne99,1000
```

---




---

## Requirements

- Python 3.x
- pandas (for handling CSV data)
  
To install pandas, use:
```bash
pip install pandas
```

---
