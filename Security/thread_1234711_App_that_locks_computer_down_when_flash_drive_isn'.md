---
title: "App that locks computer down when flash drive isn't present?"
date: 2009-08-08
forum: Security
---

### Post by billdotson on 2009-08-08
There is a program called Predator for Windows that makes it so your keyboard, mouse and monitor do not work unless a certain flash drive is inserted in the computer. Is there anything like that in Linux? Would there be any possible issues with a program like that, such as it not recognizing the drive for some reason?

I would assume the code for a program like that would read the hardware identifier (what is that, a hexadecimal number?) or either put an encryption key on the flash drive and then tell the operating system to turn off the mouse, keyboard and monitor support unless it is present. Does that sound reasonable or am I just blathering on?

---

### Post by The Tronyx on 2009-08-08
Couldn't you just have some kind of cron job run every minute?  Like, have it do a lspci or lsusb and if the USB doesn't show up, then it shuts the box down or explodes or similar.  If the hardware identifier is found, it does nothing.

---

### Post by jamie1985 on 2009-08-09
How about generate a public/private key pair, put one on the flash drive and store one somewhere on the machine, then write a bit of code that checks the key pairs?

I'm fairly sure you could write something that detects the device being removed/inserted if you wanted to. My hungover mind is telling me there will probably be an interrupt of some sort when a usb pen is inserted/removed, though I could be way off the mark with that. 

Or write a cron job (as already suggested) to run your script every so often.

I'm suggesting a key-pair as you could authorize as many flash drives as you want, heck you could have multiple key-pairs and revoke them if you ever misplace a drive. 

I hope that makes some sort of sense.

J

---

### Post by kevdog on 2009-08-09
I remember something in the Ubuntu wiki that mentioned booting with a USB key that kept a key on it.  I dont remember the page however.

---

### Post by billdotson on 2009-08-11
Hmm, the key thing (RSA keys maybe?) would be a good idea. Now I would just have to learn how to actually code more than print statements and simple while loops in python 2.4...

---

### Post by Dave_Connor on 2009-08-11
You can get into BASH scripting with creating variables detailed to 'lsusb | grep drive' and that should be atleast enough for your system :)

---

