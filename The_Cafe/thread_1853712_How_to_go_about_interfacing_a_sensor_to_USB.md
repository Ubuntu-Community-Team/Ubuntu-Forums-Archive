---
title: "How to go about interfacing a sensor to USB?"
date: 2011-10-02
forum: The Cafe
---

### Post by flyingsliverfin on 2011-10-02
I was wondering where or how I can learn the basics of interfacing a sensor to USB for a project of mine. Eventually i would want to connect an accelerometer (for testing for very small vibrations) to a port, then somehow grab that input in a program (which i also still have to figure out how to write :))

Also something that doesn't go into nitty gritty details would be nice :) I've got about 3 months for this (but i also have to do schoolwork/sports/instrumental practice) which leaves about every weekend free...

---

### Post by alphacrucis2 on 2011-10-02
> **flyingsliverfin said:**
> I was wondering where or how I can learn the basics of interfacing a sensor to USB for a project of mine. Eventually i would want to connect an accelerometer (for testing for very small vibrations) to a port, then somehow grab that input in a program (which i also still have to figure out how to write :))

Also something that doesn't go into nitty gritty details would be nice :) I've got about 3 months for this (but i also have to do schoolwork/sports/instrumental practice) which leaves about every weekend free...

What sort of electrical ouput does the accelerometer have? Some are available with USB. Older ones might output RS 232 style serial for which you could use a serial-usb converter. You will also need software to read the data from the USB port.

---

### Post by euler_fan on 2011-10-02
> **alphacrucis2 said:**
> What sort of electrical ouput does the accelerometer have? Some are available with USB. Older ones might output RS 232 style serial for which you could use a serial-usb converter. You will also need software to read the data from the USB port.

+1: If you have already picked up the sensors, then posting the specs would be a big help.

On the other hand, there are development boards for various processors which have analogue inputs that could be used. Arduino is one example of such a family. I have also messed around with ARM-based development boards where the analogue input is written to a memory address which can then be read. Either will require learning assembly or something like it.

---

### Post by compubob on 2011-10-02
your best bet is getting an Arduino
you can read many types of sensors, hook up a LCD display if you want and readout whatever info you want. You can output all your data to serial and write a program in whatever language you want to capture it and even output back to the arduino.
I have done many things with Arduino's which include controlling climate in small greenhouses and even controlling the all wheel drive system on a race car with a G-Sensor.

---

### Post by flyingsliverfin on 2011-10-02
> **alphacrucis2 said:**
> What sort of electrical ouput does the accelerometer have? Some are available with USB. Older ones might output RS 232 style serial for which you could use a serial-usb converter. You will also need software to read the data from the USB port.


I haven't got one yet, I'm still gathering general info. First time I'm doing something like this, so i figured research first then actually start

---

### Post by flyingsliverfin on 2011-10-02
> **compubob said:**
> your best bet is getting an Arduino
you can read many types of sensors, hook up a LCD display if you want and readout whatever info you want. You can output all your data to serial and write a program in whatever language you want to capture it and even output back to the arduino.
I have done many things with Arduino's which include controlling climate in small greenhouses and even controlling the all wheel drive system on a race car with a G-Sensor.

Sounds like a place to start. I'll look into this next weekend (its already sunday night!!! :( )

---

### Post by red_Marvin on 2011-10-03
Be aware that moust if not all accelerometers available are surface mount,
and on the trickier side of the surface mount scale too, are you proficient
with a soldering iron?

I think sparkfun has some breakout boards for various sensors though, probably other places too.

A minimal setup would likely consist of the sensor chip, a microcontroller
and an ft232 rs232 to usb converter. The microcontroller is needed since
you are unlikely to find a sensor chip that you can connect directly to
the ft232 circuit. The microcontroller would need to be programmed, so you'd
need hardware for that too.

By the level of your questions I'd guess that you are new at this, so an
arduino as mentioned above is probably a good idea, you get the microcontroller,
the computer interface as well as the programming hardware in one package.
As for the sensor, I'd suggest you'll try to find one with an SPI interface
and mounted on a breakout board. Make sure that it is 5V tolerant, or that
neccesary circuitry is mounted on the breakout board.

---

### Post by flyingsliverfin on 2011-10-03
I'm a fairly competent solderer, but I don't know much of the other stuff... sounds like Arduino is the best bet. 
Too bad they don't teach any of this stuff in high school, seems like it could get really interesting.

---

### Post by flyingsliverfin on 2011-10-10
So according to my math, I'd be measuring a ~1 mHz vibration... possibly lower depending on what kind of material i decide to use in the end. That seems like a good number to start with though :) 
Depending again on the material the amplitude of the wave would be around 1 micrometer.

Out of time again... next weekend ill continue

---

### Post by red_Marvin on 2011-10-10
I'm usually not nitpicky when it comes to capitalization of m/M prefixes,
since it is usually obvious from context what wether milli or Mega is
meant. But since it would here mean two very different measurement
situations; do you mean milliHz or MegaHz?

Also, since it is a question of movement on the micrometer scale,
you would do well to check the sensitivity of any sensors you
consider.

---

### Post by flyingsliverfin on 2011-10-10
oops yes its 1 **M**Hz

also just found out the ADC sampling rate of the arduino is ideally 10 KHz... might need to find an external board then.

---

### Post by red_Marvin on 2011-10-11
Well, if you can find a sensor that is digital (e.g. communicates with SPI)
and has high enough sampling rate, there should be no problem, in that respect.

However, how many points per oscillation period do you need? If you want to
measure frequency, the nyquist theorem says that you will need two points
per oscillation of the highest frequency that you want to be able to measure,
in your case with a 1MHz *upper* bound, it would mean sampling at 2MHz,
which in turn, assuming SPI, and 8bit resolution would imply 16MHz continuous
data transfer, ignoring things like the slave select toggling, and sending
command words that you likely will need to do.

Now imagine 1MHz not being the upper bound, but somewhere in the middle,
and you want up to 2MHz with 16 bit resolution - then you need 64MHz
data transfer rate at the least, out of the league of any avr.

However, the digital electronics is not your problem, there is always a
bigger and faster (and more expensive) controller you can get,
however your requirements for the sensor seems tough (high frequency,
high sensitivity), have you considered other things than an accelerometer?
Maybe piezoelectric materials?
Edit: another suggestion I got from #electronics was strain gauges.

In other words, find a suitable sensor, before locking yourself to a processor
architecture and setup.

Also, what is your budget for this? Can you borrow equipment?
Is this for school? (it sounds like it) If so, on what level?
What is it that you actually want to measure?

---

### Post by Paqman on 2011-10-11
> **flyingsliverfin said:**
> oops yes its 1 **M**Hz


Yeah, 1mHz would be less of a vibration, and more of a very leisurely swaying.

---

### Post by flyingsliverfin on 2011-10-11
Yea i was looking at piezoelectric sensors actually - using an accelerometer seems too complicated. I think these analog(?). Therefore I need an ADC.
Its part of a personal project that I may submit to science fair, I'm still thinking about it.
Its not for school... my high school doesn't offer anything Electrical engineering and not much in terms of CS (only 2 classes, computer programming (basic) and AP comp sci which I'm taking in 11th grade -next year- but I doubt they teach anything like this). I wish they did but I don't think many people would sign up. Our programming club only has about 20 members (of 2400 students across all 4 grades), if that's a good indicator for interest

> **red_Marvin said:**
> 

Now imagine 1MHz not being the upper bound, but somewhere in the middle,
and you want up to 2MHz with 16 bit resolution - then you need 64MHz
data transfer rate at the least, out of the league of any avr.


Just wondering, wouldn't that be 16*2 = 32 MHz? maybe I'm wrong, just started learning about all this resolution/MHz stuff

---

### Post by red_Marvin on 2011-10-13
If the highest frequency signal you want to measure is 2MHz you need to sample at 4MHz, as per the Nyquist theorem.

---

### Post by flyingsliverfin on 2011-10-13
ah now i see where u got that number  :)

---

### Post by flyingsliverfin on 2011-10-14
Im having trouble finding out how to convert my 1 um (the amplitude of the vibration) to something I can apply to sensitivity of sensors. Piezoelectric sensor sensitivity always seems to be given in mV/g. How does this relate to the amplitude of the wave I'm measuring? Why do they show in terms of g?

---

### Post by flyingsliverfin on 2011-10-14
Actually I figured it out with some help from my dad:
Assuming its 1 Mhz and 1 um amplitude (no longer sure about these values esp amplitude):
time for 1 period = 1/10^6th of a second 
z(t) = 1um * sin(t*2pi/(1/10^6))
take second derivative:
z" = -4pi^2*1um*10^12 (sin(2pi*t/T)) 

the sin part can be ignored since we're concerned with the max height and that turns to 1 so:

z" = -4pi^2 * 1m * 10^6 = m/s^2
(ignore - part)
&#8722;39478417.6/9.18 (g) = 4300481 g's

that's a pretty huge acceleration

---

### Post by euler_fan on 2011-10-16
If you really believe you know where most of the energy in the signal is (for instance, you have some good reason to believe that there are no significant vibrations outside 0.75-1.25 MHz) then you could also intentionally under-sample the signal and then use aliasing to retrieve data in the correct frequency band. 

Just bear in mind that you need to be very sure about the signal or else your data will be useless because you will never be able to pull out just the part you are looking for from the lower frequency signals in the aliased band.

Roberto Christi's Digital Signal Processing book gives a good introduction to this process.

---

### Post by HermanAB on 2011-10-17
Here you go:
[http://labjack.com/products](http://labjack.com/products)

---

### Post by red_Marvin on 2011-10-17
It seems that the labjack has too low sample rate unless 1) I have missed something or 2) one goes the aliasing route.

---

### Post by flyingsliverfin on 2011-12-09
ended up getting one of [these]("http://www.ti.com/product/ads7886") ADC's to play around with. Looked like one of the simplest I could find (only 6 pins :D; less confusion for me)

---

