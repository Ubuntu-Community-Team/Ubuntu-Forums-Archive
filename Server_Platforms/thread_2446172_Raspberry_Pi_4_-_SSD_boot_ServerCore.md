---
title: "Raspberry Pi 4 - SSD boot Server/Core"
date: 2020-06-25
forum: Server Platforms
---

### Post by goney3 on 2020-06-25
Hello Ubuntu Community,
I can't seem to get Ubuntu Server or Ubuntu Core to boot on SSD like I can with the RaspiOS. I have seen some solutions that use an SD card along with the SSD, but I prefer to be able to use my SD card for other things and just run off the SSD as intended. I noticed Berry Boot has been able to act as an intermediary and install Ubuntu to SSD and run, but I would prefer a pure solution. I have attempted copying over the elf and dat files from the most recent firmware to the boot of Ubuntu Server/Core and it just spits me out to uboot. To clarify, I have installed RaspiOS 64-bit on the SSD and it does boot correctly, so my issue seems to be with Ubuntu Server/Core.

What brought me to this issue is the recent release of Ubuntu Core Appliances and I wanted to try them out, but with no SSD support this is a bit of a snag for me.

Could anyone please point me in the right direction to research? I searched for "raspberry" and "ssd" here on the forums without much success. I have also looked through the Raspberry Pi forums without much luck either, most of them mention to contact Ubuntu directly as its their software running on the Pi itself.

Thank you all for your time and valuable feedback :)

---

### Post by LHammonds on 2020-06-25
There is more than one version of Raspberry Pi and more than one version of Ubuntu Server.  You failed to mention the specifics for both.

I assume you have the Raspberry Pi 4 with 8 GB of RAM because you mentioned RaspiOS 64-bit?

I assume you are wanting Ubuntu Server 20.04 (latest version).

Here is one of several how-to guides for this: [https://www.linuxhowto.info/how-to-install-ubuntu-20-04-on-raspberry-pi/](https://www.linuxhowto.info/how-to-install-ubuntu-20-04-on-raspberry-pi/)

Just make sure you are selecting the "ARM" version of Ubuntu because that is the processor type in the Pi.

**EDIT #1: **Oops, noticed you said Pi 4 in the title, sorry.

**EDIT: #2:** Seems the 1st link died within a day of posting it (probably a temporary issue with the whole site).  Fear not, using the dark magic of Google-Fu, I search the exact same title of that article (in the URL) and found these matching ones (and related) at different sites:
[Install Ubuntu 20.04 on Raspberry Pi]("https://linuxconfig.org/install-ubuntu-20-04-on-raspberry-pi") @ LinuxConfig.org
[Ubuntu downloads for Rapsberry Pi]("https://ubuntu.com/download/raspberry-pi") @ Ubuntu.com
[Ubuntu 20.04 64bit Full Desktop on Raspberry Pi 4 Installation and Demo(VIDEO)]("https://www.raspberrypi.org/forums/viewtopic.php?t=269749") ([YouTube Direct Link]("https://www.youtube.com/watch?v=RE_6PU7MNKo"))
[Ready, Set, Bake: Ubuntu 20.04 LTS is Now Certified for the Raspberry Pi]("https://www.omgubuntu.co.uk/2020/05/ubuntu-20-04-lts-is-certified-for-the-raspberry-pi")
[How to Install Ubuntu on Your Raspberry Pi]("https://www.tomshardware.com/how-to/install-ubuntu-raspberry-pi") @ TomsHardware

LHammonds

---

### Post by amen8 on 2020-06-26
first the link provided by **[[COLOR=#ff0000]LHammonds[/COLOR]]("https://ubuntuforums.org/member.php?u=1448924")** is broken.
I came accross the same issue and instead of creating a new thread I will just refine this one.
the best logical answer I found was here ([LINK]("https://askubuntu.com/questions/1237380/boot-ubuntu-20-04-on-a-raspberry-pi-4-from-ssd?newreg=9ec91f9aa38540d6852e6e53bbb673fa")) under askubuntu.com subsite for stackexchange.com 
only problem is it takes ages and nothing happens eventually
and by nothing happens I mean, the SSD card is being in read, since the SSD controller read LED is blinking like crazy but the raspberry pi machine doesnt get any local IP from the router, meaning the boot is either still in progress, or failed and there is a loop/RAM leak, making the LED to blinking without any results.

---

### Post by LHammonds on 2020-06-26
> **amen8 said:**
> first the link provided by **[[COLOR=#ff0000]LHammonds[/COLOR]]("https://ubuntuforums.org/member.php?u=1448924")** is broken.Additional links added.

Regarding your issue, it would be best if you posted details about what you are using.  Which Pi and options (such as 8GB model) and make sure you are using an approved SD card.  Not all SD cards are created equal.  [SD cards for Raspberry Pi](https://www.raspberrypi.org/documentation/installation/sd-cards.md)

LHammonds

---

### Post by goney3 on 2020-06-26
I'm asking about an SSD, not an SD.

Thanks!

---

### Post by Kradenko on 2020-06-28
> **LHammonds said:**
> Additional links added.

Regarding your issue, it would be best if you posted details about what you are using.  Which Pi and options (such as 8GB model) and make sure you are using an approved SD card.  Not all SD cards are created equal.  [SD cards for Raspberry Pi]("https://www.raspberrypi.org/documentation/installation/sd-cards.md")

LHammonds

He is referring to the booting of the OS from an external SSD via USB. It is now possible on Raspberry Pi OS. Here is a nice blog about it:

[https://www.jeffgeerling.com/blog/2020/im-booting-my-raspberry-pi-4-usb-ssd](https://www.jeffgeerling.com/blog/2020/im-booting-my-raspberry-pi-4-usb-ssd)

@goney3[COLOR=#000000], I suspect there is something with how it finds the boot partition. I am also keen to find out when they will release an update to do the booting. Also, to add to this, any idea how you can do the firmware/bootloader updates via Ubuntu( Even if it's on a SD)?

D.[/COLOR]

---

### Post by amen8 on 2020-06-28
@[COLOR=#000000][goney3]("https://ubuntuforums.org/member.php?u=2147576") we get it.
the SD is used just to update the raspberry pi 4 firmware since the old one doesnt support USB boot, after that you can start using your SSD from the beginning when you power it on.

[/COLOR]
@[LHammonds]("https://ubuntuforums.org/member.php?u=1448924")
first here is all my hardware specs:
-raspberry pi 4 2bg powered using the original power cord.
-microSD card SanDisk Ultra 32 GB 10 A1 HC-I
-Kingston microSD reader (SD to USB adapter)

steps taken:
-installed raspberry pi OS 32bit recommended version on raspberry-pi-imager
-plugged, SSH to it (headless setup), exectued ```
sudo apt update && sudo apt full-upgrade
```
-edited the file in: ```
[COLOR=#030303][FONT=Roboto]/etc/default/rpi-eeprom-update[/FONT][/COLOR]
``` and changed ```
critical 
```to ```
stable
``` (eeprom stable release)
-updated the eeprom firmware using: ```
[COLOR=#030303][FONT=Roboto]sudo rpi-eeprom-update -d -f /lib/firmware/raspberrypi/bootloader/stable/pieeprom-2020-06-15.bin[/FONT][/COLOR]
``` this is the latest _**stable **_version _**officially**_ supporting USB boot
-unplugged the SD card, and power cord to my raspberry pi, then using the kingston SD reader plugged **the same SD **to the USB port on **the same raspberry pi **without any changes to the files in the SD.
it worked like charm. so this is enough evidence the USB boot should work!!! until i wipe **the same SD** with an ubuntu image using _raspberry pi imager_ aaaaaand the raspberry pi 4 doesnt boot.
so this is clearly an issue with ubuntu.

ps: I tried a suggested solution of copying and replacing all .elf and .fat files from the [official github repo for raspberry]("https://github.com/raspberrypi/firmware/tree/master/boot") to the /boot directory in my SD, and it didnt help.
[COLOR=#DD4814]LHammonds[/COLOR]

---

### Post by amen8 on 2020-06-28
that blog is a little bit outdated by now, since there is a newer eeprom update released with a timestamp June 16. [check here]("https://github.com/raspberrypi/rpi-eeprom/tree/master/firmware")
and it is now a stable release (so you have to edit /etc/default/rpi-eeprom-update to stable instead of critical)

i dont know why you want to update the bootloader firmware using ubuntu because it doesnt matter at all. as long as you update it (by any means possible)
so for simplicity, use a temporary raspberry OS image on SD.

---

### Post by Kradenko on 2020-06-29
> **amen8 said:**
> that blog is a little bit outdated by now, since there is a newer eeprom update released with a timestamp June 16. [check here]("https://github.com/raspberrypi/rpi-eeprom/tree/master/firmware")
and it is now a stable release (so you have to edit /etc/default/rpi-eeprom-update to stable instead of critical)

i dont know why you want to update the bootloader firmware using ubuntu because it doesnt matter at all. as long as you update it (by any means possible)
so for simplicity, use a temporary raspberry OS image on SD.

I know it's dated. Like 2 weeks out of date. -_- But it's to show LHammonds what we are looking to do with Ubuntu.

---

### Post by QIII on 2020-06-29
OK.  Will the hijackers please desist and start your own threads?  All you are doing is adding distractions and confusion.

I expect that from this point forward only goney3 and those who provide answers will take part in this thread.  No more "me too" responses.

All "me to" posts from here on out will be jailed without warning.

---

### Post by Kradenko on 2020-06-30
> **QIII said:**
> OK.  Will the hijackers please desist and start your own threads?  All you are doing is adding distractions and confusion.

I expect that from this point forward only goney3 and those who provide answers will take part in this thread.  No more "me too" responses.

All "me to" posts from here on out will be jailed without warning.

100%, My apologies. I would have thought a discussion regarding the same topic would go in the same thread. 

I will go make my own thread about exactly the same subject.

Sorry again,
D.

---

### Post by wildmanne39 on 2020-06-30
> **Kradenko said:**
> 100%, My apologies. I would have thought a discussion regarding the same topic would go in the same thread. 

I will go make my own thread about exactly the same subject.

Sorry again,
D.
Hi Kradenko, the reason we ask that in the support sub-forums that all users create there own threads is so each user can get the individual help they deserve because even though many issues look the same on the surface in most cases they have a different underlying cause and it gets confusing for the users being helped and the volunteers helping in the thread, if you are offering support to the OP of the thread to resolve an issue by all means it is alright to post in the thread.

Cheers

---

### Post by goney3 on 2020-07-06
A July 5th 2020 solution to this thread can be found here:

*RPI4 Direct USB Boot Ubuntu 20.04*
[https://www.raspberrypi.org/forums/viewtopic.php?f=131&t=278791](https://www.raspberrypi.org/forums/viewtopic.php?f=131&t=278791)

---

