---
title: "Disco Live iso boots to low resolution."
date: 2019-04-16
forum: Ubuntu Development Version
---

### Post by again? on 2019-04-16
Never had problems with previous releases on same hardware.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] inxi -MG**
Machine:   Device: desktop Mobo: Gigabyte model: GA-78LMT-USB3 v: x.x serial: N/A BIOS: Award v: FA date: 04/23/2013
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti]
```
Boots to 640x480 using llvmpipe driver.
Not able to install as I can't see or manipulate confirmation boxes into view.

Should the nouveau driver be loading?
Can I edit grub to force nouveau?

---

### Post by again? on 2019-04-16
Ok I just solved it.
I booted to an 18.04 iso and checked to see if it was using the nouveau driver which it was.

Solution:
Edit grub boot menu and add
```
nouveau.modeset=1
```
Now boots to my monitors default resolution.

---

### Post by thenailedone on 2019-04-17
I also had an iso from last week do this... then a few days ago the iso I downloaded at least booted at 1024x768 so I could get the installation done (and was impressed after install when I had nvidia 4.18 drivers already installed).

---

### Post by again? on 2019-04-17
Yes, must have been a glitch.
I thought it might have been because I was booting directly from the iso through grub but
I have since updated the daily-live iso with zsync and it boots using the nouveau driver.

---

