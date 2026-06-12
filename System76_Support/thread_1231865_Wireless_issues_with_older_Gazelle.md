---
title: "Wireless issues with older Gazelle"
date: 2009-08-05
forum: System76 Support
---

### Post by indigoshift on 2009-08-05
My wife picked up a Gazelle back around 2007.  It's worked great, but with intermittent wireless issues.

She recently reinstalled 8.04, and patched it--I think there were 200-odd updates for it.

Now her wireless gets an IP address and my router sees the machine, but she can't actually do anything online--it claims there's no connection at all.  It's as if the laptop gets the connection, but has no idea what to do with it.  

I have no idea what's going on.

---

### Post by thomasaaron on 2009-08-05
Hi.

First, we add no patches for wireless on that machine. And second, our test machine in the shop works great. So, you're dealing with either a configuration issue, a bad wireless card, or a router/networking issue.

To check your configuration, do this...

>  To fix your /etc/network/interfaces file, go to a terminal
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

To verify whether or not you have a bad card, boot from a live Jaunty (9.04) CD. Wireless should work out of the box. NOTE: You configure wireless on Jaunty differently than you do on 8.04. In Jaunty, just click the network manager icon in the upper right corner of your screen and then select your access point.

You may also want to try resetting your router -- even if other computers work great with it. You'd be surprised how often that fixes wireless problems.

---

### Post by indigoshift on 2009-08-14
I honestly meant to respond to this sooner, but all sorts of Real Life got in the way.

Thanks for the response!  Looks like her machine will sometimes think it should use the loopback instead of her wireless connection.

It's working now, but we're going to follow the instructions you've recommended.

I'm glad you pointed out the "no patches for wireless"--I spent awhile trying to figure out if that were the case.

Thanks again!  She loves that laptop to death.  You guys do great work.

---

