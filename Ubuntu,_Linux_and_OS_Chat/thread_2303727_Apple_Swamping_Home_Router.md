---
title: "Apple Swamping Home Router"
date: 2015-11-21
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2015-11-21
Running 14.04 on two machines.   I have two desktops, two laptops and a tablet each with their own dedicated ip address and all work fine.  However, I have noted that over the last two years when my family (sons) stay with us I have great difficultly with my internet access - it is either snail pace (when it is good I only have 2MBit!) or just non functional.  The Apple users also complain about connectivity.  I have experienced occasions when all the Apple devices are OK but when 'my' devices try to connect I have problems - it is almost as if the Apple devices have taken over.  On one occasion I changed my desktop machine (and rebooted) to 'auto search' for an IP address rather than have a dedicated link (to avoid any contesting) but I still had trouble when all the Apple devices had connections.  This is nothing to do with Ubuntu as such and I have not found anything in the net.   Has any body experienced anything similar (mixing Apple devices with other systems net wise)?

---

### Post by coldraven on 2015-11-21
I might be wrong about this so you might want to check elsewhere. My router can do B,G and N wifi protocols. My laptop can do B or G but my phone can do N (the fastest).
My theory is that if the phone connects first then the router will go into N mode and my laptop will not be able to connect. I have set my router to only connect in B+G mode as a way to stop this happening. Hopefully someone with better network knowledge will enlighten us :)

---

### Post by tgalati4 on 2015-11-21
Yes, the N-mode can use "wide" channels that will both knockout other devices and will suck up all of your bandwidth.  Use Wifi Analyzer on an Android Phone and examine your spectrum in both 2.4 and 5 GHz.

If you set the b+g mode on the router, then the Apple users will complain.  An alternative, and this is by Apple's design, is to buy more hardware, such as an Apple AirPort Extreme and extend your network, such that your old router will handle the G traffic and the AirPort will handle the A, N traffic.  Then set up Quality of Service (QoS) rules that will keep things moving when the Apple folks come for dinner.

Understand that Apple Users are consumers and that includes bandwidth.  2 Mbits/sec is not nearly enough to feed their appetite.

---

