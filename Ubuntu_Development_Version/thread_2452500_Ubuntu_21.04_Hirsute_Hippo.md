---
title: "Ubuntu 21.04 Hirsute Hippo"
date: 2020-10-23
forum: Ubuntu Development Version
---

### Post by corradoventu on 2020-10-23
[https://launchpad.net/ubuntu/hirsute](https://launchpad.net/ubuntu/hirsute)

---

### Post by dino99 on 2020-10-24
Welcome to Hirsute Hanimal

[https://www.yourdictionary.com/hanimal](https://www.yourdictionary.com/hanimal)

---

### Post by zika on 2020-10-26
From a couple a days ago
/etc/os-release:```

NAME="Ubuntu"
VERSION="21.04 (Hirsute Hanimal)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu Hirsute Hanimal (development branch)"
VERSION_ID="21.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=hirsute
UBUNTU_CODENAME=hirsute

```

---

### Post by zebra2 on 2020-10-26
```

Distributor ID:    Ubuntu
Description:    Ubuntu Hirsute Hanimal (development branch)
Release:    21.04
Codename:    hirsute

System:
  Host: zebra1-Lenovo-320-15IAP Kernel: 5.8.0-26-generic x86_64 bits: 64 
  
compiler: gcc v: 10.2.0 Desktop: N/A wm: gnome-shell dm: GDM3 
  Distro: Ubuntu 21.04 (Hirsute Hanimal) 

$DESKTOP_SESSION
ubuntu-wayland

$XDG_SESSION_TYPE
wayland

GNOME Shell 3.38.1
Version: 3.38.1-1ubuntu1
loginctl type
Type=wayland

```

---

### Post by mc4man on 2020-10-27
Maybe ubuntu wants to now champion homeless illiterates

---

### Post by zebra2 on 2020-10-27
> **mc4man said:**
> Maybe ubuntu wants to now champion homeless illiterates


It's actually homeless hilliterates if we are following the HH theme here.
FYI

---

### Post by IanW on 2020-10-28
Looks to be "Hirsute Hippo", according to Ubuntu desktop lead Martim Wimpress:-

[https://twitter.com/m_wimpress/status/1321422316568535043](https://twitter.com/m_wimpress/status/1321422316568535043)

---

### Post by dino99 on 2020-10-28
Final naming and schedule  [https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-21.04-Hirsute-Hippo](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-21.04-Hirsute-Hippo)

distro-info-data (0.44ubuntu3) hirsute; urgency=medium

  * Add Ubuntu 21.04, Hirsute Hippo (LP: #1901361).

---

### Post by zika on 2020-10-28
Shame on You... ;)
```
:~$ cat /etc/os-release NAME="Ubuntu"
VERSION="21.04 (Hirsute Hippo)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu Hirsute Hippo (development branch)"
VERSION_ID="21.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=hirsute
UBUNTU_CODENAME=hirsute

```

---

### Post by P-I H on 2020-10-30
Hirute Hippo

---

### Post by ubername on 2020-10-30
I seem to recall a sed command to run on sources.list to simply upgrade repo's to the next generatio. can anyone remind me of it, (Particularly for groovy to hirsute) or have things moved on?

---

### Post by deadflowr on 2020-10-30
> **ubername said:**
> I seem to recall a sed command to run on sources.list to simply upgrade repo's to the next generatio. can anyone remind me of it, (Particularly for groovy to hirsute) or have things moved on?

You can do 
```
sudo sed -i 's/old/new/g' /etc/apt/sources.list
```
Replace old with the old release name and replace new with whatever the new release name is.

Optionally
You can also use  rolling rhino to set it always be the development release:
[https://github.com/wimpysworld/rolling-rhino]("https://github.com/wimpysworld/rolling-rhino")

---

### Post by P-I H on 2020-10-30
I did
sudo sed -i 's/groovy/hirsute/g' /etc/apt/sources.list

---

### Post by ubername on 2020-10-31
> **deadflowr said:**
> You can do 
```
sudo sed -i 's/old/new/g' /etc/apt/sources.list
```
Replace old with the old release name and replace new with whatever the new release name is.

Optionally
You can also use  rolling rhino to set it always be the development release:
[https://github.com/wimpysworld/rolling-rhino]("https://github.com/wimpysworld/rolling-rhino")

Thank you! This is my blue moon day!

---

### Post by grahammechanical on 2020-11-03
Grub is showing hirsute Hanimal. Someone is mocking my cockney pronunciation. Dropping the aitch and then adding an Hasperate.  An update-grub might bring in the change

Regards

---

### Post by sudodus on 2020-11-03
I discovered that there is a Lubuntu Hirsute Hippo iso file available via the [iso testing tracker](http://iso.qa.ubuntu.com/qatracker/milestones/419/builds/222477/testcases) now. I tested it live, and it works :-)

---

### Post by corradoventu on 2020-11-04
New ISO: [http://cdimages.ubuntu.com/daily-live/pending/](http://cdimages.ubuntu.com/daily-live/pending/)
```
corrado@corrado-x2-hh-1104:~$ sudo inxi -SMCx
System:
  Host: corrado-x2-hh-1104 Kernel: 5.8.0-25-generic x86_64 bits: 64 
  compiler: gcc v: 10.2.0 Desktop: GNOME 3.38.1 
  Distro: Ubuntu 21.04 (Hirsute Hippo) 
Machine:
  Type: Desktop Mobo: ASRock model: H110M-G/M.2 serial: M80-A5001202208 
  UEFI: American Megatrends v: P1.10 date: 05/11/2017 
CPU:
  Info: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP 
  arch: Kaby Lake rev: 9 L2 cache: 3072 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 31199 
  Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 4: 800 
corrado@corrado-x2-hh-1104:~$ 

```

---

### Post by P-I H on 2020-11-04
Tried it. Works OK. but there are some problems listed in Logs.
There is a fix for the SSSD problem in this thread
[https://ubuntuforums.org/showthread.php?t=2452209](https://ubuntuforums.org/showthread.php?t=2452209)
No delay when starting Chromium, but it takes about 7 sec to start Ubuntu Software.
I have to use alsamixer to enable S/PDIF to get the sound working. I'm using an ASUS D2X sound card connected with to a receiver with SPDIF.

---

### Post by lammert-nijhof on 2020-11-11
[ATTACH=CONFIG]287340[/ATTACH]

Hirsute Hippo running full screen in Virtualbox, while running itself Ubuntu 14.04 LTS in QEMU/KVM. Note that the VBox shared folder is accessible in my Host Ubuntu 20.04; Ubuntu 21.04 and through QEMU shared folders also in Ubuntu 14.04. You only have to add the system user libvirt-qemu to the vboxsf group in Hirsute Hippo: "sudo usermod -a -G vboxsf libvirt-qemu" :)

I'm using Virtualbox for more than 10 years and my oldest VM is Windows XP from Dec 2010. I know QEMU/KVM is faster with its disk IO than Virtualbox, but the user interface is more primitive and not every setting works. I decided to keep an eye on the development of QEMU/KVM, So I started to try-out QEMU/KVM in Virtualbox. You need VMs to try-out QEMU/KVM. For that I used systems, that were not updated any more, like Ubuntu 14.04 and Windows Vista :)


[ATTACH=CONFIG]287341[/ATTACH]

See all three levels in one screen 
- Host: Ubuntu 20.04 on ZFS; 
- Virtualbox VM: Ubuntu 21.04 Hirsute Hippo and 
- QEMU/KVM VM: Ubuntu 14.04.
Due to pulse-audio, I can play the shared music files on all three levels. Only disadvantage: The Ryzen 3 2200G is somewhat stressed, because it runs at 52% CPU load playing music in Ubuntu 14.04.

So far, Hirsute Hippo works perfectly, also in this crazy configuration, sandwiched between 20.04 and 14.04.

---

### Post by Frogs Hair on 2020-11-11
Put a hair suit on ! :)
```
OS: Ubuntu Budgie Hirsute Hippo (dev 
Host: N68SA-M2S 
Kernel: 5.8.0-26-generic 
Uptime: 1 hour, 3 mins 
Packages: 2074 (dpkg), 6 (flatpak),  
Shell: bash 5.0.17 
Resolution: 1680x1050 
DE: Budgie 10.5.1 
WM: Mutter(Budgie) 
Theme: Arc-Black-Steel-3.36 [GTK2/3] 
Icons: korla-pgrey [GTK2/3] 
Terminal: tilix 
CPU: AMD Athlon II X4 645 (4) @ 3.10 
GPU: NVIDIA GeForce GT 730 
Memory: 1811MiB / 3931MiB 
```

---

### Post by ajgreeny on 2020-11-19
I have been running a KVM virtual install of Groovy, 20.10 for a while now and just as an experiment I have just upgraded to 21.04 by manually editing /etc/apt/sources.list.

The upgrade went with, so far, no hiccups or problems at all that I can see.  Time will tell but looking good so far!

---

