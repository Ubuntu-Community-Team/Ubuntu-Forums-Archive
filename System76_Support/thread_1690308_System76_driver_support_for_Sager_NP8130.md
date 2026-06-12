---
title: "System76 driver support for Sager NP8130"
date: 2011-02-18
forum: System76 Support
---

### Post by seanlano on 2011-02-18
I would really love to have a Gazelle Professional, but System76 won't ship to Australia. I have read that the Gazelle is based on the Sager NP8130 - in fact they look exactly the same and have the same specs etc. I have found a few retailers of the Sager NP8130 who will ship to Australia, and will also let me put a customised image on the laptop lid as an extra. 

My question is: Will the System76 Gazelle Professional drivers allow me to use my Sager NP8130 with full functionality? I'm pretty sure that at least the fingerprint reader and maybe more won't work without it - but since they are basically exactly the same hardware the driver should work, right? I would love to have the actual System76 product, but it is too expensive to try and get it shipped here, so the Sager is really my only choice.

---

### Post by isantop on 2011-02-18
You're more than welcome to try it out, but I'm not sure you'll get very far. The System76 driver won't run on a non-system76 machine, so you'll get an error on startup saying that the Driver is designed for System76 computer running Ubuntu.

---

### Post by msrinath80 on 2011-02-18
What you need to do is basically open up the System76 driver package and examine each of the python scripts by hand. Check using lshw,lsusb,lspci whether you have the same hardware and if so, manually follow the python scripts. It will take both time and patience.

---

