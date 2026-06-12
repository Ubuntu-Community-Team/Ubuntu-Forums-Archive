---
title: "Ubuntu studio on A135-s4666?"
date: 2008-07-06
forum: Ubuntu Studio
---

### Post by Umbro_domini on 2008-07-06
Hi!I've Installed Ubuntu studio from the repo and I find it hard to configure my audio input/output with Jack.Audacity and mixx  doesn't detect my audio device each time I change an option.And Adour that requires jack doesn't see any music files. I really need help in configuring it properly, for everything to work the way it should work...

heres my hardware infos:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


thanks in advance!!!:D...Hope some one could help out..

---

### Post by thorgal on 2008-07-06
you have the infamous Intel HDA chip ;)

make sure the alsa module is loaded. In a terminal, type :

lsmod | grep snd

and spot snd-intel-hda

then, if you want to use jackd with it, either use qjackctl or the terminal command prompt. In the latter case, try this :

jackd -R -dalsa -dhw:0 -p1024 -n3

(note n=3, it is important here).

the -R indicates realtime operation. Hopefully, you can do this, otherwise, you will have to edit (as superuser) the file 

/etc/security/limits.conf

with this at the end :

username - rtprio 99
username - memlock unlimited
username - nice -19


replace username by your own username, log out and log in again.
If you want this capability for a whole group (e.g. the audio group, which should exist ... check the file /etc/group to see if it does, and that you belong to it. You should see something like  

audio: x :29:username  

!no spacing, this stupid forum interface interprets it as a smiley, godd..mn these icons!!), then the limits.conf file becomes :

@audio - rtprio 99
@audio - memlock unlimited
@audio - nice -19

Note you need the @ to specify that you refer to a unix group.

So try all this and report back here.

---

### Post by Umbro_domini on 2008-07-06
thanks ..i'll try it right away  and report if its successful
:D

---

### Post by Umbro_domini on 2008-07-06
Thank you thank youThank you thank youThank you thank youThank you thank youThank you thank you Thorgal!!!it worked very smoothly...:D.....

---

### Post by thorgal on 2008-07-06
cool! let the music rock :guitar:

---

