Tugas
Buatkanlah :

Launcher Splash logo masing-masing Individu

Buatkanlah untuk menampilkan semua project sebelum UTS dengan metode Ekplisit Intent dan Implisit Intent:

a. Project Hallo

b. Project Count

c. Project Sianida

d. Project TwoActivity

e. Project Set Alarm

Untuk tampilan Layout Bebas, terima kasih.

Apa itu Explicit dan Implicit Intent?

    Intent Implicit: Berfungsi melakukan perpindahan activity (halaman) menuju ke aplikasi internal smartphone kamu. Contohnya ketika kamu hendak membuka sebuah kamera. Project yang termasuk Implicit Intent adalah Project Alarm

    Intent Explicit: Berfungsi melakukan perpindahan activity (halaman) ke activity (halaman) lainnya. Project yang termasuk adalah Explicit Intent adalah Project Splash,Hallo,Count,Sianida dan Two Activity.

<h1>Splash Activity Code </h1>

SpalashActivity

```java
package id.co.myapplication;

import android.content.Intent;
import android.os.Bundle;
import android.os.Handler;

import androidx.appcompat.app.AppCompatActivity;

public class SplashActivity extends AppCompatActivity {
    private static final int SPLASH_TIMEOUT = 5000;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_splash);

        new Handler().postDelayed(new Runnable() {
            @Override
            public void run() {
                Intent intent = new Intent(SplashActivity.this, MainActivity.class);
                startActivity(intent);
                finish();
            }
        }, SPLASH_TIMEOUT);
    }
}


```

<h1>Project Hello</h1>

MainHello.java

```java

package id.co.myapplication;

import android.content.Intent;
import android.os.Bundle;

import androidx.appcompat.app.AppCompatActivity;

public class MainHello extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_hello);
        Intent tampilHello = getIntent();
    }
}
```
activity_hello.xml

```xml

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainHello">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        android:textSize="100px"
        android:textColor="@color/red"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>

```
<h1>Project Count</h1>

```java
package id.co.myapplication;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.TextView;
import android.widget.Toast;
import android.widget.EditText;

public class MainToast extends AppCompatActivity {
    private int hitung = 1;
    private TextView showHitung;
    private int fib1 = 1; // Nilai pertama dalam deret Fibonacci
    private int fib2 = 1; // Nilai kedua dalam deret Fibonacci
    private EditText inputCount;
    private boolean maxCountSet = false;
    private int maxCount = 0;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_toast);
        showHitung = (TextView) findViewById(R.id.show_count);
        inputCount = (EditText) findViewById(R.id.max_input);
        fib1 = 1;
        fib2 = 1;
        showHitung.setText(Integer.toString(fib1));
    }

    public void showToast(View view) {
        Toast toast = Toast.makeText(this, R.string.toast_message, Toast.LENGTH_SHORT);
        toast.show();
        showHitung.setText(Integer.toString(1));
    }

    public void countBack(View view) {
        fib1 = 1;
        fib2 = 1;
        maxCount = 0;
        maxCountSet = false;
        inputCount.setText("");
        showHitung.setText(Integer.toString(0));
    }

    public void setMaxCount(View view) {
        String maxCountString = inputCount.getText().toString();
        if (!maxCountString.isEmpty()) {
            int newMaxCount = Integer.parseInt(maxCountString);
            if (newMaxCount >= 0) {
                maxCount = newMaxCount;
            }
        }
    }
    public void countUp(View view) {
        String maxCountString = inputCount.getText().toString();

        if (!maxCountString.isEmpty()) {
            int maxCount = Integer.parseInt(maxCountString);
            int nextFib = fib1 + fib2;

            if (maxCount >= 0) {
                if (fib1 <= maxCount) {
                    if (nextFib <= maxCount) {
                        fib1 = nextFib;
                        int temp = fib1;
                        fib1 = fib2;
                        fib2 = nextFib;
                    } else {
                        fib2 = maxCount;
                    }
                    showHitung.setText(Integer.toString(fib2));
                } else {
                    fib1 = 1;
                    fib2 = 1;
                    showHitung.setText(Integer.toString(0));
                }
            }
        } else {
            int nextFib = fib1 + fib2;
            fib1 = fib2;
            fib2 = nextFib;
            showHitung.setText(Integer.toString(fib1));
        }
    }
}
```
activity_toast.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools">

    <Button
        android:id="@+id/button_toast"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        android:layout_marginEnd="200dp"
        android:background="@color/red"
        android:onClick="showToast"
        android:text="@string/button_label_max"
        android:textColor="@android:color/white"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="UsingOnClickInXml" />

    <Button
        android:id="@+id/button_count"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginBottom="8dp"
        android:layout_marginEnd="200dp"
        android:layout_marginStart="8dp"
        android:background="@color/red"
        android:onClick="countUp"
        android:text="@string/button_label_count"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml" />

    <TextView
        android:id="@+id/show_count"
        android:layout_width="0dp"
        android:layout_height="0dp"
        android:layout_marginBottom="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        android:background="#FFFFFF"
        android:gravity="center_vertical"
        android:text="@string/count_initial_value"
        android:textAlignment="center"
        android:textColor="@color/red"
        android:textSize="160sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@+id/button_count"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/button_toast"
        tools:ignore="RtlCompat" />

    <EditText
        android:id="@+id/max_input"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="200dp"
        android:layout_marginTop="8dp"
        android:layout_marginEnd="8dp"
        android:background="@color/red"
        android:text="@string/text_max"
        android:textColor="@color/white"
        android:textSize="36sp"
        android:inputType="number"
        android:onClick="setMaxCount"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/button_back"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginBottom="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginStart="200dp"
        android:background="@color/red"
        android:onClick="countBack"
        android:text="@string/button_label_back"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

<h1>Project Two Activity</h1>
