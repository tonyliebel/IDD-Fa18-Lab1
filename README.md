# IDD-Fa18-Lab1: Blink!

**A lab report by Hartmut Tony Liebel***

**Fork** this repository to get a template for Lab 1 for *Developing and Designing Interactive Devices* at Cornell Tech, Fall 2018. You should modify this `README.md` file to delete this paragraph and update below. As the lab asks:

> Include your responses to the bold questions on your own fork of the lab activities. Include snippets of code that explain what you did. Deliverables are due next Tuesday. Post your lab reports as `README.md` pages on your GitHub, and post a link to that on your main class hub page.

We've copied the questions from the lab here. Answer them below!

## Part A. Set Up a Breadboard

Done

## Part B. Manually Blink a LED

**a. What color stripes are on a 100 Ohm resistor?**
Brown, Black, Brown, Tolerance
 
**b. What do you have to do to light your LED?**
Connect the Power from the Arduino to one side of the switch, diode to other side of switch, resistor on ground side of diode, resistor back to arduino ground.

## Part C. Blink a LED using Arduino

### 1. Blink the on-board LED

**a. What line(s) of code do you need to change to make the LED blink (like, at all)?**
void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(LED_BUILTIN, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(100);                       // wait for a second
  digitalWrite(LED_BUILTIN, LOW);    // turn the LED off by making the voltage LOW
  delay(100);                       // wait for a second
}
**b. What line(s) of code do you need to change to change the rate of blinking?**
delay()
**c. What circuit element would you want to add to protect the board and external LED?**
 A resistor or a fuse.
 
 
**d. At what delay can you no longer *perceive* the LED blinking? How can you prove to yourself that it is, in fact, still blinking?**
10ms is where you can no longer perceive the blink. By pointing a 30fps camera at it, I am able to confirm it is in fact still blinking.

**e. Modify the code to make your LED blink your way. Save your new blink code to your lab 1 repository, with a link on the README.md.**
*/

int led = 11;           // the PWM pin the LED is attached to
int brightness = 0;    // how bright the LED is
int fadeAmount = 5;    // how many points to fade the LED by

// the setup routine runs once when you press reset:
void setup() {
  // declare pin 11 to be an output:
  pinMode(led, OUTPUT);
}

// the loop routine runs over and over again forever:
void loop() {
  // set the brightness of pin 11:
  analogWrite(led, brightness);

  // change the brightness for next time through the loop:
  brightness = brightness + fadeAmount;

  // reverse the direction of the fading at the ends of the fade:
  if (brightness <= 0 || brightness >= 255) {
    fadeAmount = -fadeAmount;
  }
  // wait for 30 milliseconds to see the dimming effect
  delay(10);
}

### 2. Blink your LED

**Make a video of your LED blinking, and add it to your lab submission.
[Video Here](https://github.com/tonyliebel/IDD-Fa18-Lab1/blob/master/fastblink.MOV)

## Part D. Manually fade an LED

**a. Are you able to get the LED to glow the whole turning range of the potentiometer? Why or why not?**
No, because at full resistance, the LED should not be receiving the power it needs to illuminates

## Part E. Fade an LED using Arduino
[Video Here](https://github.com/tonyliebel/IDD-Fa18-Lab1/blob/master/fade.MOV)

**a. What do you have to modify to make the code control the circuit you've built on your breadboard?**
You have to switch the LED anode to a PWM pin, in this case pin 11.

**b. What is analogWrite()? How is that different than digitalWrite()?**
Analogwrite alows for the PWM pin to move between full power & off in a stepped pattern (i.e. actually fade) while digital write can only emit full power or no power.

## Part F. FRANKENLIGHT!!!


### 1. Take apart your electronic device, and draw a schematic of what is inside. 
[Schematic Here](https://github.com/tonyliebel/IDD-Fa18-Lab1/blob/master/schematic2.jpg)

**a. Is there computation in your device? Where is it? What do you think is happening inside the "computer?"**
Yes. It is right in the middle of the board. It is a calculator, so I assume it includes the logice behind addition, subtraction, multiplication etc. as well as serving as short term memory


**b. Are there sensors on your device? How do they work? How is the sensed information conveyed to other portions of the device?**
There are buttons that act as pressure sensors. The device is a basic calculator - so the buttons serve to bring physical pushes of the button to a correlated value that goes into the computer.


**c. How is the device powered? Is there any transformation or regulation of the power? How is that done? What voltages are used throughout the system?**
The device is powered by a small HG battery, as well as a small photvoltaic cell putting out 1.5volts. There are two capacitors on the board, and I see no resistors for power management.


**d. Is information stored in your device? Where? How?**
I think it must be stored in the computer.

### 2. Using your schematic, figure out where a good point would be to hijack your device and implant an LED.

**Describe what you did here.**
I found a small LED on the back of the calculator (actually, not sure what it's purpose is, as it is completely hidden in the casing).
I used the Arduino for power, and jumped the LED to PWM pin #11. By doing this, I was able to have the LED on the board of the calculator Fade and brighten up with a short delay. In addition, I cut two 

### 3. Build your light!

**Make a video showing off your Frankenlight.**
[Video Here](https://github.com/tonyliebel/IDD-Fa18-Lab1/blob/master/schematic.MOV)

**Include any schematics or photos in your lab write-up.**
