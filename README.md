## API DOCUMENTATION (ENDPOINTS)

### /mongotest

DESCRIPTION: Test Mongo connection (insertOne)

PARAMETERS: none

RETURNS:

{
  "acknowledged": Boolean,
  "insertedId": String
}

NOTES:

Confirm in https://cloud.mongodb.com/ that the insertion was made

### /alreadyloggedin

DESCRIPTION: Check if user is logged in Firebase (onAuthStateChanged)

PARAMETERS: none

RETURNS:

{
  "email": String,
  "admin": Boolean,
  "balance": Integer
}

### /signup

DESCRIPTION: Create user in Firebase (email & password)

PARAMETERS: name, email, password, admin ('true' or 'false')

RETURNS:

true || `${errorCode}: ${errorMessage}`

### /login

DESCRIPTION: Login request in Firebase (signInWithEmailAndPassword)

PARAMETERS: email, password

RETURNS:

{
  "email": String,
  "admin": Boolean,
  "balance": Integer
}

### /logout

DESCRIPTION: Logout request from Firebase (signOut)

PARAMETERS: email

RETURNS:

`user logged out` || `Error in logging out`

### /transaction

DESCRIPTION: Make a transaction. This means update the user's balance in the DB

PARAMETERS: email, amount

RETURNS: Information after transaction

{
  "email": String,
  "admin": Boolean,
  "balance": Integer
}

### /alldata

DESCRIPTION: Returns all the Database's information

PARAMETERS: email

RETURNS: 

{
  "user": {
    "name": String,
    "email": String,
    "admin": Boolean,
    "balance": Integer
  },
  "allUsers": [
    {
      "_id": String,
      "name": String,
      "email": String,
      "password": String,
      "admin": Boolean,
      "balance": Integer,
      "transactions": [
        {
          "deposit": Boolean,
          "amount": Integer,
          "date": String
        }...
      ]
    }...
  ],
  "activity": [
    {
      "_id": String,
      "email": String,
      "action": String,
      "date": String
    }...
  ]
}