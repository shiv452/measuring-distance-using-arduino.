// define the ultrasonic pin's//
#define trigPin  5 // OUTPUT PIN//
#define echoPin  6 //INPUT PIN//

//Defing the led's pin//
#define led1  7
#define led2  8
#define led3  9
#define led4  10
#define led5  11
#define buzzer  13

//buzzer sound//
 int sound = 300;t

//veryfing the output and input pin's//
 void setup()
 {
Serial.begin(9600); // starting the serial communication//
pinMode(trigPin,OUTPUT);
pinMode(echoPin,INPUT);
pinMode(led1,OUTPUT);
pinMode(led2,OUTPUT);
pinMode(led3,OUTPUT);
pinMode(led4,OUTPUT);
pinMode(led5,OUTPUT);
pinMode(buzzer,OUTPUT);


 }
 
void loop()
{
  long duration,distance;
  digitalWrite(trigPin,LOW);
  delay(2);
  digitalWrite(trigPin,HIGH);
  delay(10);
  digitalWrite(trigPin,LOW);

    duration = pulseIn(echoPin,HIGH);
    distance =(duration/2)/29.1;

    if (distance <= 40)
    {
      digitalWrite(led1,HIGH);
      sound = 300;
    }
    else
    {
      digitalWrite(led1,LOW);
    }
    if (distance < 35)
    {
      digitalWrite(led2,HIGH);
      sound =310;
    }
    else
    {
      digitalWrite(led2,LOW);
    }
    if(distance < 30)
    {
      digitalWrite(led3,HIGH);
      sound =320;
    }
    else
    {
      digitalWrite(led3,LOW);
    }
    if (distance <25)
    {
      digitalWrite(led4,HIGH);
      sound =330;
    }
    else
    {
      digitalWrite(led4,LOW);
    }
    if (distance <20)
    {
      digitalWrite(led5,HIGH);
      sound = 340;
    }
    else
    {
      digitalWrite(led5,LOW);
    }

    if(distance > 40|| distance <=0)
    {
      Serial.println("outof range");
      noTone(buzzer);
      }
      else
      {
        Serial.print(distance);
        Serial.println("cm");
        tone(buzzer,sound);
        
      }
delay(500);
}

  
    
    
    
    
  
    
