//Define Trig and Echo pin
#include <SoftwareSerial.h>
#define trigPin 6
#define echoPin 7
Int relay=10;
Int buz=4;
//Define variables
long duration;
Int distance;
Void setup()
{
Serial.begin(9600);
mySerial.begin(9600);
//Define inputs and outputs
pinMode(trigPin,OUTPUT);
pinMode(echoPin,INPUT);
pinMode(relay,OUTPUT);
pinMode(buz,OUTPUT);
//Begin Serial communication
Serial.begin(9600);
digitalWrite(relay,HIGH);
}
Void loop()
{/
/clear the trigPin by setting it LOW
digitalWrite(trigPin,LOW);
delayMicroseconds(5);
//Trigger the sensor by setting th trigpin high for 10 microseconds
digitalWrite(trigPin,HIGH);
delayMicroseconds(10);
digitalWrite(trigPin,LOW);
//Read the echoPin.pulseIn() returns the duration (length of the pulse) in microseconds.
duration=pulseIn(echoPin,HIGH);
//Calculate the distance
distance=duration*0.034/2;
//Print the distance on the Serial Monitor (ctrl+shift+M)
Serial.print(“Distance=”);
Serial.print(distance);
Serial.println(“cm”);
If (distance>=5)
{
digitalWrite(buz,HIGH);
digitalWrite(relay,LOW);
// lcd.print(“sendng sms”);
Delay(100);
mySerial.println(“AT+CMGS=\”phone.no.\”\r”);
Delay(100);
mySerial.println():
mySerial.println(“HIGH ALERT!!!”);
mySerial.println(“CRACK DETECTED ON TRACK”);
mySerial.println(“TRAIN STOPED”);
digitalWrite(buz,LOW);
delay(26000);
}}
