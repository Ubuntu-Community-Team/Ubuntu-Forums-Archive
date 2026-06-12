---
title: "why there is no Ubuntu version for Raspberry Pi"
date: 2013-06-26
forum: The Cafe
---

### Post by asifnaz on 2013-06-26
I have tried both Debian and Fedora on raspberry pi and they are running great . Still waiting to hear from Ubuntu:popcorn:

---

### Post by hakermania on 2013-06-26
Ubuntu is way too heavy for such a small system! Debian runs great, though :)

---

### Post by Bucky Ball on 2013-06-26
If an OS is based on Debian I guess it's more than halfway there. I have Raspbian running great on mine and apparently Rasp, Xbian and a few other Debian based systems work fine, too, so I hear.

---

### Post by asifnaz on 2013-06-26
> **hakermania said:**
> Ubuntu is way too heavy for such a small system! Debian runs great, though :)

Ubuntu is little a bit heavier but still should be run on Raspberry Pi without any problem .

---

### Post by Paqman on 2013-06-26
> **asifnaz said:**
> Ubuntu is little a bit heavier but still should be run on Raspberry Pi without any problem .

The RPi uses an older version of the ARM chip that isn't supported by Ubuntu. Ubuntu is focussed on the more up-to-date ARM versions that you'll find in phones and tablets.

---

### Post by Cheesemill on 2013-06-26
> **Paqman said:**
> The RPi uses an older version of the ARM chip that isn't supported by Ubuntu. Ubuntu is focussed on the more up-to-date ARM versions that you'll find in phones and tablets.

^ This.

Canonical dropped support for the ARMv6 processor (which is used for the Raspberry Pi) several years ago. The last version of Ubuntu available which ran on a version of that particular processor was 9.04 which reached end of life years ago.

At the end of the day there is little practical difference between running Ubuntu and running Debian on a Raspbery Pi, the software available for both is nearly identical.

---

