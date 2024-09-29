# pgm3

import android.content.Intent;
import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    private Button btn;
    private EditText edit;
    private String tag = "Event";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);
        Log.d(tag, "In the onCreate() event");

        btn = findViewById(R.id.button1);
        edit = findViewById(R.id.e1);

        btn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String text = edit.getText().toString();
                Intent i = new Intent(MainActivity.this, MainActivity2.class);
                i.putExtra("key1", text);
                startActivity(i);
            }
        });
    }

    @Override
    protected void onStart() {
        super.onStart();
        Log.d(tag, "In the onStart() event");
    }

    @Override
    protected void onRestart() {
        super.onRestart();
        Log.d(tag, "In the onRestart() event");
    }

    @Override
    protected void onResume() {
        super.onResume();
        Log.d(tag, "In the onResume() event");
    }

    @Override
    protected void onPause() {
        super.onPause();
        Log.d(tag, "In the onPause() event");
    }

    @Override
    protected void onStop() {
        super.onStop();
        Log.d(tag, "In the onStop() event");
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        Log.d(tag, "In the onDestroy() event");
    }
}
main activity 2

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;
import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity2 extends AppCompatActivity {
    private Button button;
    private TextView view;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main2);

        button = findViewById(R.id.button);
        view = findViewById(R.id.view);

        String text1 = getIntent().getStringExtra("key1");
        if (text1 != null) {
            view.setText(text1);
        } else {
            view.setText("No name provided");
        }

        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent i = new Intent(MainActivity2.this, MainActivity.class);
                startActivity(i);
            }
        });
    }
}
