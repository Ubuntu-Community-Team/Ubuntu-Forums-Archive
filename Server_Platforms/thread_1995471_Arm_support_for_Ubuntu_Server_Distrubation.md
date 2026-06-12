---
title: "Arm support for Ubuntu Server Distrubation"
date: 2012-06-03
forum: Server Platforms
---

### Post by ads2996 on 2012-06-03
Hi

I am considering running a home server from the model b version of the raspberry pi. I was looking to find if there is ubuntu server arm support. I am already running a server off an atx tower pc. Though this works fine i am trying to find a cheaper solution.

Thanks in Advance

---

### Post by Gyokuro on 2012-06-03
Hi

Ubuntu will not work on this devices due to a different supported arm architecture - Debian works and it's mentioned on their site ([http://www.raspberrypi.org/downloads](http://www.raspberrypi.org/downloads)).

---

### Post by Cheesemill on 2012-06-03
Ubuntu announced it was dropping support for ARM v6 (the version Raspberry Pi uses) in 2010 with the release of Lucid (10.04).

Ubuntu now only has an ARM port for v7 and higher processors so in other  words no, Ubuntu won't be available for the Raspberry Pi.

As others have mentioned you should go with Debian instead as it uses  the same package format and package management tools (.deb and apt-get)  so you should feel right at home.

---

### Post by ads2996 on 2012-06-05
Does Debian support xbmc. As after reconsidering my plans the raspberry pi might not be able to cope with what i want it to do. So a solution was to use the raspberry PIs as recieving boxes for my tv downstairs and other ones could be connected to speakers and they would act like a cheaper alternative to a sonos system.

---

### Post by spynappels on 2012-06-05
If you want XBMC, there is currently a dedicated image being developed with a chopped down Linux OS and the XBMC interface. can't remember the details at the moment, but a quick google should find them.

---

### Post by Groodles on 2012-06-05
> **ads2996 said:**
> Does Debian support xbmc. As after reconsidering my plans the raspberry pi might not be able to cope with what i want it to do. So a solution was to use the raspberry PIs as recieving boxes for my tv downstairs and other ones could be connected to speakers and they would act like a cheaper alternative to a sonos system.

[http://wiki.xbmc.org/index.php?title=Installing_XBMC_for_Linux#Debian](http://wiki.xbmc.org/index.php?title=Installing_XBMC_for_Linux#Debian)

:)

---

### Post by Cheesemill on 2012-06-05
> **spynappels said:**
> If you want XBMC, there is currently a dedicated image being developed with a chopped down Linux OS and the XBMC interface. can't remember the details at the moment, but a quick google should find them.

You're thinking of OpenELEC.

[http://openelec.tv/](http://openelec.tv/)
[http://www.raspberrypi.org/phpBB3/viewtopic.php?f=35&t=5163](http://www.raspberrypi.org/phpBB3/viewtopic.php?f=35&t=5163)

---

### Post by ads2996 on 2012-06-05
I think OpenELEC will do what I am looking for. All I have to do now is wait for the PIs to come back into stock and wire my house up with cat5e or cat6 haven't decided yet.

---

### Post by Cheesemill on 2012-06-05
If you still haven't registered interest in a Raspberry Pi then I'd do so now, it's going to be a while before they're available on the open market and registering gets you a place in the queue.

---

### Post by ads2996 on 2012-06-05
Thanks i'll do that.

---

### Post by spynappels on 2012-06-05
Should get mine next week, ordered and paid for. Can't wait....

---

