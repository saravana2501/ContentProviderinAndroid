
# Ex.No:3 Create Your Own Content Providers to get Contacts details.


## AIM:

To create your own content providers to get contacts details using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min. required Artic Fox)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as “ex.no.3″ and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Get contacts details and Display details give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to print the text create your own content providers to get contacts details.
Developed by: SARAVANA KUMAR S
Registeration Number : 212224220090
*/
```

### activity_main.xml:
```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Experiment 04 - Get Contacts"
        android:textSize="22sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.176" />

    <Button
        android:id="@+id/btnContacts"
        android:layout_width="317dp"
        android:layout_height="48dp"
        android:text="Get Contacts"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView"
        app:layout_constraintVertical_bias="0.163" />

    <TextView
        android:id="@+id/txtContacts"
        android:layout_width="367dp"
        android:layout_height="248dp"
        android:paddingTop="20dp"
        android:textSize="16sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/btnContacts"
        app:layout_constraintVertical_bias="0.141" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

### MainActivity.java:
```java
package com.example.contactexp;

import android.Manifest;
import android.annotation.SuppressLint;
import android.database.Cursor;
import android.os.Bundle;
import android.provider.ContactsContract;
import android.widget.Button;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;
import androidx.core.app.ActivityCompat;

public class MainActivity extends AppCompatActivity {

    Button btnContacts;
    TextView txtContacts;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        btnContacts = findViewById(R.id.btnContacts);
        txtContacts = findViewById(R.id.txtContacts);

        ActivityCompat.requestPermissions(
                this,
                new String[]{Manifest.permission.READ_CONTACTS},
                1
        );

        btnContacts.setOnClickListener(v -> getContacts());
    }

    @SuppressLint("Range")
    private void getContacts() {

        Cursor c = getContentResolver().query(
                ContactsContract.CommonDataKinds.Phone.CONTENT_URI,
                null,
                null,
                null,
                null
        );

        StringBuilder s = new StringBuilder();

        assert c != null;

        while (c.moveToNext()) {

            String name = c.getString(
                    c.getColumnIndex(
                            ContactsContract.CommonDataKinds.Phone.DISPLAY_NAME));

            String number = c.getString(
                    c.getColumnIndex(
                            ContactsContract.CommonDataKinds.Phone.NUMBER));

            s.append(name)
                    .append(" : ")
                    .append(number)
                    .append("\n\n");
        }

        txtContacts.setText(s.toString());

        c.close();
    }
}
```

### AndroidManifest.xml:
```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <uses-permission android:name="android.permission.READ_CONTACTS"/>
    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Contactexp">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```

## OUTPUT
<img width="1920" height="1200" alt="01" src="https://github.com/user-attachments/assets/ec6d4318-d48a-4411-b3fa-1f2beb646ca8" />
<img width="1920" height="1200" alt="02" src="https://github.com/user-attachments/assets/3a31e2ad-83c1-497a-8613-01c8329eaa6e" />
<img width="1920" height="1200" alt="03" src="https://github.com/user-attachments/assets/24d99270-bd6a-4c40-ac72-2cbd9ce6277e" />



## RESULT
Thus a Simple Android Application create your own content providers to get contacts details using Android Studio is developed and executed successfully.
