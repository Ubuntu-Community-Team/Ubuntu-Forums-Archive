---
title: "Microcontroller IDEs for Linux"
date: 2011-03-21
forum: The Cafe
---

### Post by lz1dsb on 2011-03-21
I recently delved into the Arduino world and I'm so fascinated by the whole philosophy. I personaly like the fact that the IDE (although not that advanced) is supported on Win, Linux and Mac. Which I think is great. 
So I was thinking how many other microcontroller vendors out there are also embracing this philosophy: to provide IDEs for other operating systems other than Windows. 
I've been working with Microchip's PICs in the past and I've only heard on one local event from a product manager that they had been planning to release their IDE under Linux. Which haven't happened so far. And I've found in this forums that they have something like a beta release (MPLAB X or something like this) which is far far away from the IDE that they provide for Windows. 
Atmel - I haven't seen an IDE for Linux, although they have an avr-gcc package which the Arduino IDE uses. 
So does anybody with more experience than me has an inside on this? Do you know a microcontroller vendor which is more Linux friendly? From what I've found so far, Atmel seems to be much more friendlier as there's an avr gcc compiler which is free, compared to the almost $1000 that Microchips wants for their compiler.

---

### Post by An Sanct on 2011-03-21
Tried [this]("http://elettrolinux.com/Integrated-Development-Environment/side4linux-an-ide-for-atmel-avr-microprocessor.html")? It is and Atmel IDE.

Have you tried using wine with the ms IDEs??

---

### Post by lz1dsb on 2011-03-22
I haven't tried this. I read on the WINE forums that MPLAB shouldn't have any problems. Bot so far I haven't had the time to test it. I'm not sure if the USB programmer/debugger I have would work though. The last time I plugged in a USB stick while a WinXP virtual machine was working the whole system crashed. But since than I don't know why, but I didn't test it again...  
The link is quite interesting. Thank you.

Cheers, 
Boyan

---

### Post by An Sanct on 2011-03-23
Your welcome!

Its interesting for me too, so I thought I would share it.

Wine is not a virtual machine, I had problems with Virtualbox+USB stuff (mainly my blackberry), but never with wine+usb. Its worth a try.

---

### Post by lz1dsb on 2011-03-23
You're so right. Even though I've been using WINE for quite some time, I still mistake it with a virtual machine. I have to give it a shot though. I still have my ICD2 laying somewhere in the closet.

Cheers,
Boyan

---

