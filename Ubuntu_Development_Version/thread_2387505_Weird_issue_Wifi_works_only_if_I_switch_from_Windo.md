---
title: "Weird issue: Wifi works only if I switch from Windows to Ubuntu"
date: 2018-03-19
forum: Ubuntu Development Version
---

### Post by manmath on 2018-03-19
I'm running system with Bionic and Windows 10 in a dualboot setup. Everything works in both the OSes, but wifi on Bionic works if I first boot windows and then reboot the system to Bionic. So that means, I've to boot windows to get wifi work in linux. Here's some info you might find helpful.

```
lsusb:
Bus 002 Device 004: ID 046d:0825 Logitech, Inc. Webcam C270
**Bus 002 Device 003: ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter**
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1a2c:2124 China Resource Semico Co., Ltd 
Bus 001 Device 003: ID 04ca:0061 Lite-On Technology Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

iwconfig:
**wlx00367620cc77**  IEEE 802.11  ESSID:"purvi"  
Mode:Managed  Frequency:2.437 GHz  Access Point: E6:62:51:04:3E:87   
Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
Retry short limit:7   RTS thr:off   Fragment thr:off
Encryption key:off
Power Management:off
Link Quality=61/70  Signal level=-49 dBm  
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:12   Missed beacon:0
```

---

### Post by wildmanne39 on 2018-03-19
*Thread moved to **Ubuntu Development Version, a more appropriate forum**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Code tags also prevents the smiley faces from showing up when you post your output to the forum.

---

### Post by wyliecoyoteuk on 2018-03-20
Ubuntu is not loading the firmware for some reason.
Wifi adapters need firmware loading at boot to deal with country specific wifi rules.
The reason it works after booting windows is that the firmware is not flushed on a warm boot.

the firmware should be:

/lib/firmware/mt7601u.bin

you may be able to copy it from your windows driver package, or from an older version of Ubuntu

---

### Post by chili555 on 2018-03-20
> **wyliecoyoteuk said:**
> Ubuntu is not loading the firmware for some reason.
Wifi adapters need firmware loading at boot to deal with country specific wifi rules.
The reason it works after booting windows is that the firmware is not flushed on a warm boot.

the firmware should be:

/lib/firmware/mt7601u.bin

you may be able to copy it from your windows driver package, or from an older version of UbuntuThe firmware is included in the package linux-firmware which is installed by default. Moreover, if an interface is created and it connects, which it clearly did, then the firmware is, no doubt, present.

Please cold boot straight into Ubuntu and run:```
lsmod | grep mt7
```Is the driver mt7601u loaded? If not, does the wireless spring to life if you do:```
sudo modprobe mt7601u
```If the driver is loaded, does restarting Network Manager help?```
sudo service network-manager restart
```Are there any clues in the log?```
dmesg | grep -e mt7 -e wlx
```

---

### Post by wyliecoyoteuk on 2018-03-20
Firmware has been missed out of linux-firmware before now. As Bionic is still pre-release, it may have gone unnoticed.
The fact that it does work if he boots into Windows first, points to the driver functioning only if the firmware is already loaded.
So either the firmware file is missing, or the driver is not loading it, or not loading it early enough.

---

### Post by chili555 on 2018-03-20
> The fact that it does work if he boots into Windows first, points to the driver functioning only if the firmware is already loaded.And survived a reboot from one OS to another completely different OS? Very doubtful.> So either the firmware file is missingNo.

---

### Post by wyliecoyoteuk on 2018-03-20
> **chili555 said:**
> And survived a reboot from one OS to another completely different OS? Very doubtful.
Not doubtful at all, I have seen it many times after a warm boot on a dual boot install.
Another symptom is that on Windows or Linux dual boot installs, wifi will only work properly after a cold boot, due to one OS leaving the firmware in an unexpected state for the other OS.
It is less common these days, mainly due to more graceful shutdowns, but it doesn't mean it can't happen.
Of course, I have only been working on networks since 1995, so what do I know.

---

### Post by monkeybrain20122 on 2018-03-20
Maybe same issue as [this thread]("https://ubuntuforums.org/showthread.php?t=2386964"). I also experienced firmware missing in kernel 4.15.

Edited: I fixed it by compiling kernel 4.16 rc4 from a [patched source]("https://git.kernel.org/pub/scm/linux/kernel/git/kvalo/wireless-drivers.git/"). At that time the newest kernel on mainline kernel ppa was 4.16 rc2 and it didn't work, Now 4.16 rc6 is available,  if the patch has been merged upstream upgrading your kernel to 4.16 rc 6 should fix it.

---

### Post by wyliecoyoteuk on 2018-03-20
Out of interest, I just downloaded and installed Bionic in a vm, and the firmware file is indeed there.
Bionic currently runs kernel 4.15.0-12, so monkeybrain20122's solution should work.

---

### Post by manmath on 2018-03-20
> **wyliecoyoteuk said:**
> 
the firmware should be:

/lib/firmware/mt7601u.bin

That's already there! Strange but sadly true. The ubuntu firmware package has it. And I checked it's there. It's really puzzling.

I tried all those commands you mentioned in two instances, 1) booting directly to Ubuntu where none returned anything and there was no wifi network, and 2) Switching from Windows to Ubuntu where wifi worked as desired, and lsmod showed mt7601, modprobe showed the module is already loaded, restarting network-manager showed first disconnecting the wifi and reconnecting, and dmesg showed "usbcore: registered new interface driver mt7601u".

> **wyliecoyoteuk said:**
> Firmware has been missed out of linux-firmware before now. As Bionic is still pre-release, it may have gone unnoticed.
The fact that it does work if he boots into Windows first, points to the driver functioning only if the firmware is already loaded.
So either the firmware file is missing, or the driver is not loading it, or not loading it early enough.

No, it's there, /lib/firmware has a file mt7601u.bin.

> **wyliecoyoteuk said:**
> Ubuntu is not loading the firmware for some reason.
Wifi adapters need firmware loading at boot to deal with country specific wifi rules.
The reason it works after booting windows is that the firmware is not flushed on a warm boot.

the firmware should be:

/lib/firmware/mt7601u.bin

you may be able to copy it from your windows driver package, or from an older version of Ubuntu

It's already there.

> **chili555 said:**
> And survived a reboot from one OS to another completely different OS? Very doubtful.No.

The firmware mt7601u.bin is there in /lib/firmware.

---

### Post by monkeybrain20122 on 2018-03-20
> **manmath said:**
> It's already there.

Can you do a fresh boot (not logging into Windows first) and then post the output of 
```

lshw -C network
```

---

### Post by manmath on 2018-03-20
> **wyliecoyoteuk said:**
> Not doubtful at all, I have seen it many times after a warm boot on a dual boot install.
Another symptom is that on Windows or Linux dual boot installs, wifi will only work properly after a cold boot, due to one OS leaving the firmware in an unexpected state for the other OS.
It is less common these days, mainly due to more graceful shutdowns, but it doesn't mean it can't happen.
Of course, I have only been working on networks since 1995, so what do I know.

Very right. I had experienced similar issues long back. But it's first in Bionic, even in cold boots (booting system after 10 hours). Bionic is behaving quite well except for this wifi problem. What's surprising that, if I boot from xenial or debian 9.4 livecd the wifi works quite good, as expected. But it's really troublesome for me to install any of them. As my root partition resides on a sata dom with many other packages and lots of customizations.

> **monkeybrain20122 said:**
> Maybe same issue as [this thread]("https://ubuntuforums.org/showthread.php?t=2386964"). I also experienced firmware missing in kernel 4.15.

Edited: I fixed it by compiling kernel 4.16 rc4 from a [patched source]("https://git.kernel.org/pub/scm/linux/kernel/git/kvalo/wireless-drivers.git/"). At that time the newest kernel on mainline kernel ppa was 4.16 rc2 and it didn't work, Now 4.16 rc6 is available,  if the patch has been merged upstream upgrading your kernel to 4.16 rc 6 should fix it.

Thanks. It worked! I compiled 4.16 rc6 from the mainline, and the wifi works as desired.

(Actually, half an hour before participating in the thread I was compiling mainline 4.16 rc6 kernel like a game. But hey, it helped. Just copied the default .config from boot. It took long, but was worth it!)

---

### Post by monkeybrain20122 on 2018-03-20
> **manmath said:**
> . But it's really troublesome for me to install any of them. As my root partition resides on a sata dom with many other packages and lots of customizations.

You can use fsarchiver to "clone" your Bionic installation and restore it where ever and install an OS that works for you.

So you mean you spend a lot of time customizing a pre-release OS meant for testing? :o That is kind of odd. :) I plan to wipe my Bionic partition and reinstall several times before release and wipe it again after, since it is for experimentations and not for real work. :)

---

### Post by manmath on 2018-03-20
Mainline kernel 4.16 rc6 fixed the problem. It's weird though cos in stock bionic kernel modules for my mediatek card was already there as well as the firmware in linux-firmware. Anyways, it solved.
But how can I mark the thread solved? I can't see such option.

---

### Post by monkeybrain20122 on 2018-03-20
> **manmath said:**
> Thanks. It worked! I compiled 4.16 rc6 from the mainline, and the wifi works as desired.

So maybe that firmware you saw is a stub. it is not really there. Do you mean you downloaded the .debs from mainline? Compiling kernel takes a long time.

---

### Post by monkeybrain20122 on 2018-03-20
> **manmath said:**
> 
But how can I mark the thread solved? I can't see such option.

It is under thread tools on the upper right.

---

### Post by manmath on 2018-03-20
> **monkeybrain20122 said:**
> You can use fsarchiver to "clone" your Bionic installation and restore it where ever and install an OS that works for you.

So you mean you spend a lot of time customizing a pre-release OS meant for testing? :o That is kind of odd. :) I plan to wipe my Bionic partition and reinstall several times before release and wipe it again after, since it is for experimentations and not for real work. :)

Of course, odd. But I found Bionic better than Xenial. Good that with 4.16 rc6 kernel from the mainline the problem is resolved. Now I've my fingers crossed, will only update the system when the final/stable Bionic is released.

Thank you all for being so supportive.

> **monkeybrain20122 said:**
> So maybe that firmware you saw is a stub. it is not really there. Do you mean you downloaded the .debs from mainline? Compiling kernel takes a long time.

No debs, could not find any. Just downloaded the tar.gz file, extracted it, copied the config file from boot partition and compiled the package. It took some half an hour in a quad-core setup with -j 4 compiling option.

---

### Post by monkeybrain20122 on 2018-03-20
> **manmath said:**
> No debs, could not find any. Just downloaded the tar.gz file, extracted it, copied the config file from boot partition and compiled the package. It took some half an hour in a quad-core setup with -j 4 compiling option.

It took me almost two hours with -j4. But that is an old machine. You don't need to compile from source if you get the kernel from mainline, just download 3 .debs (headers all, headers generic and image generic) put them in one folder, cd into it and do

```
dpkg -i *.deb
```

Reboot, that's it.

I compiled at that time since the fix has not been merged upstream yet (as evident that the latest from mainline 4.16-rc2 didn't work) Now it apparently has.

---

### Post by monkeybrain20122 on 2018-03-20
> **manmath said:**
> No debs.

Here they are [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.16-rc6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.16-rc6/)

---

### Post by manmath on 2018-03-20
> **monkeybrain20122 said:**
> It took me almost two hours with -j4. But that is an old machine. You don't need to compile from source if you get the kernel from mainline, just download 3 .debs (headers all, headers generic and image generic) put them in one folder, cd into it and do

```
dpkg -i *.deb
```

Reboot, that's it.

I compiled at that time since the fix has not been merged upstream yet (as evident that the latest from mainline 4.16-rc2 didn't work) Now it apparently has.

Sad, I was not aware of it. The problem is solved. But where's the 4.16 kernel in bionic repo? I could not find it that's why just as a game I downloaded tar.gz from mainline (kernel.org).

> **monkeybrain20122 said:**
> Here they are [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.16-rc6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.16-rc6/)
Sorry, I was not aware of it. I was searching the package cache for the source file in source.list. Thank you for pointing the ppa.

---

### Post by monkeybrain20122 on 2018-03-20
> **manmath said:**
> Sad, I was not aware of it. The problem is solved. But where's the 4.16 kernel in bionic repo? I could not find it that's why just as a game I downloaded tar.gz from mainline (kernel.org).

No, no 4.16 in Bionic repo. Since it is a LTS I have the feeling that it will be stuck with 4.15 for until 18.04.2 when you can opt in to HWE then you can upgrade kernel in the "official way", unless it provides 4.16 at release time.

---

### Post by manmath on 2018-03-20
One more problem though not so serious and doesn't affect Bionic. Now that same wifi dongle is not working properly in Windows. It works only if I shut down Bionic, switch off the UPS, and then cold boot to Windows. But it's ok, i can live with it. Will test it a few days and then will format the windows partition. I doubt something is wrong with the mediatek wifi dongle (I got it from grey market for $3 (INR 200). It's still in warranty, if doesn't work well will replace it or buy another one. So, guy please suggest a wifi dongle that works perfectly well on Linux and not so expensive.

---

### Post by monkeybrain20122 on 2018-03-20
> **manmath said:**
> One more problem though not so serious and doesn't affect Bionic. Now that same wifi dongle is not working properly in Windows. It works only if I shut down Bionic, switch off the UPS, and then cold boot to Windows. But it's ok, i can live with it. Will test it a few days and then will format the windows partition.

No idea, the only Windows I have is Win7 in VM.:) Maybe you can mark this thread as solved? The tab is under thread tools on the top of the box (not the screen) on the right side.

---

### Post by manmath on 2018-03-20
> **monkeybrain20122 said:**
> No idea, the only Windows I have is Win7 in VM.:) Maybe you can mark this thread as solved? The tab is under thread tools on the top of the box (not the screen) on the right side.
Mine is Windows 10 Home 64bit. I've kept it for one purpose MS Office cos still libreoffice is unable to retain formatting of the files I receive. Now that the new Wine supports Office 2010/13, I can sacrifice Windows.

---

### Post by monkeybrain20122 on 2018-03-22
> **amiyakusahoo said:**
> Wired ethernet connection issue for this cause

1- Please check the ethernet cable colour code of the ethernet port.
2-Check some bad cabel and connector
3-check the networking Device like switch  are working properly
4-Check the Lan (local area network) driver is worked proper
5- and checked the router Lan setting some rules affected in your network

He didn't say "wired", but "weird". :) It is a wifi issue that has nothing to do with ethernet or ethernet cables.

---

