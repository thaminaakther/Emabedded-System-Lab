# Emabedded-System-Lab
#Arduino Radar Model for Distance and Angle Finding using Ultrasonic Sensor and Servo Motor


## Components used / Material
* Arduino uno
* Ultrasonic sensor
* Servo Motor


## Code
```
#include <Servo.h>. 
const int trigPin = 10;
const int echoPin = 11;
long duration;
int distance;
Servo myServo;

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT); 
  Serial.begin(9600);
  myServo.attach(12); 
}
void loop() {
  for(int i=15;i<=165;i++){  
    myServo.write(i);
    delay(30);
    distance = calculateDistance();
    Serial.print(i);
    Serial.print(","); 
    Serial.print(distance); 
    Serial.print("."); 
  }


  for(int i=165;i>15;i--){  
    myServo.write(i);
    delay(30);
    distance = calculateDistance();
    Serial.print(i);
    Serial.print(",");
    Serial.print(distance);
    Serial.print(".");
  }
}

int calculateDistance(){ 
  
  digitalWrite(trigPin, LOW); 
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH); 
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH); 
  distance= duration*0.034/2;
  return distance;
}
```

## Circuit Diagram
![image](https://github.com/thaminaakther/Emabedded-System-Lab/blob/dfcd4255a8c3f8d5280b651233b3a68b8a019f0a/radar_circuit_diagram.png)
