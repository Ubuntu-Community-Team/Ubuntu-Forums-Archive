---
title: "Serial Port Project"
date: 2012-04-21
forum: The Cafe
---

### Post by sandyd on 2012-04-21
I recently decided that I wanted to create a project with a huge array of LEDs as indicators.

They would be controlled via serial port (believe me, I actually still have one) by a running script.

Anyone have any suggestions on what I should use for a PIC controller?

The entire thing is probably going to be powered by the Raspberry Pi board via a usb-> serial

---

### Post by ssam on 2012-04-21
the simplest thing would be to use an arduino (or similar). They are very easy to talk to over serial, and very easy to attach to LEDs or other indicator/sensors. The modern arduinos have a built in USB to serial chip, so they plug into USB, but look like a serial port. Some old ones have actual serial ports.

---

### Post by Bandit on 2012-04-21
Hmm, I need to get into doing projects like these. The ARDUINO looks pretty kewl. What ever you do please keep us posted as I would love to follow your progress.

---

### Post by drdos2006 on 2012-04-21
The Raspberry is an ARM device, supported programming appears to be Python although Qt4 is mentioned.

My impression is the USB is controlling interface. 

Looking at this it appears you need an expansion board.
Also the PIC has been changed to an Atmel chip, rather than a PIC.

[http://www.raspberrypi.org/archives/868](http://www.raspberrypi.org/archives/868)

regards
[edit]
However, I did find this. 
[http://lavalink.com/2012/03/raspberry-pi-serial-interfacing/](http://lavalink.com/2012/03/raspberry-pi-serial-interfacing/)

For a PIC or Atmel chip to receive RS232 serial comms you would need an interfacce to change the signal level for the chip to be able to transmit/receive to the RS232 interface.
[/edit]

---

### Post by sandyd on 2012-04-21
Hmm....
Ive made some progress in my research.

The arduinos don't have enough power to light up many LEDs (Im looking at 10+). I haven't figured how to work with that, but I can probably attach it using one of these [http://www.creatroninc.com/index.php/arduino/shields-for-arduino/arfpa-032044.html](http://www.creatroninc.com/index.php/arduino/shields-for-arduino/arfpa-032044.html)

The arduino can be controlled via serial ([http://forums.trossenrobotics.com/tutorials/how-to-diy-128/complete-control-of-an-arduino-via-serial-3300/](http://forums.trossenrobotics.com/tutorials/how-to-diy-128/complete-control-of-an-arduino-via-serial-3300/)).

If I can't get the serial port rolling, Ill just add a USB Shield ([http://www.creatroninc.com/index.php/arduino/shields-for-arduino/ardus-009947.html](http://www.creatroninc.com/index.php/arduino/shields-for-arduino/ardus-009947.html)). After all, USB is still serial...

Does anyone know where to get Tri-color LEDs?
I mean the ones where both can be on at once in order to produce the third color. Red and green (forming yellow) would be awesome.

---

### Post by drdos2006 on 2012-04-21
The Raspberry has two serial connections. The serial connections can go to a MAX232 which runs off 5 volts, same voltage as Atmel chip.
The MAX232 converts RS232 to TTL signal levels.

Program the Atmel chip to receive serial commands from the Raspberry, Atmel chip runs the LEDS. If you need more power for the LEDs then attach the LEDS to 12 volt power.

regards
[edit]
ATmega8-16PI 28 Pin PDIP, 8kb flash, 16MHz
ATmega128-16AI 40Pin TQFP, 128k x 8 flash, 16MHz
ATmega162-16PI 40Pin PDIP, 16k flash, 2 x UART, 16MHz

If you use the ATmega162 then you do not need a MAX232 as the conversion is done on the chip.
This chip has 35 I/O lines.

If you use the ATmega128 then you will need a MAX232. This chip has 32 I/O lines.

If you use the ATmega8 then you will need a MAX232. This chip has 23 I/O lines.

Tri-colour LEDS are VERY VERY expensive.
[/edit]

---

### Post by sandyd on 2012-04-21
> **drdos2006 said:**
> The Raspberry has two serial connections. The serial connections can go to a MAX232 which runs off 5 volts, same voltage as Atmel chip.
The MAX232 converts RS232 to TTL signal levels.

Program the Atmel chip to receive serial commands from the Raspberry, Atmel chip runs the LEDS. If you need more power for the LEDs then attach the LEDS to 12 volt power.

regards
[edit]
ATmega8-16PI 28 Pin PDIP, 8kb flash, 16MHz
ATmega128-16AI 40Pin TQFP, 128k x 8 flash, 16MHz
ATmega162-16PI 40Pin PDIP, 16k flash, 2 x UART, 16MHz

If you use the ATmega162 then you do not need a MAX232 as the conversion is done on the chip.
This chip has 35 I/O lines.

If you use the ATmega128 then you will need a MAX232. This chip has 32 I/O lines.

If you use the ATmega8 then you will need a MAX232. This chip has 23 I/O lines.

Tri-colour LEDS are VERY VERY expensive.
[/edit]
The ATmega162 it is then.
Since tri-color LEDs are expensive, Ill probably use dual-color LEDs, or something like [this]("http://search.digikey.com/scripts/dksearch/dksus.dll?site=us&lang=en&mpart=569-0112-300F&vendor=350")

And raspbery pis are currently out of stock. Ill wait.

---

### Post by drdos2006 on 2012-04-21
Well if the Raspberry is out of stock then just use the Atmel to connect to your serial port. Again, allow the Atmel to read the serial port and control the LEDs.

regards

---

### Post by Bandit on 2012-04-21
> **sandyd said:**
> Hmm....
Ive made some progress in my research.

The arduinos don't have enough power to light up many LEDs ...........
I recommend just using the card to trigger a relay. That way you can adjust the power requirements needed for the LEDs with very little limitations and then just use the cards low voltage to trigger the relay. Athough this can be a noisy solution if you run a mechanical (electro magnetic style) relay which are used in higher voltage/amperage solution like the lights on your car. But not expensive. Electronic relays are pretty much silent, but may cost more and cant handle as much voltage.

---

### Post by sandyd on 2012-04-22
> **drdos2006 said:**
> Well if the Raspberry is out of stock then just use the Atmel to connect to your serial port. Again, allow the Atmel to read the serial port and control the LEDs.

regards
I'm using the Raspberry to run the scripts that control the LEDs.
I.E. wget, ping, .etc .etc

---

### Post by sandyd on 2012-04-22
> **Bandit said:**
> I recommend just using the card to trigger a relay. That way you can adjust the power requirements needed for the LEDs with very little limitations and then just use the cards low voltage to trigger the relay. Athough this can be a noisy solution if you run a mechanical (electro magnetic style) relay which are used in higher voltage/amperage solution like the lights on your car. But not expensive. Electronic relays are pretty much silent, but may cost more and cant handle as much voltage.
Ive been thinking of pulling out the arduino all together, and using my own PIC. I have several extremely powerful (actually their adjustable) A/C Adaptors downstairs, and I can simply use one of them.

I can easily get my sister to put together a PCB once I have the circuit diagrams done. Once the PCB is put together, I can just use a hot air solder gun to get everything on permanently (except for the LED bredboard)

---

### Post by drdos2006 on 2012-04-22
If you need to wait for the Raspberry then you can still control the Atmel LEDs with your PC's serial port.

regards

---

### Post by Bandit on 2012-04-22
> **sandyd said:**
> Ive been thinking of pulling....... (except for the LED bredboard)

True that.. :-k

I am planning on doing a similar project sometime this fall if we buy or build a house. Going all home automation. Hopefully.. 
That will be something I will document and post here. :)

---

### Post by F.G. on 2012-04-22
pyserial is a nice and easy way to program serial port control. i did a major project (promiscuously scanning rfid cards for security testing) using it. you can also use pyqt4 for a GUI if you want (really depends on if you want control to be from a computer with a screen or not). 

anyhow, it should be fun. good luck.

---

