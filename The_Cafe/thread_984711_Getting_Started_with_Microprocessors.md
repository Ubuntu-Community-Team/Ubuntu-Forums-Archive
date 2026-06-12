---
title: "Getting Started with Microprocessors"
date: 2008-11-16
forum: The Cafe
---

### Post by lucasl on 2008-11-16
Hi!
I want to try programming microprocessors for no particular reason. I did a search, but nothing that helpful came up, as I know absolutely nothing about it except for some basic electronics, soldering and programming (C) experience.
I have no idea about which to buy and programmers and compilers and breadboards and all that.
Could somebody help me out? Cheap components would be nice.:D

Thanks!

---

### Post by pbpersson on 2008-11-16
More information would be helpful.

What are your input devices?  What are your output devices?

As I recall, the earliest computers were a bunch of lights and switches on a panel.  People used the switches to load values into registers.  Then you could load a small program to read the value from register A, add it to register B, and display the results on a row of lights.

11011111 + 1010000101 = 1101100100

If you spent weeks of your life building a computer to add two numbers together successfully, would that be a good thing?  Is that your goal?

In 1978 this was considered really high tech when the first hobbyists built their home computers.

---

### Post by lucasl on 2008-11-16
No devices as of yet. The sort of thing I was thinking was just a blinking LED or something, with maybe an advanced project being LED naughts and crosses or a electronic die or something, just simple things like that.

---

### Post by Warren Watts on 2008-11-16
If I were you, I would look into something like the Basic Stamp Microcontroller.  

From the Parallax website: ( [http://www.parallax.com/Default.aspx?tabid=295](http://www.parallax.com/Default.aspx?tabid=295) )

> What is the BASIC Stamp Microcontroller Module?

A BASIC Stamp is a single-board computer that runs the Parallax PBASIC language interpreter in its microcontroller. The developer's code is stored in an EEPROM, which can also be used for data storage. The PBASIC language has easy-to-use commands for basic I/O, like turning devices on or off, interfacing with sensors, etc. More advanced commands let the BASIC Stamp module interface with other integrated circuits, communicate with each other, and operate in networks. The BASIC Stamp microcontroller has prospered in hobby, lower-volume engineering projects and education due to ease of use and a wide support base of free application resources.

---

### Post by kevdog on 2008-11-17
The first microprocessor project I became involved with was known as the UIRT - Universal Infrared Remote Transmitter Project.  This device made it capable of controlling your computer with use of the Girder software.  It interfaced through the computer's serial port.  I built the whole thing from scratch and programmed it at the local college.

Sad part about it -- is that I can't even find the original homepage for the project any longer.

Another guy, known as John Rees -- very helpful -- troubleshooted the design for a while, but later made it interface through USB rather than through the serial connector.  Unlike the original UIRT design that was published, he never published how to construct or program the microprocessor for this device.  Its home can be found here:
[http://usbuirt.com/overview.htm](http://usbuirt.com/overview.htm)

I helped troubleshoot the early device -- version 1 or whatever it was back then.  You would have thought the guy would have sent me a few devices for free, but nope -- that didn't happen.

I haven't used the device now in years, now that Girder -- the software that interacts with the device -- went from being free -- to a pay product.  It was fun to tinker with, however IMO opinion not worth the $49 they are currently selling it for -- unless major improvements have been done with the interface.

What a freakin rip!!

---

### Post by mips on 2008-11-17
Try the PIC microcontroller. They are simple and cheap as chips. Lots of resources on the web.

[http://en.wikipedia.org/wiki/PIC_microcontroller](http://en.wikipedia.org/wiki/PIC_microcontroller)
[http://www.microchip.com/stellent/idcplg?IdcService=SS_GET_PAGE&nodeId=64](http://www.microchip.com/stellent/idcplg?IdcService=SS_GET_PAGE&nodeId=64)

Microchip has shipped over 6 billion of these little critters.

Also learn some assembly language, really fun.

---

### Post by kernelhaxor on 2008-11-17
> **mips said:**
> Try the PIC microcontroller. They are simple and cheap as chips. Lots of resources on the web.

[http://en.wikipedia.org/wiki/PIC_microcontroller](http://en.wikipedia.org/wiki/PIC_microcontroller)
[http://www.microchip.com/stellent/idcplg?IdcService=SS_GET_PAGE&nodeId=64](http://www.microchip.com/stellent/idcplg?IdcService=SS_GET_PAGE&nodeId=64)

Microchip has shipped over 6 billion of these little critters.

Also learn some assembly language, really fun.

That looks interesting .. do you have one of those? if u do, what do u use it for? wht did u program?

---

### Post by mips on 2008-11-17
> **kernelhaxor said:**
> That looks interesting .. do you have one of those? if u do, what do u use it for? wht did u program?

I still have a few chips lying around. I built my own programmer from schematics I got of the net which I loaned to a friend and never got back.

The PIC was just one of the microcontrollers I used while studying electronic engineering. 
After studying I made some money with them programming chips for a certain *cough* console, not going into that though.

All the programming I ever did on microproccessors/microcontrollers have been in their native Assembly language. Some of the PIC models also have C-compilers available but I would not even bother. Lol, I still remember my exams where we wrote the assembly code out on paper. most of my programming has been electronics related, interfacing to stuff etc I nearly started a neat project years back to design a wave/surge controller for marine aquarium powerheads, never happened though.

There are a gazillion uses out there for PIC and they also come in pretty diverse packages optimised for one application or the other.

Another worthy mention must go to the Atmel AVR ucontrollers. I have never used them but have heard good things about them. [http://en.wikipedia.org/wiki/Atmel_AVR](http://en.wikipedia.org/wiki/Atmel_AVR)

---

### Post by brawd on 2008-11-18
Being as I am coming up to retirement I was also thinking of pic microcontrollers as something to keep the grey matter ticking over. However I got into Ubuntu first and its kept me puzzled for the last few weeks. If there is one thing I've learnt whilst wrestling with Ubuntu it is that I will never go back to ms.

However when googling for 'pics for linux' I did come across this if its any help.

[http://linuxgazette.net/issue79/sebastian.html](http://linuxgazette.net/issue79/sebastian.html)

regards,

brawd

---

### Post by brawd on 2008-11-18
And I just thought you may also be interested in KiCad. You can get it via the download thingy in system.

brawd.

---

### Post by lucasl on 2008-11-18
After looking round I probably end up getting the [PICkit 2 starter kit]("http://www.microchipdirect.com/productsearch.aspx?Keywords=DV164120"), mainly because it comes with a demo board with 4 LEDs and a push button, as well as lessons and support from GPUtils.

---

### Post by gpsmikey on 2008-11-18
Definitely check out the PIC family of chips (Microchip).  All sorts of different versions available, easy to program, you can either do it in assembly or buy basic (stamp) or C compilers for them.  Require almost no support hardware.  I used one for a Cub Scout Pinewood derby track timer and everybody loved it.  The 16F870 was the one I used - cheap, built in A/D converter, MUX, UART for serial stuff and a number of discrete pins capable of driving LED's directly etc.  Check out Digikey for pricing and availability.  [http://www.digikey.com](http://www.digikey.com)  also Microchip for their data sheets and app notes [http://www.microchip.com](http://www.microchip.com).  Fun family of chips to build "gadgets" with !!

mikey

---

### Post by freebeer on 2008-11-18
Heh.  Kind of a co-incidence for me that the PIC and Atmel devices were mentioned in one thread (but maybe not - if they're that popular).  I helped develop two electronic devices for my business that uses them.  I didn't work on the code itself, but the design and performance criterion was my responsibility.  It's an interesting field, but alas, I have no time to delve into it.  :(

---

### Post by gpsmikey on 2008-11-18
> **freebeer said:**
> Heh.  Kind of a co-incidence for me that the PIC and Atmel devices were mentioned in one thread (but maybe not - if they're that popular).  I helped develop two electronic devices for my business that uses them.  I didn't work on the code itself, but the design and performance criterion was my responsibility.  It's an interesting field, but alas, I have no time to delve into it.  :(

My hot tub controller is based on my design with an AT2051 Atmel chip.  Both Atmel and Pic have fun chips, but the PIC series seems to be more all inclusive in covering everything from an electronic led flasher up to a pretty powerful chipset with some of the newer 18 series stuff (have not had a chance to play with them yet).  One thing worth checking out is another of my favorite magazines -- "Circuit Cellar" - definitely a hardware hackers magazine.  Then there is always "Nuts and Volts" although I only have a subscription to Circuit Cellar.  Lots of good support out there for the PIC chips - entire web sites and businesses devoted to them.  You can find them in all sorts of things !! Just to get you a bit excited, do a Google search on "embedded pic" - lots of fun things and books out there !!

mikey

---

### Post by mips on 2008-11-19
> **gpsmikey said:**
> One thing worth checking out is another of my favorite magazines -- "Circuit Cellar" - definitely a hardware hackers magazine.  Then there is always "Nuts and Volts" although I only have a subscription to Circuit Cellar.

Back in the day when I was still buying magazines I used to loved Elektor magazine.
[http://www.elektor.com/](http://www.elektor.com/)
[http://www.elektor.com/magazines.46742.lynkx](http://www.elektor.com/magazines.46742.lynkx) December 2008 Online edition
[http://www.elektor.com/magazines.46742.lynkx?filterGuid=6d5bd647-4ca0-491f-89c2-1a675d447ff4](http://www.elektor.com/magazines.46742.lynkx?filterGuid=6d5bd647-4ca0-491f-89c2-1a675d447ff4)  [COLOR=Red]Lots on Microcontrollers![/COLOR]

---

### Post by freebeer on 2008-11-19
Yeah, I believe my controller (thermostat) uses the 18 series chip :confused: More like embarrassed, since I should know it off the top of my head, as I have to select the chip type whenever I need to change the software on it.  *blush*

---

### Post by gpsmikey on 2008-11-19
I originally purchased the CCS compiler when I was first working with the PICS, however, it looks like there are a number of free C compilers out there now like this one [http://sdcc.sourceforge.net/](http://sdcc.sourceforge.net/) and there was a mention of one from Microchip as well.  When I retire (hopefully soon), I have a number of PIC projects I want to do.  Might also want to check out Eagle CAD - they have a free version as well as a full blown version and it runs under windows AND Linux. [http://www.cadsoft.de/](http://www.cadsoft.de/)

mikey

---

### Post by gogo2520 on 2009-03-08
Hello 
 I have a problem with hotplug. Its not in the etc directory, I have the libusb.1.04 package loaded but I don't know what eles to do. I am new to linux and could use some help.
                 Thank you for any information
                     gogo

---

### Post by Rocket2DMn on 2009-03-08
Please start a new thread for your problem.  Thank you.

---

