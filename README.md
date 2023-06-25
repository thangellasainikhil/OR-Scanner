# QR Payments System ( QR-SCANNER )

This section of the project "QR Payments System" is a QR Scanner which scans a QR Code and performs the transaction to complete user's food orders.
This project is a part of our Semester-End Course Based Project.

## What's happening at the back?

1. Validate the QR Code
    - Checking for QR Code in the database QR Records to check if QR is already used with in validation time.
    - Check QR Validity by validation time of 15 mins.
2. If QR is validated User validation starts.
    - Check for username in database.
    - If it matches decrypt the pin and validate it that with pin in database.
3. Generate Bill
    - Check for validity of product prices in database.
    - Generate Bill respective to quantity of food selected.
    
4. Verify User account balance
    - Check for sufficient balance in user's account.
    
5. If all the above conditions are validated initiate transaction.
6. Deduct balance from user's account.
7. If the customer is the first customer of the day in stalls_credits table no row will be present on that particular stall name.
    1. So directly insert bill as credit amount.
9. Else the customer is not the first customer of the day so update credit amount for that stall name and that particular date.
10. So here stall name and date together are primary key (composite primary key).
11. Update the stall orders respectively.
12. Update QR Code details in QR Records for further QR validation purpose.
13. Commit the database changes only when every database transaction is done successfully. Otherwise, rollback all transactions and respond accordingly.


## Tech Stack Used
   ### Relational Database
      1. MySQL Database Management System.
      
   ### QR Scanner
      1. pyzbar (python module)
      2. opencv-python
      3. mysql-connector-python

### Use .env file to store your db credentials
### folder structure for .env file

    .                       # root project directory
    |-..                    # other directories
    |--src                  # src directory
    | |--Database_Scripts   # inside src, all database handling script files
    | |--Python_Scripts     # additional python script files
    | .env                  # .env file inside src at src directory level
    |_..                    # other directories
  
### contents inside .env

    MY_USERNAME = your_root_username_here
    MY_PASSWORD = your_db_password_here
    MYDB = your_local_database_name_here

***(dont enclose credentials in quotes, and add .env file to .gitignore)***
