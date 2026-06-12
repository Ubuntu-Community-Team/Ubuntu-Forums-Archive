---
title: "hammerfall hdsp multiface not working"
date: 2009-02-20
forum: Ubuntu Studio
---

### Post by pulse00 on 2009-02-20
hi,

i'm using a hammerfall hdsp multiface audiocard, which worked fine in previous versions of ubuntu. Yesterday i installed 8.10, but unfortunately my soundcard isn't working anymore.

The card comes with it's own mixer called hdspmixer which is installed via
the alsa-tools-gui. Also, it has a hdsploader app which loads the firmware to the card (it comes with the alsa-firmware-loaders package i think).

Previous ubuntu versions came with a package called alsa-firmware which included the firmware for the card. Ubuntu 8.10 doesn't seem to have this package anymore. After some googling i've found the alsa-firmware package in the Medibuntu repository.

After installing the alsa-firmware package, the hdsploader outputs the following error:

```
hdsploader - firmware loader for RME Hammerfall DSP cards
Looking for HDSP + Multiface or Digiface cards :
Card 0 : RME Hammerfall DSP + Multiface at 0xf87f0000, irq 22
Upload firmware for card hw:0
Hwdep ioctl error on card hw:0 : Device or resource busy.
```

It seems to detect the card fine but can't acces it for some reason.

The mixer works fine btw, i'm just not hearing any sound but i assume that's related to the hdsploader problem.

Anyone knows what could cause this ?

---

### Post by thorgal on 2009-02-20
try a complete power off first :
shutdown PC
unplug power cable
unplug firewire cable from multiface

then, plug all that stuff back and reboot. Youshould see a red light on the front panel of the multiface at early boot time, turning off as the firmware gets loaded at a later stage during the boot process.

I experimented suspend to S3 and resume and I got problems of that kind. Only a complete power off fixed it. I have a Multiface II by the way. The Multiface I could be a bit different ...

---

### Post by calimerox on 2009-06-01
thorgal, I actually have at the moment right the same problem ..

hdsploader
hdsploader - firmware loader for RME Hammerfall DSP cards
Looking for HDSP + Multiface or Digiface cards :
Card 0 : RME Hammerfall DSP + Multiface at 0xc4000000, irq 11
Upload firmware for card hw:0
Hwdep ioctl error on card hw:0 : Device or resource busy.

it sais.. and usually I could solve it with your described power off trick.. but now it doesnt, im with the jaunty distro and i can see the red light turning off at  startup, but it doesnt work... 

thx for help guys... :(

---

