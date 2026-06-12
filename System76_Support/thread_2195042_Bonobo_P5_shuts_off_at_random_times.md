---
title: "Bonobo P5 shuts off at random times"
date: 2013-12-22
forum: System76 Support
---

### Post by chelmite2 on 2013-12-22
My system has been shutting off at random times, while I'm at the console.
There's a little "peep" sound, and then the power is off. There's no proper shutdown.
 I can power on to continue.
The power supply is plugged in and charging. I have the laptop on a hard lap-pad, and I'm sitting down at home.
(I.e., I'm stationary, not mobile, so it's not like I'm on the subway.)

I'm running ubuntu 13.10.
I'm also running a script to throttle the CPU if the temperature gets above 80C.
(Thunderbird has been going wild recently, but the shutdown that just happened was while Thunderbird was closed.)

Any ideas on how to track this down?

Thanks,
chelmite

---

### Post by monkeybrain20122 on 2013-12-22
The random shutting down is to protect the computer from overheating, so you have to figure out why it is running so hot.

---

### Post by matthekc2 on 2013-12-22
I found this temperature sensor guide for Ubuntu, the package shows as available for 13.10.  It shows temps and fan RPM's could be useful...

Guide
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

Package looks to be available.
[https://launchpad.net/ubuntu/+source/lm-sensors](https://launchpad.net/ubuntu/+source/lm-sensors)

---

### Post by chelmite2 on 2014-09-22
> **monkeybrain20122 said:**
> The random shutting down is to protect the computer from overheating, so you have to figure out why it is running so hot.

Thanks! I opened it up and found both fans blocked by lint!  I cleaned it up, and now it's running fine.:p

---

