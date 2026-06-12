---
title: "How to record with an emu 0404 pci card"
date: 2008-08-26
forum: Ubuntu Studio
---

### Post by darkline on 2008-08-26
Hi all,

I would like to start recording music in audacity with an emu 0404 pci card (i have ubuntustudio 8.04). I have tried but no sound was recorded (but i dont understand JACK and some of  the settings).
If another program is easier for recording that is fine, i can always import it after.

Also, if possible would i be able to monitor the sound recorded through a different soundcard at the same time (that one being either onboard sound or a c-media CMI8738 )

Thanks for any help!

---

### Post by darkline on 2008-09-02
bump?

---

### Post by tuxulin on 2008-09-03
what is and where did you get the driver for your emu 0404 ?

i have that card too but i have never being able to get it going.


Tuxulin

---

### Post by darkline on 2008-09-06
Hmmm, well i was thinking that it was all installed fine before, bnut it seems it isnt.

heres what i have so far!

1, run the script from this [post](http://ubuntuforums.org/showpost.php?p=5236403&postcount=22) except changing the alsa versions to
[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.17a.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.17a.tar.bz2)
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18rc1.tar.bz2)
[ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.17.tar.bz2](ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.17.tar.bz2)
[ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.17.tar.bz2](ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.17.tar.bz2)
[ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.18rc2.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.18rc2.tar.bz2)

(all just a bit more recent than the others).

2, reboot 

3,then run ```
dmesg | grep alsa
[   44.570523] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:822: emu1010: Special config.
[   44.570605] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:861: emu1010: EMU_HANA_ID=0x7f
[   44.570610] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:880: emu1010: filename emu/emu0404.fw testing
[   47.114133] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:684: firmware size=0xd67c
[   51.869740] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:893: emu1010: Loading Hana Firmware file failed, reg=0x7f

```

now that file exists but is not executable (dont know if that makes a difference!!)

also i ran ```
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Aug 25 2008 for kernel 2.6.24-21-generic (SMP).

```
Which isnt the version i installed!! I installed this a while ago (as you can see). I believe this may be part of the problem but am not sure.

also here is ```
asoundconf list
Names of available sound cards:
SI7012
Headset
CMI8738

```
my emu doesnt appear!!


So i think its something to do with it not seeing the version i installed - more research needed i think!

tuxulin, are your outputs of the above commands similar or not? if they are, at least the problems consistant!

---

### Post by tuxulin on 2008-09-06
i tried it all and for the most parts got the same results.
for what its worth when i ran asoundconf list all that showed
is "Audio PCI"

i have 1 sound card on the PCI which is the emu 0404 and since
sound is only coming from my built in stock sound card then i think it is referred to the pci card. strange but true.


Tuxulin

---

### Post by darkline on 2008-09-07
hmm does seem odd, wish i knew how to do this but my linux knowledge just isnt good enough!!!

i tried uninstalliong alsa 1.0.16, but am now left with a computer that wont login because some files are missing (i think the error is something like cant find file asound).

Brilliant.

---

### Post by oneevilwombat on 2009-03-08
i cant wait until i can get mine to work in ubuntu either,
ive been playing guitar for a while,and id like to see bill gates sit on a tack...a LONG rusty one...until then i guess i hafta use
it in ( urk) winxp...
:guitar:

---

