---
title: "Age of Mythology Install Disc 2 issue under Wine 1.0.1 in Ubuntu 9.04"
date: 2009-05-24
forum: Wine
---

### Post by jango102 on 2009-05-24
I've been trying to install AoM under Wine in Ubuntu 9.04. The installer works fine right up until it asks me to "Insert Disc 2 into drive D:". The first time around, I tried hitting the eject button on the computer, and ubuntu gave me this error message:

Failed to eject "/org/freedesktop/Hal/devices/storage_model_CD_ROM_LTN_487T".
Given device "/org/freedesktop/Hal/devices/storage_model_CD_ROM_LTN_487T" is not a volume or drive.

So I went into my file manager and clicked "eject volume". That worked, so I inserted Disc 2 and waited for it to show up in the file manager, then clicked "OK" in the AoM dialog box asking for the disc. After less than a second, the box came back. Somehow it can't detect the second disc. Has anybody had this problem? Is there anything I'm doing wrong?

---

### Post by coyotepod on 2009-06-10
in the Wine settings I clicked on Drives and autotect to detect the CD-ROM then it worked for me

---

