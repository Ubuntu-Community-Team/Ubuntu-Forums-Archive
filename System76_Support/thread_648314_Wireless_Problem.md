---
title: "Wireless Problem"
date: 2007-12-23
forum: System76 Support
---

### Post by Skia_42 on 2007-12-23
Hello, I have a Dartar laptop I purchased a few months ago. I recently left for a week long trip and now my Wifi is not working. It worked before I left and I have the network name and wep key. When I connect to the network, I see the bars (80%) so I know it is connected. However, It is not connected to the internet. I tried the trouble shooting guide but it still does not work. Any ideas?

Edit: Ethernet is not working either, it shows up as connected but I can´t get any sites.

---

### Post by Skia_42 on 2007-12-23
I think I know what the problem is, but I do not know how to fix it. When I look at the interfaces with network-tools I see lo, eth0, eth1 and eth1:avahi. eth1:avahi has an ip address and other stuff assigned to it while eth1 does not. I do not know what avahi is, or how the extra interface got there. Anyone know how to fix this?

---

### Post by thomasaaron on 2007-12-24
Please specify which Darter you have. If you don't know, go to System > Admin > System76 Driver > About

If you have a white darter, make sure your wireless switch (top left, over the keyboard) is on.

In the meantime, try this::

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

