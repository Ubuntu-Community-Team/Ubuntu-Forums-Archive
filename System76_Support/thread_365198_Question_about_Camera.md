---
title: "Question about Camera"
date: 2007-02-19
forum: System76 Support
---

### Post by Cobra78 on 2007-02-19
Hi to Everyone

So....i don't have a System76 Notebook, because i live in Italy, anyway my notebook had a built-in web-cam that doesn't work with Linux.

So the question is:

what type of web-cam is on System76 Laptop? Is possible the Driver for yours web-cam work on mine (i have a [LEFT][COLOR=red][FONT=serif]**_Syntek_**[/FONT][/COLOR][/LEFT]
 cam)? In this case, can i obtain and install your driver without problems on my system?

Tanks for any answer :)

---

### Post by crichell on 2007-02-19
Run the command:

lsusb

We'll be able to determine if it is the same camera - if so we're happy to provide the driver.

---

### Post by Cobra78 on 2007-02-20
Here is my lsusb

```

Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 174f:a821  
Bus 001 Device 001: ID 0000:0000  

```

I think that the camera is " Bus 001 Device 003: ID 174f:a821  "

Very thanks

---

### Post by crichell on 2007-02-20
Lets update your USB id's - maybe we'll get a better definition than just the bus id.

```
sudo update-usbids 
```

then

```
lsusb
```

and post - hopefully we'll get better info.

---

### Post by Cobra78 on 2007-02-21
I update my usb id's, but no change  
in the outut of lsusb, i think thath my device is too new :/

I can only wait....

Anyway very thanks for your time ^^

---

### Post by crichell on 2007-02-22
You may want to check if it's on this guys list:

[http://mxhaard.free.fr/index.html](http://mxhaard.free.fr/index.html)

Michel did a great job developing our Gazelle Performance camera driver.

---

### Post by Cobra78 on 2007-02-23
Already tried gspca and other Cameras driver too, but with no luck :P

So the evidence is that for now there is no way to get my camera working, but is not really a problem :)

Very thnx for your time, and go on with SYstem76, i think is a great Idea, and i hope that in the future you will ship it in Italy too :D

---

### Post by sprtchk on 2007-04-24
Hello !

This is a Syntek STK-1135 webcam, I have the same one. There is an experimental driver here ([http://syntekdriver.sourceforge.net/index.php?mode=faq)](http://syntekdriver.sourceforge.net/index.php?mode=faq)). I tried to test it but for the moment when I load the driver and then run camorama, camorama freezes. I haven't had the time yet to see if the solution of my problem was already in their forum.

Sincerely

---

