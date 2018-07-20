# Firebase-Query-to-Excel
A class to process Firebase Firestore database queries and create an excel file that could be shared

## Usage
1. Add above class to your project
2. Import necessary libraries
3. To use the class in another class or activity create an instance of it

    -fieldNames String array contains the name of the fields you want to retrieve from the query. Order of names in the array is important.
```java
String[] fieldNames = {"name", "email", "id", "more"};
FirebaseDBCollectionToExcel createExcel = new FirebaseDBCollectionToExcel( fieldNames);
```
4. Within the part you call the query include the buildFileFromQuery(QueryDocumentSnapshot document ) method like so:
```java
db.collection("users").get().addOnCompleteListener(new OnCompleteListener<QuerySnapshot>() {

            public void onComplete(@NonNull Task<QuerySnapshot> task) {

                if (task.isSuccessful()) {
                
                     for ( QueryDocumentSnapshot document : task.getResult()) { //Include here
                          createExcel.buildFileFromQuery(document);
                     }
   }
  }
}
```
5. After creating the file, you can save it to the local storage using saveFileToStorage(String fileName, String dirName) method:
```java
String fileName = "File Name";
String dirName = "Directory Name";
createExcel.saveFileToStorage(fileName, dirName);
```
6. Lastly given the file is in storage, you can share it through mailing applications using the method shareFileToEmail( String subject)
  
   This method will open an intent
```java
String subject = "Email Subject";
createExcel.shareToEmail( subject);
```

## Needed improvments
- Create a ready to use importable library

## Authors
[Zeyad Khaled](https://www.linkedin.com/in/zeyadkhaled/ "Zeyad Khaled")


