---
title: "Evolution MK-249c2"
date: 2014-05-13
forum: Ubuntu Studio
---

### Post by wolfej on 2014-05-13
Good Evening All,

I have been getting started using ubuntu studio to record music after having used the standard distro for my desktop for the past few years.

I already have a lexicon alpha working for recording guitars but I am struggling with getting my Evolution MK-249c2 usb midi keyborad working. The keyboard itself is receiving power over usb but doesn't look like it is being detected.

Any help would be greatly appreciated and thank you in advance.

JW

---

### Post by jejeman on 2014-05-13
Give
```
lsusb
amidi -l
```

---

### Post by wolfej on 2014-05-14
Bus 001 Device 003: ID 041e:406c Creative Technology, Ltd Live! Cam Sync [VF0520]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 1210:000a DigiTech 
Bus 002 Device 003: ID 046d:c52e Logitech, Inc. 
Bus 002 Device 002: ID 1130:1620 Tenx Technology, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


and


Dir Device    Name

---

### Post by jejeman on 2014-05-14
Did you had Evolution pluged in? Which one is it in lsusb output?

No MIDI device is recognized.

---

### Post by wolfej on 2014-05-16
Yes the Evolution is plugged in but not recognised. I have tried with an alternative; akai lpk25 which was detected straight away;

Bus 001 Device 003: ID 041e:406c Creative Technology, Ltd Live! Cam Sync [VF0520]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 046: ID 09e8:0076 AKAI  Professional M.I. Corp. LPK25 MIDI Keyboard
Bus 002 Device 004: ID 1210:000a DigiTech 
Bus 002 Device 003: ID 046d:c52e Logitech, Inc. 
Bus 002 Device 002: ID 1130:1620 Tenx Technology, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by jejeman on 2014-05-16
Well, if it is not listed in lsusb output, then it will not work.
Is device working on other PC/OS?

---

### Post by wolfej on 2014-05-17
I get the same result on another PC running ubuntu studio. I am going to  try with a windows laptop tomorrow and failng that with a midi to usb  adapter instead of the usb out on the keyboard. Thanks for all your help  so far, I will of course post the results as I get them.

---

