---
title: "Mp3 mixing software"
date: 2009-10-05
forum: Ubuntu Studio
---

### Post by Glyndog on 2009-10-05
Hi I have been using Ubuntu for about 6 months now and thinks its great and this forums has helped me many times in the past with problems but now i have another problem and can not find any solutions!

Basically I am trying to plug an external mp3 mixer (bit of hardware) into my laptop and use software called Numark Cue LE.

Basically the mixer is called "icue musix mixing station" and the software is "Numark Cue LE."

Its windows software and I used wine to install it but when I open the software it cannot detect the hardware...


Does anyone have any ideas, am not really expected to be able to get this working but I would be very impressed and grateful for any advice.

Thanks! :confused:

---

### Post by raboofje on 2009-10-06
How is the hardware connected to your machine? USB? Firewire? Parallel port?

Either wine or some other virtualization solution (such as VirtualBox) might be able to 'tunnel' the connection.

---

### Post by Stochastic on 2009-10-06
I'd say you should try installing mixxx, it's a free digital DJ program that has support for a lot of external controllers.  It's likely easier to setup than a wine-based program.

---

### Post by Glyndog on 2009-10-07
Thanks for replies, its connected USB, I actually cant try any of your solutions due the adapter for my battery suddenly not working but will let you know asap if it works :)

---

### Post by Stochastic on 2009-10-09
Once you're back up and running, if you're still not able to get things to work, try posting the output of ```
lsusb
``` to help us troubleshoot.

---

### Post by Glyndog on 2009-11-11
hi sorry for late reply it took me a while to get up and running..

i installed mixxx and it doesnt seem to support this controller the output for lsusb is :

Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 15e4:0110  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by AutoStatic on 2009-11-11
It's not being recognized. Could not find anything about using the device with GNU/Linux either. So hopefully someone who likes the device enough and knows how to write C writes a driver for it. Just like the [Mixman DM2]("http://www.youtube.com/watch?v=e7tonj6_Oik").
Or maybe I didn't search good enough.

---

### Post by Glyndog on 2009-11-16
I had a feeling it would need a driver and i doubt anyone has wrote one.

Just wondering to do you reckon I could use it via VirtualBox OSE or something similar as I really dont want to dual boot with windows.

---

### Post by AutoStatic on 2009-11-16
> **Glyndog said:**
> Bus 005 Device 002: ID 15e4:0110
This is the ION device BTW, but didn't find anything on that either.
No idea if Virtualbox will work for you, I don't use that kind of software at home.

---

