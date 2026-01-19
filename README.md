// Pin where MQ-2 gas sensor analog output is connected
int gasSensorPin = A0;
// Pin where buzzer is connected
int buzzerPin = 8;
// Gas level limit (decided after observing sensor readings)
int gasThreshold = 400;
void setup() {
// Set buzzer as output device
pinMode(buzzerPin, OUTPUT);
// Start serial communication to monitor gas values
Serial.begin(9600);
Serial.println("Gas Detector System Started...");
}
void loop() {
// Read analog value from MQ-2 sensor
int gasValue = analogRead(gasSensorPin);
// Display gas value on Serial Monitor
Serial.print("Gas Level: ");
Serial.println(gasValue);
// Check if gas level crosses safe limit
if (gasValue > gasThreshold) {
// Gas detected – activate buzzer
digitalWrite(buzzerPin, HIGH);
Serial.println(" WARNING: Gas Leakage Detected!");
}
else {
// Gas level is safe – keep buzzer off
digitalWrite(buzzerPin, LOW);
Serial.println("Gas level is normal.");
}
