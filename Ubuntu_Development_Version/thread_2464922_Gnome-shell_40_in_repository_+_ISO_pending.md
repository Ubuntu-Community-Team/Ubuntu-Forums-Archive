---
title: "Gnome-shell 40 in repository + ISO pending"
date: 2021-07-16
forum: Ubuntu Development Version
---

### Post by mohegan on 2021-07-16
Gnome-shell **40.2-1ubuntu1** is arrived in the official repository and in the daily ISO (pending version only at this time) !

[https://cdimage.ubuntu.com/daily-live/pending/]("https://cdimage.ubuntu.com/daily-live/pending/")


I will test it as soon as possible !!

---

### Post by VMC on 2021-07-16
> **mohegan said:**
> Gnome-shell **40.2-1ubuntu1** is arrived in the official repository and in the daily ISO (pending version only at this time) !

[https://cdimage.ubuntu.com/daily-live/pending/](https://cdimage.ubuntu.com/daily-live/pending/)


I will test it as soon as possible !!

Looks like it:
```
$ apt policy gnome-shell
gnome-shell:
  Installed: 40.2-1ubuntu1
  Candidate: 40.2-1ubuntu1
  Version table:
 *** 40.2-1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu impish/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by mohegan on 2021-07-16
I try the pending ISO and Ubiquity doesn't work. So, installation isn't possible. I try the canary installer but it is not complete. I can't select the partitions...

I will try tomorrow.

---

### Post by corradoventu on 2021-07-17
For the canary installer i have the same problem [https://github.com/canonical/ubuntu-desktop-installer/issues/36](https://github.com/canonical/ubuntu-desktop-installer/issues/36)

---

### Post by guiverc on 2021-07-17
I don't know if this is the issue, but it was one issue with recent `ubiquity`

***     Ubiquity fails to build with GTK4***

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1936488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1936488)

It's been marked *Fix Released* but you need to wait a ~day+ for it to find its way to the ISO

---

### Post by zebra2 on 2021-07-17
I have two copies of 21.10 dual booting on the same computer.  Both are on EXT4 format with bios set to legacy. 
I'm not having any trouble installing and booting these ISO's at all. I just zsync'ed with the current July 17th pending version and installed with no problems.
I don't do the UEFI thing so don't know about that. Gnome 40 is nice, but I'm not getting GTK4 yet.
```

ystem:
  Host: zebra-110-15ISK Kernel: 5.13.0-12-generic x86_64 bits: 64 
  compiler: gcc v: 10.2.1 Desktop: GNOME 40.2 tk: GTK 3.24.29 
  wm: gnome-shell dm: GDM3 Distro: Ubuntu 21.10 (Impish Indri) 
$DESKTOP_SESSION
ubuntu
$XDG_SESSION_TYPE
wayland
GNOME Shell 40.2
Version: 40.2-1ubuntu1
loginctl type
Type=wayland
zebra1@zebra-110-15ISK:~$ 

```

---

### Post by mohegan on 2021-07-17
Today, Ubiquity is fix. I have installed the current ISO. Just a little problem with my recent wifi card (Intel AX201). It wasn't recognize (same on 20.04). So, no bluetooth nor wifi. I added the impish proposed repository and update my system (to install linux-image-5.13.0-12).

Currently, no problem at all !

---

### Post by zebra2 on 2021-07-17
I don't know much about uefi, fastboot, and secure boot but if you turn those off your wifi may work. That wifi card has kernel drivers in Ubuntu.  You don't need uefi with Ubuntu and I havent seen anything in your posts that mention Windows.

---

### Post by VMC on 2021-07-17
> **mohegan said:**
> Today, Ubiquity is fix. I have installed the current ISO. Just a little problem with my recent wifi card (Intel AX201). It wasn't recognize (same on 20.04). So, no bluetooth nor wifi. I added the impish proposed repository and update my system (to install linux-image-5.13.0-12).

Currently, no problem at all !

type this in a terminal, and see what errors come out:
```
sudo dmesg|grep wifi
```

---

### Post by mohegan on 2021-07-18
The current impish kernel (linux-image-5.11.0-20) don't support my wifi card. The Intel WiFi AX201/AX203 was supported since kernel 5.12 and backported to kernel 5.11.4 : [https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.11.4-5.10.21-Released]("https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.11.4-5.10.21-Released")

With the current kernel (linux-image-5.11.0-20), it doesn't work :
```
[   12.023563] iwlwifi 0000:01:00.0: api flags index 2 larger than supported by driver
[   12.023599] iwlwifi 0000:01:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 93.8.63.28
[   12.024058] iwlwifi 0000:01:00.0: loaded firmware version 59.601f3a66.0 ty-a0-gf-a0-59.ucode op_mode iwlmvm
[   12.148084] iwlwifi 0000:01:00.0: Detected Intel(R) Wi-Fi 6 AX210 160MHz, REV=0x420
[   12.313082] iwlwifi 0000:01:00.0: loaded PNVM version 0x324cd670
[   12.415012] iwlwifi 0000:01:00.0: Timeout waiting for PNVM load!
[   12.415023] iwlwifi 0000:01:00.0: Failed to start RT ucode: -110
[   12.415028] iwlwifi 0000:01:00.0: iwl_trans_send_cmd bad state = 1
[   12.619047] iwlwifi 0000:01:00.0: firmware didn't ACK the reset - continue anyway
[   12.631122] iwlwifi 0000:01:00.0: Failed to run INIT ucode: -110
```

With the proposed kernel version (linux-image-5.13.0-12), it's OK :
```
[   12.057875] iwlwifi 0000:01:00.0: api flags index 2 larger than supported by driver
[   12.057903] iwlwifi 0000:01:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 0.0.2.25
[   12.058410] iwlwifi 0000:01:00.0: loaded firmware version 63.c04f3485.0 ty-a0-gf-a0-63.ucode op_mode iwlmvm
[   12.141243] iwlwifi 0000:01:00.0: Detected Intel(R) Wi-Fi 6 AX210 160MHz, REV=0x420
[   12.292104] iwlwifi 0000:01:00.0: loaded PNVM version 0x324cd670
[   12.378425] iwlwifi 0000:01:00.0: base HW address: xx:xx:xx:xx:xx:xx
[   12.411959] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0

```

---

### Post by VMC on 2021-07-18
Most likely its in the "/lib/firmware" folder.

---

### Post by mohegan on 2021-07-18
For playing videos, gstreamer1.0-plugins-bad is missing ! It is necessary to install it manually to watch x264 or x265.

---

