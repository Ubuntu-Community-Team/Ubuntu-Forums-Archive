---
title: "Ubuntu 22.10 is the “Kinetic Kudu”"
date: 2022-04-25
forum: Ubuntu Development Version
---

### Post by osse7 on 2022-04-25
Repos should be filled on next 28th

[https://www.omgubuntu.co.uk/2022/04/ubuntu-22-10-codename-is-kinetic-kudu](https://www.omgubuntu.co.uk/2022/04/ubuntu-22-10-codename-is-kinetic-kudu)

---

### Post by este.el.paz on 2022-04-25
> **osse7 said:**
> Repos should be filled on next 28th

[https://www.omgubuntu.co.uk/2022/04/ubuntu-22-10-codename-is-kinetic-kudu](https://www.omgubuntu.co.uk/2022/04/ubuntu-22-10-codename-is-kinetic-kudu)


Alrighty then . . . does that mean "three days hence" or "next" means, next month's 28th??  When will I be changing my sources.list to "kinetic"??

I was hoping it would have been "krazy kudu" . . . ????  Easier to type "krazy" than  'kinetic"

---

### Post by vicshrike on 2022-04-25
Kinetic release schedule here.

[https://discourse.ubuntu.com/t/kinetic-kudu-release-schedule/27263](https://discourse.ubuntu.com/t/kinetic-kudu-release-schedule/27263)

---

### Post by este.el.paz on 2022-04-26
> **vicshrike said:**
> Kinetic release schedule here.

[https://discourse.ubuntu.com/t/kinetic-kudu-release-schedule/27263](https://discourse.ubuntu.com/t/kinetic-kudu-release-schedule/27263)

@vicshrike:

Thanks for posting that . . . .

---

### Post by zebra2 on 2022-04-26
```

Zebra1@zebra1-320-15IAP:~$ inxi1
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Kinetic Kudu (development branch)
Release:    22.10
Codename:    kinetic
inxi -Sxx
System:
  Host: zebra1-320-15IAP Kernel: 5.15.0-27-generic x86_64 bits: 64
    compiler: gcc v: 11.2.0 Desktop: GNOME 42.0 tk: GTK 3.24.33 wm: gnome-shell
    dm: GDM3 Distro: Ubuntu 22.10 (Kinetic Kudu)
$DESKTOP_SESSION
ubuntu
$XDG_SESSION_TYPE
wayland
GNOME Shell 42.0
Version: 42.0-2ubuntu1
loginctl type
Type=wayland

zebra1@zebra1-320-15IAP:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Kinetic Kudu (development branch)
Release:	22.10
Codename:	kinetic



```

---

### Post by grahammechanical on 2022-04-26
An hour or two ago I changed my jammy repositories for kinetic repositories. There were no updates available. So, I guess that the repositories have been setup but they are filled with the latest jammy packages. I expect that to change over the next few days.

Regards

---

### Post by guiverc on 2022-04-26
> **grahammechanical said:**
> An hour or two ago I changed my jammy repositories for kinetic repositories. There were no updates available. So, I guess that the repositories have been setup but they are filled with the latest jammy packages. I expect that to change over the next few days.

I did the same last night; disabling `partner` (for *kinetic*) as I got errors for that and my system too still reports as *jammy* not *kinetic*.  The package `base-files` I see in *kinetic* looks identical to *jammy* thus no new name yet for me either.

Different result to @zebra2

I'm not worried though, name change is neither *'here or there*' .  

Kinetic hasn't been setup yet on [packages.ubuntu.com]("https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=base-files") nor `rmadison` which makes exploring easier.

[https://changelogs.ubuntu.com/changelogs/pool/main/b/base-files/base-files_12ubuntu4/changelog](https://changelogs.ubuntu.com/changelogs/pool/main/b/base-files/base-files_12ubuntu4/changelog)

*I do see a later package in jammy-proposed (via `rmadison`); but not using jammy anymore.  It maybe there in kinectic-proposed too alas rmadison isn't showing kinectic yet.*

---

### Post by zebra2 on 2022-04-27
I have used every dev version as my primary system since Karmic. 

```

zebra1@zebra1-320-15IAP:~$ cat /etc/os-release
PRETTY_NAME="Ubuntu Kinetic Kudu (development branch)"
NAME="Ubuntu"
VERSION_ID="22.10"
VERSION="22.10 (Kinetic Kudu)"
VERSION_CODENAME=kinetic
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=kinetic
zebra1@zebra1-320-15IAP:~$ hostnamectl
 Static hostname: zebra1-320-15IAP
       Icon name: computer-laptop
         Chassis: laptop
      Machine ID: 7674afcc424b4523ae7680afc8b572ef
         Boot ID: 189067774e3444aa9dec7c66c7808c0d
Operating System: Ubuntu Kinetic Kudu (development branch)
          Kernel: Linux 5.15.0-27-generic
    Architecture: x86-64
 Hardware Vendor: Lenovo
  Hardware Model: Lenovo ideapad 320-15IAP

```

---

### Post by zebra2 on 2022-04-27
Because of Grub changes I re-partitioned my drive and installed a fresh Jammy. Then fully updated with proposed enabled prior to the Kinetic upgrade.  

then

sudo sed -i 's/jammy/kinetic/g' /etc/apt/sources.list
sudo sed -i 's/jammy/kinetic/g' /usr/share/python-apt/templates/Ubuntu.info
sudo apt-get update
sudo apt-get upgrade
sudo reboot

PS wouldn't hurt for you Moderators to update the Header in this section to reflect the current dev version "Karmic".  Time marches on!

---

### Post by IanW on 2022-04-27
> **grahammechanical said:**
> An hour or two ago I changed my jammy repositories for kinetic repositories. There were no updates available. So, I guess that the repositories have been setup but they are filled with the latest jammy packages. I expect that to change over the next few days.

Regards

> **guiverc said:**
> I did the same last night; disabling `partner` (for *kinetic*) as I got errors for that and my system too still reports as *jammy* not *kinetic*.  The package `base-files` I see in *kinetic* looks identical to *jammy* thus no new name yet for me either.

Different result to @zebra2

I'm not worried though, name change is neither *'here or there*' .  

Kinetic hasn't been setup yet on [packages.ubuntu.com]("https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=base-files") nor `rmadison` which makes exploring easier.

[https://changelogs.ubuntu.com/changelogs/pool/main/b/base-files/base-files_12ubuntu4/changelog](https://changelogs.ubuntu.com/changelogs/pool/main/b/base-files/base-files_12ubuntu4/changelog)

*I do see a later package in jammy-proposed (via `rmadison`); but not using jammy anymore.  It maybe there in kinectic-proposed too alas rmadison isn't showing kinectic yet.*


Guys, the schedule says that the toolchain won't be loaded onto Kinetic until _tomorrow_ (April 28th)

---

### Post by zebra2 on 2022-04-27
Forgot to mention, the kinetic base files came in yesterday with my upgrade to kinetic. . 

```

zebra1@zebra1-320-15IAP:~$ dpkg -l base-files
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-==================================>
ii  base-files     12ubuntu5    amd64        Debian base system miscellaneous files>

```

---

### Post by grahammechanical on 2022-04-27
> Guys, the schedule says that the toolchain won't be loaded onto Kinetic until _tomorrow_ (April 28th) 				

True, but some of us like to get in as early as we can and watch how things develop.

Regards

---

### Post by zebra2 on 2022-04-27
> **grahammechanical said:**
> True, but some of us like to get in as early as we can and watch how things develop.

Regards

Yes, and in addition many of us don't need the compilers in the first place.   That being said, I have had early starts, start with a bigger bang than this one.  I had to redo my partition anyway so not a problem to do the upgrade.

---

### Post by jbicha on 2022-04-28
> **IanW said:**
> Guys, the schedule says that the toolchain won't be loaded onto Kinetic until _tomorrow_ (April 28th)

That's not a precise date. All it's saying is that in the first week of Ubuntu development, there are some initial uploads for compilers, base-files, debootstrap, distro-info-data, etc.

For an example of what that looks like, you can check out the [earliest uploads for 21.10]("https://lists.ubuntu.com/archives/impish-changes/2021-April/").

But you were right and the archive did open for general uploads today, April 28.

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2022-April/001313.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2022-April/001313.html)

---

### Post by Bashing-om on 2022-04-28
Guys - Yup ^

See: [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2022-April/001313.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2022-April/001313.html)
The call is out for testing and "drown Proofing" :D

\o/

---

### Post by zebra2 on 2022-04-28
Thank you Jeremy and everyone else in this thread.

Whoops!
Here we go again. 
Game on!

---

