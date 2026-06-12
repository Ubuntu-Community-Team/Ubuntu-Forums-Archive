---
title: "Serval 1 wireless encryption does not work"
date: 2008-06-20
forum: System76 Support
---

### Post by icewater on 2008-06-20
I have a Serval 1 using the ilw3945 network driver.  I haven't been able to establish an encrypted connection to my WAP in a couple/few months now, when the ilw3945 driver replaced the ipw3945.

Is this a known issue?  Any idea when a solution will be available?

Thanks.

---

### Post by thomasaaron on 2008-06-20
Hi.

1. What Ubuntu version are you using?
2. Make sure the wireless switch is on (it's on the leading edge of your computer, on the left side -- toggle it to the left for the SerP1).
3. Follow the instructions below and reboot your computer...

To fix your /etc/network/interfaces file, go to a terminal
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

---

