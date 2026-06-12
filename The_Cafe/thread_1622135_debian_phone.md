---
title: "debian phone"
date: 2010-11-15
forum: The Cafe
---

### Post by LunaticHiatus on 2010-11-15
If you took the arm port of debian and tried to install it on your android phone with the android kernel, couldn't you esentially have a full linux phone?

---

### Post by ssam on 2010-11-15
depends if you could get the specs to talk to all the components GSM, power management, GPS, etc.

if you priority is getting debian on a phone, then you might want to look at the openmoko
[http://wiki.openmoko.org/wiki/Debian](http://wiki.openmoko.org/wiki/Debian)

---

### Post by LunaticHiatus on 2010-11-15
> **ssam said:**
> depends if you could get the specs to talk to all the components GSM, power management, GPS, etc.

if you priority is getting debian on a phone, then you might want to look at the openmoko
[http://wiki.openmoko.org/wiki/Debian](http://wiki.openmoko.org/wiki/Debian)

Its cdma, but the componets talking to each other would be handled by the drivers and the linux kernel is monolithic so the drivers are located within the kernel.

---

### Post by slackthumbz on 2010-11-15
> **LunaticHiatus said:**
> Its cdma, but the componets talking to each other would be handled by the drivers and the linux kernel is monolithic so the drivers are located within the kernel.

Just get a phone with Maemo, that's pretty much a debian ARM build with a few extra drivers and a GSM stack.

---

### Post by LunaticHiatus on 2010-11-15
its the customization which interests me, also proof of concept. however, you make a good point. I would probably be more likely to find information about installing maemo on android phones over debian and I could just customize maemo from their.

---

### Post by ssam on 2010-11-15
> **LunaticHiatus said:**
> Its cdma, but the componets talking to each other would be handled by the drivers and the linux kernel is monolithic so the drivers are located within the kernel.

if all the GSM handling is done in kernel space, but i am not sure this is necessarily true. i think in the openmoko the GSM chips is connected by serial. the kernel just has the serial port driver, all the commands to the chip are send from a userspace daemon.

---

### Post by Simian Man on 2010-11-15
You could run programs on the phone's general purpose processor easily enough.  I think making it actually do the things you expect a phone to do would be pretty much insurmountable though.

---

