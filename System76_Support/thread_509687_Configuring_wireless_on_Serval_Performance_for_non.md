---
title: "Configuring wireless on Serval Performance for non-WEP encrypted wireless connection?"
date: 2007-07-25
forum: System76 Support
---

### Post by toddpedlar on 2007-07-25
This is perhaps a silly question - but on my new Serval Performance (just arrived today -
looks quite awesome)  when I try to set up the wireless for connection to our college-wide wireless network, 
I don't have an option for Open access (i.e. no WEP encryption) when I use the
Network Administration GUI thing.

Is there a simple way to configure the card for open, non-WEP access?

Thanks,

Todd

---

### Post by thomasaaron on 2007-07-26
First of all, if you are trying to configure you wireless via...
System > Administration > Networking
...that's not really the preferred way. If you've done that, you should probably follow these instructions...

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

Just left-click the icon and select your network.

---

### Post by toddpedlar on 2007-07-26
> **thomasaaron said:**
> First of all, if you are trying to configure you wireless via...
System > Administration > Networking
...that's not really the preferred way. If you've done that, you should probably follow these instructions...

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

Just left-click the icon and select your network.

That's what I've been doing all along... but while "Wired Network" happily comes up, "Wireless Network" doesn't ever appear.   I've never actually done the "System > Administration > Network" thing.

I'll try the (what seems draconian) reset above, and see what happens.  

Todd

---

### Post by toddpedlar on 2007-07-26
Okay, Tom - draconian worked.  Don't know what happened to cause things to fail, since all I ever tried to do was use the Network Manager GUI.  It works happily now, and I've switched from wired to wireless a few times with no hitches.

Thanks,

Todd

ps - you were right... I really do like the look of the new Serval (and the great battery life of the new 9-cell battery!)

---

