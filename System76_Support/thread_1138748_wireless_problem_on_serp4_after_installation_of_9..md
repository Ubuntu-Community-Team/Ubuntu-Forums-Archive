---
title: "wireless problem on serp4 after installation of 9.04"
date: 2009-04-26
forum: System76 Support
---

### Post by Viranh on 2009-04-26
My wireless card stops transmitting every 5 minutes or so, and more often the more I use it. It still shows that it is connected, but I can't access web pages or download anything and have to disconnect and reconnect. It's very frustrating since I do not have a wired connection at my apartment. I will probably just reinstall intrepid, but I would like to be able to upgrade at some point, and I won't be able to until this is fixed. Wireless card is the intel pro/wireless 4965 a/g/n.

---

### Post by thomasaaron on 2009-04-27
Did you upgrade to Jaunty or do a fresh install?

Try running Jaunty from a live CD. See how the wireless card works there. It sounds like a configuration issue.

---

### Post by Viranh on 2009-04-27
It was a fresh install. I ran the live cd first, and it seemed to be working, but I didn't attempt to download anything large. This problem becomes much more obvious when I try to download an update or program with apt. I'm back to using intrepid for now, but a jaunty install amazingly takes only about 20 minutes if you have suggestions.

I'll try the live cd again and try to download something and see what happens.

---

### Post by shomaster on 2009-04-29
I too, seem to be experiencing this problem after an upgrade to Jaunty on my serp4.

---

### Post by thomasaaron on 2009-04-30
Did you try your wireless from a live CD?

ALSO, follow these instructions and see if it fixes the problem...
> 
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

### Post by cnsnyldz on 2009-05-01
I have exactly the same problem at my Acer 5584 WXMI. The wireless seems to restart itself every 10 minute or so. I both tried it with update & fresh install. No change. At ubuntu 8.10, I had no problem.

---

