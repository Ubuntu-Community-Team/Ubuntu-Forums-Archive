---
title: "Wireless in Pangolin"
date: 2008-11-05
forum: System76 Support
---

### Post by Guille Damke on 2008-11-05
Hello,

I just unpacked my new Pangolin Performance. I have tried to connect it to wireless with no success. Even my network icon has disappeared from the system tray (I restored it with ```
nm-applet --sm-disable
```   but this one does not show the available networks. (At the beginning they appeared, but I could not be connected anyway).

Why do I see a "wlan0" and a "wlan0:avahi" when I type "ifconfig".

I also installed a Network Monitor in the panel, and when I select wlan0 and click on "configure" I get a message "The interface does not exist". It does the same if I type "wlan0-avahi".

If it helps, I am trying to connect to a open network (no encrypted), even entering the essid it does not connect. I had to post this message from another PC.

Any help is appreciated.
Guille.

---

### Post by thomasaaron on 2008-11-05
Try this:

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

### Post by Guille Damke on 2008-11-06
Hi,
I tried it and it work perfectly, the available wireless networks are listed again, and I could connect wthout any problem. 

Thanks thomasaaron! for your help, all of the good comments that I read about about the system76 support was one of the reasons that pushed me for going for this laptop!

Guille.

---

