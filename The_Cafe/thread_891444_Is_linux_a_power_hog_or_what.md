---
title: "Is linux a power hog or what?"
date: 2008-08-16
forum: The Cafe
---

### Post by Warpnow on 2008-08-16
I've been shopping around for a laptop, and it semes most laptops become less energy efficient when you put Ubuntu on them from reviews. This lead me to think...is linux just not energy efficient?

I mean I REALLY want to buy this Thinkpad T61, but according to some reviews I'd take a 30% loss in battery life...

And now I'm wondering, how much is it costing me a month to run Ubuntu on my desktop in extra power?

Hrm.

---

### Post by TheSlipstream on 2008-08-16
Actually, it's because they're made for Windows, and Ubuntu can not use many of the components with the same efficiency.

---

### Post by cocopuffz on 2008-08-16
I'm not sure, but from my limited experience it's pretty hit & miss. My Ubuntu box runs cooler than my XP. It's a dual boot... maybe the software is reporting differently. I'm not sure. I installed a temp sensors/fan controller and it is cooler in Ubuntu.

I have Mint installed on an OLD Dell, and that works fine. I installed the same version of Mint on a NEW dell and the fan runs constantly and it is much hotter the touch than when it's running XP (dualboot).

I gather it must be the different hardware support. The old dell has an external wifi card, while the new one has an internal etc... 

It would be interesting to see some real test results in a "green machine" comparison.

---

### Post by Obi-Wan Jerkobi on 2008-08-16
Yes, computers that come with Windows are built for Windows. That's why there's some level of loss when installing linux on it because it operates the hardware in different ways than windows. (i.e. Why you don't ever have to defrag in linux.)

It's just like how a 512MB 2GHz G5 can run leopard perfectly well with no snazzy video card or anything, but yet no lag or crippled experience. :)

---

### Post by FuturePilot on 2008-08-16
My old laptop which has a pretty old battery and it's pretty much dead because it can't hold a charge for very long actually gets a good hour to an hour and a half under Ubuntu. Under Windows it gets about 20 minutes :shock:

---

### Post by PryGuy on 2008-08-16
Yeah, I think it generally depends on hardware and/or drivers. My notebook runs good under ubuntu. Haven't made serious comparisons but it works about the same time as in Windows.

---

### Post by Nepherte on 2008-08-16
Using vor's tutorial [HOWTO: Improve battery life on a laptop]("http://http://ubuntuforums.org/showthread.php?t=729644&highlight=power+saving"), I managed to squeeze out an extra hour out of my Sony battery, resulting in 4 hours. In vista it is still 5 hours, but I can live with 4 hours.

---

### Post by stmiller on 2008-08-16
For most, Linux is generally a tad bit better for power than Windows. There were a few big studies with Redhat vs. Windows and power consumption recently. Linux used far less power on identical hardware as Linux. (That was servers, though.)

For laptops the thing that drains the battery the most is wifi and the screen. Just turning down your screen brightness will save quite a bit of battery power. You can also fine tune your hard drive with Linux if you are picky (program is: hdparm).

---

### Post by toupeiro on 2008-08-16
> **stmiller said:**
> For most, Linux is generally a tad bit better for power than Windows. There were a few big studies with Redhat vs. Windows and power consumption recently. Linux used far less power on identical hardware as Linux. (That was servers, though.)

For laptops the thing that drains the battery the most is wifi and the screen. Just turning down your screen brightness will save quite a bit of battery power. You can also fine tune your hard drive with Linux if you are picky (program is: hdparm).

+1.  Screens are pretty much the number 1 killer of your battery life.  I love my HP 8710w, but the one complaint I have about it is the battery life.

---

### Post by ssam on 2008-08-16
i think there is quite a big variation. If you have a component whose linux driver does not support powersaving, then that one component could reduce battery life quite a lot. If you have linux friendly hardware, then you can get better battery life than windows.

an extreme example is the OLPC laptop was designed to run linux. it has many clever powersaving tricks, for example switching everything off (apart from the display) when the machine is idle for a moment, and switching it back on as soon as you press a key. using the webcam to monitor ambient light levels, and adjusting the display brightness.

also a lot of work has been done by intel to monitor and reduce linux power usage. look up powertop

---

### Post by ghindo on 2008-08-16
In general, the newer the hardware, the poorer the Linux support is.  Meaning Linux will run less efficiently.  Old hardware, however...

---

### Post by FuturePilot on 2008-08-16
> **ghindo said:**
> In general, the newer the hardware, the poorer the Linux support is.  Meaning Linux will run less efficiently.  Old hardware, however...

I'd have to disagree with that. My new laptop gets great battery life under Ubuntu.

---

### Post by Canis familiaris on 2008-08-16
I would recommend this command:
```
sudo dpkg-reconfigure gnome-applets
```
and choose Yes to give root access to the CPU Frequency Scaling Monitor and you could now choose Powersave profile to save power in Laptops.

---

