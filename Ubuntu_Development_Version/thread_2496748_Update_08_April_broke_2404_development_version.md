---
title: "Update 08 April broke 2404 development version"
date: 2024-04-10
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2024-04-10
I updated the 24.04 development version on 08 April. Lots of packages were held back but many packages we were updated. On rebooting I got a white screen with this message:

> Oh No! Something has gone wrong. A problem occurred and the system cannot recover. Please contact a system administrator.

The only thing that can be done at this point is a hard reboot. I have run the development version for many years and this is the first time in a long time that the development version has broken to the extent that the desktop does not load.

I also have 20.04.6 and 22.04.4 installed so I get a Grub boot menu. I can access Advanced options for Ubuntu. This problem happens with both Linux 6.8.0-11 and Linux 6.6.0-14 kernels.

Choosing the recovery mode kernel seems to show Linux loading and the usual recovery menu is displayed. The error happens also if I chose recovery mode>resume.

I am able to use recovery menu >Root to update and upgrade. On 09 April there were no packages to download. On 10 April the only update was Linux firmware. I expect that over the next few days as the many held back packages are released this problem will be fixed.

The machine has Intel UHD graphics. It uses the Mesa open source video driver. It may have been an update to the Mesa driver that has caused this problem. Certainly, the mesa range of drivers are part of all those packages being held back.

Such is life.

Regards

---

### Post by ajgreeny on 2024-04-10
When was the previous update to that 24.04 system? When did you actually install the system?

There have been major problems for the past couple of weeks with many packages being removed by the **apt upgrade** process making the system fairly useless, so unless you have not run an upgrade for the past two weeks or thereabouts, I'm very surprised that you have not seen this before.

All seems to have improved now and having just installed today's pending iso of Xubuntu all was installing and working very well.

I use only virtual machine installs in KVM so if there are major difficulties or problems I just delete the VM and start again.
For about a week or more before the eventual release of a new iso on the 6th or 7th March there was a total lack of new iso files to try but, as I say, all seems good again now so I suggest you reinstall with the most recent isi when you get a chance?

---

### Post by corradoventu on 2024-04-11
For me problem was solved just with full-upgrade

---

### Post by grahammechanical on 2024-04-18
I am sorry that I have not replied sooner. I do not use the internet every day. I also had breakage on the Ubuntu 20.04.6 install caused by my failure to pay attention to what I was doing.

@corradoventu

Your solution worked. It brought in hundreds of packages that were held back but at the end the install booted to a login screen and desktop. There was breakage.

Gnome Files was removed. The Android emulator Waydroid also was removed along with the Android app that I run in it. On the positive side Wine was updated and the Windows app I use Wine for still works.

The Ubuntu gnome extension that puts the home folder icon on the desktop at the bottom right must be disabled or missing because that icon is no longer on the desktop.

A few months ago an update brought in a new Ubuntu utility called Firmware Updater. That is also missing. Perhaps it is not meant to be part of a default install but as something available to install.

Thunderbird has transitioned from a deb package to a snap package. It works as it should. Those doing an online upgrade from 22.04 LTS to 24.04 LTS should be aware that this change will happen.

And so we live.

Regards

---

### Post by jbicha on 2024-04-21
I recommend you do a reinstall. It is easier than trying to manually fix missing details especially since you probably aren't aware of all the details you are missing.

---

### Post by grahammechanical on 2024-04-22
I like to run the development version and set it up the way I like to see how things work out before I upgrade. It was my original intention to switch from 20.04 LTS to 22.04 LTS but a Windows app that I run in Wine refuses to run. It works fine in 20.04 LTS and in 23.10 moving on into 24.04 development version.

So, I changed my plans. I have activated Ubuntu Pro for 20.04 LTS. I now intend to replace 22.04 LTS with 24.04 LTS when it is released. Then I will either convert 24.04 development version into 24.20 development version or reinstall 24.04 LTS over 24.04 development version and then convert a clean 24.04 into the 24.10 development version and try again to set things up the way I like it.

This the first time in years that I have experienced the development version breaking in such a spectacular fashion. It all adds to the fun.

Regards

---

### Post by Claus7 on 2024-04-22
Hello,

from what you mention I get the idea that in the end your upgrade worked even if there were some tweaks here and there. I'm asking because I'm really interested if, even though this LTS development cycle may have been one of the most demanding ones, in the end the gradual upgrading just worked.

Regards!

---

### Post by Claus7 on 2024-05-02
Hello,

a big issue during the upgrade process, at least from mantic to noble is a non ending thunderbird loop. This is a known issue to developers, which is supposed to get fixed when 24.04.1 is released.

In order to bypass the issue either remove completely thunderbird prior to the upgrade or tamper with thunderbird during the upgrade. The following commands will be in the right direction: 
sudo snap remove --purge thunderbird
sudo apt purge thunderbird
sudo apt install thunderbird

In order to avoid the loop, thunderbird should be installed first and then purged if not needed.

Regards!

---

