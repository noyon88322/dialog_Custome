
# Dialog Custome

CREATED BY NOYON BISWAS

![esport_24_logo](https://github.com/user-attachments/assets/0478002c-4abf-4a96-a718-7c1dacf93a83)



#  STEP : 1

### Go TO res => layout => create > dialo_layout.xml





   ```bash
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="@dimen/_250sdp"
    android:layout_height="@dimen/_210sdp"
    android:orientation="vertical"
    android:layout_gravity="center"
    android:layout_margin="@dimen/_10sdp"
    android:background="@drawable/shade_dialog">

    <ImageView
        android:id="@+id/dia_log_img"
        android:layout_width="@dimen/_45sdp"
        android:layout_height="@dimen/_45sdp"
        android:src="@drawable/logout"
        android:layout_gravity="center"
        android:layout_marginTop="@dimen/_10sdp"
        />

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Do You Really Want \n Logout?"
        android:gravity="center"
        android:textSize="@dimen/_20sdp"
        android:fontFamily="@font/poppins_regular"
        android:layout_marginTop="@dimen/_15sdp"
        />


    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:weightSum="2"
        android:padding="@dimen/_20sdp"
        >
        <androidx.appcompat.widget.AppCompatButton
            android:id="@+id/btn_yes"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="NO"
            android:background="#F60000"
            android:textColor="#FAF7F7"
            android:layout_weight="1"
            android:layout_marginRight="@dimen/_10sdp"

            />

        <androidx.appcompat.widget.AppCompatButton
            android:id="@+id/btn_no"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="YES"
            android:background="#1BFB24"
            android:textColor="#FAF7F7"
            android:layout_weight="1"
            android:layout_marginLeft="@dimen/_10sdp"

            />






    </LinearLayout>
</LinearLayout>

  ```


   
  ## Open Theme.xml 



   ```bash

<resources xmlns:tools="http://schemas.android.com/tools">


    <!-- In res/values/styles.xml -->
    <style name="Dialog" parent="Theme.AppCompat.Light.Dialog">
        <item name="android:windowBackground">@android:color/white</item>
        <item name="android:windowNoTitle">true</item>
        <item name="android:windowIsTranslucent">true</item>
        <item name="android:backgroundDimEnabled">true</item>
    </style>
</resources>

   ```






 # MainActivity.java
 Step 5


   ```bash


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        img_logout = findViewById(R.id.img_logout);

        /////LogOut Dialog

        img_logout.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Dialog dialog = new Dialog(MainActivity.this,R.style.Dialog);
                dialog.setContentView(R.layout.dialog_layout);

                AppCompatButton btn_yes,btn_no;

                btn_yes = dialog.findViewById(R.id.btn_yes);
                btn_no = dialog.findViewById(R.id.btn_no);

                btn_yes.setOnClickListener(new View.OnClickListener() {
                    @Override
                    public void onClick(View v) {
                        FirebaseAuth.getInstance().signOut();
                        Intent i = new Intent(MainActivity.this,login.class);
                        startActivity(i);
                    }
                });
                btn_no.setOnClickListener(new View.OnClickListener() {
                    @Override
                    public void onClick(View v) {
                        dialog.dismiss();
                    }
                });
                dialog.show();
            }
        });



   ```
