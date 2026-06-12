---
title: "Wireless on hardy with Pangolin panv3"
date: 2008-04-23
forum: System76 Support
---

### Post by kperkins on 2008-04-23
Interesting, but not a problem at this time.  
I do have wireless, but my wireless light is off(the one on the front of the laptop beside power, and battery lights), the switch is set to on, and Fn-F2 doesn't seem to do anything.


I'm using panv3 with dual core cpu, and hardy 64 bit.
Any ideas?

---

### Post by Squish on 2008-04-26
i think i have the same problem

According to my network manager, i am connected to my internet via wifi, but my light shows clearly I am not... as well I cannot connect to the internet.

if I downgrade kernels, I can use it... but I dont want to do that, as a whole slew of things is fuubarred.

This is kinda lame~ (I have the wireless G card found in the serval performance, purchased in november)

---

### Post by kperkins on 2008-04-26
Sounds like a different problem--I actually do have internet, but no wireless radio light, and Fn-F2 doesn't seem to turn it on or off.

---

### Post by ajesh on 2008-04-28
If wireless is working, but the wi-fi LED does not glow properly, then this thread probably has the answer:
[http://ubuntuforums.org/showthread.php?p=4775217#post4775217](http://ubuntuforums.org/showthread.php?p=4775217#post4775217)

It worked for me....

---

### Post by kperkins on 2008-05-01
> **ajesh said:**
> If wireless is working, but the wi-fi LED does not glow properly, then this thread probably has the answer:
[http://ubuntuforums.org/showthread.php?p=4775217#post4775217](http://ubuntuforums.org/showthread.php?p=4775217#post4775217)

It worked for me....
Thank you ajesh, I'll give it a try

---

### Post by thomasaaron on 2009-11-30
Squish, try this...

> To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

NOTE:
Unless you are dealing with static IP addresses (which is pretty rare for the
general end-user) you should NOT establish a network connection by going to
System > Administration > Network.

Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little
computer monitor).   

Kperkins, if that link didn't fix it, please file a bug report here. It may just be something we need to fix in the System76 Driver (which I assume you ran?). 

launchpad.net/system76

---

