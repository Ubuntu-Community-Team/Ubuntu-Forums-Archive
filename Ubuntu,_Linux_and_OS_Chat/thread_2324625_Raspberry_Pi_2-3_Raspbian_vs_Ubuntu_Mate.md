---
title: "Raspberry Pi 2-3: Raspbian vs Ubuntu Mate"
date: 2016-05-15
forum: Ubuntu, Linux and OS Chat
---

### Post by erotavlas on 2016-05-15
Hi,
I would like to have an advice about the best OS for raspberry pi. I know that raspberry Pi 2,3 can run both raspbian and ubuntu mate. I read [here]("https://www.raspberrypi.org/forums/viewtopic.php?f=66&t=128329") and they are very similar since both use the same debian base. The majority of comparison are between raspbian jessie 8 and ubuntu mate 15.10. What about the latest release jessie 8.4 and ubuntu mate 16.04?
What are your recommendations? 
Thank you

---

### Post by speedwell68 on 2016-05-22
Raspbian, IMHO it is much better supported by the RPI community.

---

### Post by Frogs Hair on 2016-05-24
> **speedwell68 said:**
> Raspbian, IMHO it is much better supported by the RPI community.

I would agree , Raspbian uses a minimal LX panel configuration while Mate is Gnome 2 based. What I've read suggests mate may be a little resource hungry on a Pi.

---

### Post by ssam on 2016-05-25
Depends what you want to use it for, I use both for different tasks. Some tutorials and howtos might assume raspbian, and raspbian is still the official distros.

Ubuntu Mate gives you newer versions of software, so you might hit bugs in raspbian that have been fixed by the upstream developers a year ago. Ubuntu is compiled for armv7, so it will be a little faster on a Pi2 or Pi3, but wont run on a Pi1 or PiZero. Mate is a more featurefull and customisable desktop, but you might find the barebones LXDE in raspbian slightly faster. The opens source graphics driver is going to make them both much snappier to use soon, but is currently a bit unstable.

Best thing is to try both.

---

