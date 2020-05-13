# stone-paper-scissor
a game in android studio
package com.example.rockpaperscissor;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.ImageView;
import android.widget.TextView;
import android.widget.Toast;

import java.util.Random;

public class MainActivity extends AppCompatActivity {

    Button b_rock, b_scissor, b_paper;
    TextView tv_score;
    ImageView iv_ComputerChoice, iv_HumanChoice;

    int HumanScore,ComputerScore = 0;


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        b_paper = (Button) findViewById(R.id.b_paper);
        b_scissor = (Button) findViewById(R.id.b_scissor);
        b_rock = (Button) findViewById(R.id.b_rock);

        iv_ComputerChoice = (ImageView) findViewById(R.id.iv_ComputerChoice);
        iv_HumanChoice = (ImageView) findViewById(R.id.iv_HumanChoice);

        tv_score = (TextView) findViewById(R.id.tv_score);

        b_paper.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                iv_HumanChoice.setImageResource(R.drawable.paper);
                String message = play_turn("paper");
                Toast.makeText(MainActivity.this, message, Toast.LENGTH_SHORT).show();
                tv_score.setText("SCORE HUMAN: " +Integer.toString(HumanScore) + " || COMPUTER: " +Integer.toString(ComputerScore));
            }


        });

        b_rock.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                iv_HumanChoice.setImageResource(R.drawable.rock);
                String message = play_turn("rock");
                Toast.makeText(MainActivity.this, message, Toast.LENGTH_SHORT).show();
                tv_score.setText("SCORE HUMAN: " +Integer.toString(HumanScore) + " || COMPUTER: " +Integer.toString(ComputerScore));



            }


        });

        b_scissor.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                iv_HumanChoice.setImageResource(R.drawable.scissor);
                String message = play_turn("scissor");
                Toast.makeText(MainActivity.this, message, Toast.LENGTH_SHORT).show();
                tv_score.setText("SCORE HUMAN: " +Integer.toString(HumanScore) + " || COMPUTER: " +Integer.toString(ComputerScore));
            }


        });


    }

    public String play_turn( String player_choice ){

        String computer_choice="";
        Random r=new Random();


        int computer_choice_number = r.nextInt(3)+1;
        if (computer_choice_number==1){
            computer_choice="rock";
        }else

        if (computer_choice_number==2) {
            computer_choice="scissor";
        }else

        if (computer_choice_number==3) {
            computer_choice="paper";
        }

        if (computer_choice=="rock") {
            iv_ComputerChoice.setImageResource(R.drawable.rock);

        } else

        if (computer_choice=="scissor") {
            iv_ComputerChoice.setImageResource(R.drawable.scissor);

        } else

        if (computer_choice=="paper") {
            iv_ComputerChoice.setImageResource(R.drawable.paper);

        }




        if(computer_choice == player_choice) {
            return " It's a TIE " ;
        }
        else if (player_choice =="scissor"&& computer_choice == "rock" ) {
            ComputerScore++;
            return "Rock crushes scissors. Computer Win!!!";

        }
        else if (player_choice =="scissor" && computer_choice == "paper") {
            HumanScore++;
            return "Scissor cuts paper. You Win!!!";

        }

        else if (player_choice =="rock" && computer_choice == "scissor") {
            HumanScore++;
            return "Rock crushes scissors. You Win!!!";

        }

        else if (player_choice =="rock" && computer_choice == "paper") {
            ComputerScore++;
            return "Paper covers rock . Computer Win!!!";

        }
        else if (player_choice =="paper" && computer_choice == "rock") {
            HumanScore++;
            return "Paper covers Rock. You Win!!!";

        }
        else if (player_choice =="paper" && computer_choice == "scissor") {
            ComputerScore++;
            return "Scissor cuts Paper. Computer Win!!!";

        }
        else{
            return "don't know";
        }
  }



}






---------------------------------------------------

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/tv_humanChoice"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Human Choice"
        android:textColor="#0E1871"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.2"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.042" />

    <ImageView
        android:id="@+id/iv_HumanChoice"
        android:layout_width="252dp"
        android:layout_height="191dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.164"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:srcCompat="@drawable/paper" />

    <Button
        android:id="@+id/b_rock"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="ROCK"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toStartOf="@+id/b_paper"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.955" />

    <Button
        android:id="@+id/b_paper"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="PAPER"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toStartOf="@+id/b_scissor"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.955" />

    <Button
        android:id="@+id/b_scissor"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="SCISSOR"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.377"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.955" />

    <ImageView
        android:id="@+id/iv_ComputerChoice"
        android:layout_width="252dp"
        android:layout_height="191dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.824"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:srcCompat="@drawable/rock" />

    <TextView
        android:id="@+id/tv_ComputerChoice"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Computer Choice"
        android:textColor="#0C0C5D"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.79"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.042" />

    <TextView
        android:id="@+id/tv_score"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="SCORE  human : 0  ||  computer : 0"
        android:textAllCaps="true"
        android:textColor="#0C0C0C"
        android:textSize="18sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.904"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.909" />
</androidx.constraintlayout.widget.ConstraintLayout>


----------------------------------------------------------------


<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/tv_humanChoice"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Human Choice"
        android:textColor="#0E1871"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.022" />

    <ImageView
        android:id="@+id/iv_HumanChoice"
        android:layout_width="252dp"
        android:layout_height="191dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.522"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.19"
        app:srcCompat="@drawable/paper" />

    <ImageView
        android:id="@+id/iv_ComputerChoice"
        android:layout_width="252dp"
        android:layout_height="191dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.468"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.699"
        app:srcCompat="@drawable/rock" />

    <Button
        android:id="@+id/b_paper"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="PAPER"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toStartOf="@+id/b_scissor"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.86" />

    <Button
        android:id="@+id/b_rock"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="ROCK"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toStartOf="@+id/b_paper"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.86" />

    <Button
        android:id="@+id/b_scissor"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="SCISSOR"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.801"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.86" />

    <TextView
        android:id="@+id/tv_ComputerChoice"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Computer Choice"
        android:textColor="#0C0C5D"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.459" />

    <TextView
        android:id="@+id/tv_score"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="SCORE  human : 0  ||  computer : 0"
        android:textAllCaps="true"
        android:textColor="#0C0C0C"
        android:textSize="18sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.954" />
</androidx.constraintlayout.widget.ConstraintLayout>

-----------------------------------------------------


<resources>

    <!-- Base application theme. -->
    <style name="AppTheme" parent="Base.Theme.AppCompat.Light.DarkActionBar">
        <!-- Customize your theme here. -->
        <item name="colorPrimary">@color/colorPrimary</item>
        <item name="colorPrimaryDark">@color/colorPrimaryDark</item>
        <item name="colorAccent">@color/colorAccent</item>
    </style>

</resources>


