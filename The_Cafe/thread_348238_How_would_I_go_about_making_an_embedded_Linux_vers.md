---
title: "How would I go about making an embedded Linux version that would run on a Palmpilot?"
date: 2007-01-28
forum: The Cafe
---

### Post by presbp on 2007-01-28
I was thinking of trying to build a Linux distro from scratch that would run on a palmpilot or a device similar to that such as  Treo.  Even better.. could I get a Linux distro to run on a phone such as this [http://www.nokiausa.com/phones/6126/](http://www.nokiausa.com/phones/6126/)

---

### Post by zvandiver on 2007-01-28
Check out this site [http://shadowmite.com/wiki/index.php/Treo_650_Linux_Port_Status_-_Mirror_of_handhelds.org](http://shadowmite.com/wiki/index.php/Treo_650_Linux_Port_Status_-_Mirror_of_handhelds.org)
and this one [http://www.hackndev.com/](http://www.hackndev.com/)

Zane

---

### Post by ZylGadis on 2007-01-28
The first and most important hurdle for embedded linux is drivers. You have to carefully investigate the actual hardware chips / components the device is made of, and see if linux drivers already exist. If not, perhaps you may want to write them yourself - it is not difficult, but you need to have good documentation on the hardware interfaces. Which is, generally, information that hardware manufacturers do not provide to the general public.

So, to sum up: embedded linux is not at all hard, provided the hardware manufacturers are willing to cooperate by providing the necessary information.

I don't know about Nokia, but I would not bet on any manufacturer installing windows by default to give you the necessary information.

---

