---
title: "Counter Strike Source hard locks system"
date: 2009-04-03
forum: Wine
---

### Post by Private_Ops on 2009-04-03
I'm running a fresh install of Ubuntu 8.10.

I downloaded wine off the repositories (which is odd cause I usually compile the latest).

I got Steam up and running and downloaded CSS.

I run it in a virtual desktop. It plays fine, FPS is good, but after a random amount of time my entire system will just flat out hard lock.

I'm running wine version 1.0.1. I also am using an ATI 4830 with fglrx. Not sure of the version to be honest, I used the restricted drivers installer. How can I check this? CS:S is also running in DX8.1.


Has anyone else encountered this problem? Is there a fix?

---

### Post by NightMKoder on 2009-04-04
By hard lock I assume you mean input stops responding. This is most likely a kernel panic (you might see your keyboard leds flashings). It's a fault of the ATI driver (wine can't cause this). Try updating/reconfiguring the fglrx driver itself. You can also try installing the latest drivers from ati: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Private_Ops on 2009-04-04
> **NightMKoder said:**
> By hard lock I assume you mean input stops responding. This is most likely a kernel panic (you might see your keyboard leds flashings). It's a fault of the ATI driver (wine can't cause this). Try updating/reconfiguring the fglrx driver itself. You can also try installing the latest drivers from ati: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Oddly, the LEDs on my keyboard do not flash, but the system DOES stop responding to any input at all.

---

### Post by binbash on 2009-04-04
wine can not cause hard locks.It may be a kernel lock up, ati driver fault or something with screensaver.

---

### Post by Private_Ops on 2009-04-04
> **binbash said:**
> wine can not cause hard locks.It may be a kernel lock up, ati driver fault or something with screensaver.

Screen Saver? Care to explain? It never kicks on when I'm playing.

---

### Post by asdfoo on 2009-04-04
> **Private_Ops said:**
> Screen Saver? Care to explain? It never kicks on when I'm playing.

More than likely it's because you unfortunately have an ATI card and drivers, which are of much lower quality on Linux.  ATI do try to fix these problems but it's a slow process taking years for them to get anywhere, causing grief to a lot of users.

If you have the option, buy a nvidia card, I think I saw a geforce 9800GT for $99 on newegg, you will find the situation to be much better.  I think I have played CSS, and many other games for atleast two years and never had a hard lock.  They have worked very hard for many years to provide a good quality product on both Linux and Windows.

---

### Post by Private_Ops on 2009-04-05
> **asdfoo said:**
> More than likely it's because you unfortunately have an ATI card and drivers, which are of much lower quality on Linux.  ATI do try to fix these problems but it's a slow process taking years for them to get anywhere, causing grief to a lot of users.

If you have the option, buy a nvidia card, I think I saw a geforce 9800GT for $99 on newegg, you will find the situation to be much better.  I think I have played CSS, and many other games for atleast two years and never had a hard lock.  They have worked very hard for many years to provide a good quality product on both Linux and Windows.



I want to go Nvidia, I like ATI, but the drivers is a bit of an issue. I can't even use compiz without things messing up.

My old 8500GT did pretty well running CSS under wine.

I want to do a new build but, money is tight and my priorities are on my BlaZeR2 (ZR2 Blazer) since my computer is working fine. I may have to switch back to the 8500, not sure if I will though.

---

### Post by asdfoo on 2009-04-06
> **Private_Ops said:**
> I want to go Nvidia, I like ATI, but the drivers is a bit of an issue. I can't even use compiz without things messing up.

My old 8500GT did pretty well running CSS under wine.

I want to do a new build but, money is tight and my priorities are on my BlaZeR2 (ZR2 Blazer) since my computer is working fine. I may have to switch back to the 8500, not sure if I will though.

prices are dropping on the nvidia 9xxx series, so keep an eye out for a good deal

---

