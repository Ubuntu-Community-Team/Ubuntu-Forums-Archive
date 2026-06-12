---
title: "Lost connection to home wireless network"
date: 2012-11-21
forum: Ubuntu Development Version
---

### Post by epikvision on 2012-11-21
I recently installed 13.04 on my development laptop, and it connected to my home network right off the box. I've been using it for a few days now, but just today, it doesn't recognize my home network anymore. All other wireless networks are recognized but my home's.

How can I fix this? Thanks.

---

### Post by grahammechanical on 2012-11-22
Hi epikvision

In regards to making a wireless connection to a wireless access point (router) Ubuntu has not changed. It is the same for 11.10, 12.04, 12.10 and 13.04. In fact 13.04 is still very much based upon 12.10.  We have to follow the same diagnostic paths as for any version of Ubuntu.

What have you done to identify the problem?  what does this tell you?

> All other wireless networks are recognizedThat tells me that Ubuntu has recognised your wireless card/adapter and has installed a module/driver for it.  In fact this is the proof:

>  it connected to my home network right off the boxWhat does this tell you?

> just today, it doesn't recognize my home network anymoreWhat changed?

Since 12.04 we can go into System Settings and open a Network utility and move a slider to switch off wireless networking. We can also switch On and Off  Airplane Mode. I do not know what this does because I have never moved the switch to On.

These are simple things that we can check. It is also a way of getting information that can help you fix what is wrong.

As you are using a development version of Ubuntu and are having this problem this guide will help you.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Regards.

---

### Post by ronacc on 2012-11-22
sometimes all that is necessary to get the connection working is to click on the network indicator in the top bar and disable wireless and then renable it .

---

### Post by epikvision on 2012-11-22
I tried all that, but in the end, the source of the problem was my malfunctioning router.  I solved the issue by plugging out then plugging in the router again.  Now I'm happy. 

Sorry about bringing up this trivial issue.:)

---

