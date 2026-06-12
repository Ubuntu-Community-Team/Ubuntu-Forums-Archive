---
title: "Terratec DMX 6fire USB?"
date: 2008-10-02
forum: Ubuntu Studio
---

### Post by ax-ax on 2008-10-02
I have a DMX 6fire USB (that works in windows) but I really don't understand how to get it to work in linux. 

Lsusb shows:
Bus 005 Device 002: ID 0ccd:0080 TerraTec Electronic GmbH 

And Envy24control doesn't find it.

To be honest, I don't know anything about soundsystems on linux, and this seems to complicated to solve just by luck. So, does anybody else have any experience or knowledge about this?

Help would really be appreciated ;)

---

### Post by ax-ax on 2008-12-19
Seriously, I don't get how I'm supposed to get the damn card to work. It works alright in windows, is detected by lsusb but no matter what I do, I can't get it to work. 

To make this even more annoying, does windows bluescreen every time I boot it (cause it doesn't like my internal soundcard's game port), so I have to shutdown, open the computer, screw like a hundred screws and remove the soundcard manually to be able to use my DMX, while others is discussing how to get 5.1 sound, different order of the soundcards etcetera. 

I must confess that I am slightly annoyed.

(this is maybe wrong category for this thread, could someone move it?)

---

### Post by togo59 on 2008-12-21
> **ax-ax said:**
> Seriously, I don't get how I'm supposed to get the damn card to work. It works alright in windows, is detected by lsusb but no matter what I do, I can't get it to work. 

To make this even more annoying, does windows bluescreen every time I boot it (cause it doesn't like my internal soundcard's game port), so I have to shutdown, open the computer, screw like a hundred screws and remove the soundcard manually to be able to use my DMX, while others is discussing how to get 5.1 sound, different order of the soundcards etcetera. 

I must confess that I am slightly annoyed.

(this is maybe wrong category for this thread, could someone move it?)
Bump.

With intrepid I got the start-up sound but nothing after log in.

Same now I have ubuntustudio. Beeps at login screen. Not a squeak thereafter.

I have Terratec DMX 6Fire PCI card (not USB).

---

### Post by ax-ax on 2008-12-21
I found out that the usb doesn't work with standard alsa modules. Next question: is it possible to get it to work at all?

---

### Post by 8086 on 2009-01-10
Sorry, but this card has a proprietary driver model, and does not comply with the USB Audio standard (which would be supported by Alsa). So unfortunately you are, just like me, stuck to using it in Windows. Blows *big time*

---

### Post by markbuntu on 2009-01-11
You guys should let Terra Tec know about this and maybe suggest that they either contact alsa.org and talk to the driver writers or write a driver themselves for linux.

You should point out to them that over 10million people are now using linux and many of them are professional musicians who would like to take advantage of the really great hardware they make but are currently not able to due to their non-standard implementation of usb protocols.

These people are in the business of selling hardware. They will listen. Just be nice and encouraging. As current owners and users of this hardware, you will make an impact.

---

### Post by Stochastic on 2009-01-12
> **markbuntu said:**
> You guys should let Terra Tec know about this and maybe suggest that they either contact alsa.org and talk to the driver writers or write a driver themselves for linux.

You should point out to them that over 10million people are now using linux and many of them are professional musicians who would like to take advantage of the really great hardware they make but are currently not able to due to their non-standard implementation of usb protocols.

These people are in the business of selling hardware. They will listen. Just be nice and encouraging. As current owners and users of this hardware, you will make an impact.

I couldn't have said it better myself.  I'd just like to add that if they are belligerent or belittling towards Linux, a clear-headed mention of returning their product to the store may help to change their views.  But in general, try to be friendly and helpful, not forceful and angry.

---

### Post by giancarlo.melandri on 2010-01-07
hello... this is my first post in this forum . I was trying to discover if DMX 6fire could work with linux before buying it.

so .. I found this document...
[http://ftp.terratec.de/Documentation/Linux_and_Mac_OSX_Compatiblity.pdf](http://ftp.terratec.de/Documentation/Linux_and_Mac_OSX_Compatiblity.pdf)

... and I was hoping that the GNU-Application envy24control could be sufficient to make it work  ...
( I 've ubuntu 9.04 and envy24control is in alsa-tools-gui package ) 

Am I in a wrong way ? Can anyone try if envy24control works with DMX 6fire ?

Best Regads!
( .. sorry for my english .. it is not my first language... )

---

### Post by copyrightake on 2011-08-20
I discovered a working driver for the Terratec DMX 6fire USB! :D

[http://sourceforge.net/projects/sixfireusb/](http://sourceforge.net/projects/sixfireusb/)

You can compile the module or apparently the driver is available in the kernel 2.39 and up.

---

### Post by sgx on 2011-08-21
Maybe a new topic, (year included) about this would be good, and help future google searchers.
Cheers

---

