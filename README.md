

#include <Servo.h>

Servo servoCamX;
Servo servoCamY;

int posCamY = 90;
int posCamX = 90;

void setup(){
  // put your setup code here, to run once:
Serial.print("hello");
servoCamX.attach(2);
servoCamY.attach(4);

Serial.begin(9600);
servoCamX.write(posCamX);
servoCamY.write(posCamY);


}

void loop(){
  while(1) {
    Serial.print("hello");
    if(Serial.available())
    {
      char Command = Serial.read();
      switch(Command)
      {
        case 'i':
        posCamY = posCamY + 20;
        servoCamY.write(posCamY);
        break; 
        case 'k': 
        posCamY = posCamY - 20; 
        servoCamY.write(posCamY);
        break; 
        case 'j': 
        posCamX = posCamX + 20; 
        servoCamX.write(posCamX);
        break; 
        case 'l': 
        posCamX = posCamX - 20;
        servoCamX.write(posCamX);
        break; 
      } 
    } 
  }
}
