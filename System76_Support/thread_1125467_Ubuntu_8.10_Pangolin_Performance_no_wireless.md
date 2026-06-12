---
title: "Ubuntu 8.10 Pangolin Performance no wireless"
date: 2009-04-14
forum: System76 Support
---

### Post by speedkreature on 2009-04-14
I've had my Pangolin for a couple weeks now. LOVE IT!  I've only got two gripes with it, one is more my OCD tendencies than anything (keyboard bows at the top middle) the other is actually a problem....I have no wireless.

I installed the kubuntu-desktop package a couple days ago as I really like the interface of KDE4 and feel that KDE apps have a better UI than most Gnome apps so I've spent some time logged in to a KDE session over the last couple days.  Overall a good experience.  Then I went to suspend the computer and it froze.  I gave it about 5 minutes but it never recovered so I held down the power button and turned it off.  When I rebooted, knetwork manager refused to start and when I started it manually, it didn't detect any wireless networks (I live in an appartment and there are MANY wireless networks).  I logged out and booted into Ubuntu and network manager started, but still no wireless...

So, I backed up all my data, reinstalled Ubuntu 8.10 (with the same 3 partitions that were default), installed the System76 driver (2.3.1) and STILL no wireless.

I'm at a loss...

---

### Post by thomasaaron on 2009-04-14
We dont' support kubuntu, but some 76ers who use it may be able to help.

However, you should have wireless in Ubuntu. Follow these instructions and see if it helps...

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

If that doesn't work, boot from a live Ubuntu CD and see if you have wireless. If you do, you have a configuration problem. If you do not, it is a hardware problem.

---

### Post by speedkreature on 2009-04-15
> **thomasaaron said:**
> We dont' support kubuntu, but some 76ers who use it may be able to help.

However, you should have wireless in Ubuntu. Follow these instructions and see if it helps...

  

If that doesn't work, boot from a live Ubuntu CD and see if you have wireless. If you do, you have a configuration problem. If you do not, it is a hardware problem.

"auto lo" and "iface lo inet loopback" were the only two lines in the interfaces config file.  As stated above, this is a new installation.  Restarted with an 8.10 LiveCD and still no luck.  :-(

I noticed there is an antennea icon on the F11 key...is it possible the device has simply been disabled?

---

### Post by Guille Damke on 2009-04-15
Hi,
In the pangolin panp4n, you enable/disable the wireless by hitting Fn+F11 (The 3rd LED from left to right turns on/off in green). If you have Bluetooth, then Fn+F12 makes it, and it is indicated by the same LED, which lights yellow too. If both are activated, then the final color is Green+Yellow.

---

### Post by speedkreature on 2009-04-15
Looks like my wireless was somehow disabled.  I'd tried pushing Fn+F11 several times (with a few seconds in between) with no luck.  Tried it just now and held both down for a few seconds and now everything is back to normal!  :p

---

### Post by formol on 2009-04-16
try to put the default option in the bios.  i disabled my wifi once by plugin a wifi dongle + ndiswrapper on my pangolin...

---

