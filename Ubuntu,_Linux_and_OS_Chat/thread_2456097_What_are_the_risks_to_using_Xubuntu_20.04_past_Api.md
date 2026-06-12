---
title: "What are the risks to using Xubuntu 20.04 past Apirl 2023?"
date: 2021-01-04
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2021-01-04
I'm maintaining my grandpa's laptop, it's a Dell Inspiron E1505 64-bit, which came preinstalled with Windows XP, and it has 2GB RAM. In 2015, the laptop was hit with a virus, so I installed Xubuntu 14.04 on it, and have been maintaining his laptop for him ever since, every 3 years I'd do a fresh install of Xubuntu, and just recently, I upgraded him to Xubuntu 20.04.

My grandpa mainly uses his laptop for Facebook, email, YouTube, and he video chats using Facebook.

Here's my problem, I'm going overseas for my job and I might not be back by the time the next LTS upgrade, so I won't be able to upgrade my grandpa's laptop like I did before. I've considered remotely upgrading his laptop, but in my experience, I've tried to upgrade his laptop through the upgrade button before, but  it didn't turn out well, so I've always done his upgrading through fresh  installs with liveUSB, so my problem is I won't be there to do it. My grandpa isn't tech-savvy enough to create a liveUSB on his on and install it, even if I tried talking through the process, and none of my family members and friends are tech-savvy enough either to create liveUSB and install, so I can't count on them to upgrade his laptop, and the computer repair in my area aren't familiar with Linux, only Windows. I'm not sure if installing Windows 10 will work on a laptop this old, and besides, due to the bad experience of a virus hitting his laptop, he prefers Linux over Windows, he told me as such.

Since I won't be around to upgrade him to the latest LTS version, can my grandpa continue to use his laptop with Xubuntu after Apirl 2023? What are the risks?

---

### Post by CatKiller on 2021-01-04
The flavours all use exactly the same repositories, so the parts that are common to the main distro (kernel, browsers, command line utilities, and so on) will get exactly the same security and bug fixes. So that part is fine.

The teams that maintain the flavours are much smaller than the main team, though, so they don't have the resources to maintain five releases all at once, so the support period for the parts that are specific to their flavour are shorter. So if, in 2024, some critical flaw is found in Xfce's file browser, or text editor, or window manager, or whatever, the fix won't be backported to your grandad's laptop.

Having said that, 2 GB RAM is pretty small already with how hungry websites are. A new laptop with more RAM and 22.04 already installed might be just the ticket when the time comes.

---

### Post by linuxyogi on 2021-01-04
IMHO this the only area where Linux Mint is superior. All of their spins namely Cinnamon, Mate & XFCE are supported for full 5 years. So one might ask why am I using Lubuntu & not Mint. Well coz I am "addicted" to Lubuntu. I know it sounds stupid but that's a fact.

---

### Post by bernard010 on 2021-01-04
My self I would get the new Lubuntu 21.04 that will be released on 04-22-2021 Especially due to it's very low hardware requirements. With 2GB memory it will run fast.

---

### Post by grahammechanical on 2021-01-04
I am 72 years old and it is true that I have been using Ubuntu since 2007. But I say this: Do not write off the older generation so easily. We oldies can learn new things. In fact we need to if we are to maintain our ability to think.

Show your grandfather how to download an ISO image and burn it to USB stick. Let him write down for himself the procedure. Then walk through with him an actual install. Again let him document the process. Show him where to find official and community documentation.

If the machine has enough hard disc space then show him how to dual boot with another install of Xubuntu and let him gain experience of upgrading the second install. You could start with 14.04. Then upgrade to 18.04 and then to 20.04. From then onwards he can upgrade this second install to 20.10: 21.04: 21.10: 22.04 and so on. If the installation is kept in a default state the upgrade should work. He will always have an up to date OS he can use. He can then upgrade the first install to 22.04 and have the second install to use should the upgrade break something.

Also, introduce him to Ubuntu Forums where he can learn about Linux and ask for help if needed.

Regards

---

### Post by ajgreeny on 2021-01-04
To answer your actual question, which so far everybody has avoided, you will need to consider how much, or which packages, of Xubuntu 20.04 will be unsupported after April 2023.
The large majority of the packages that make up Xubuntu will remain fully supported as they are the base packages that are common to all the Ubuntu family of OSs.

Only the xfce4 xubuntu packages will be unsupported after that time, and there is a command which I am having trouble finding at present that allows you to list the unsupported packages. I will search for that command and post it here once I find it.

So whilst I will never suggest that you can continue to use Xubuntu 20.04 risk free after April 2023, you alone can either accept, or not, the risk of continuing its use with those relatively few unsupported packages.  My gut feeling is that the risks, though most definitely present, will be fairly small, though please wait for other users comments before you make up your mind.

EDIT:
The command to show package support status is
ubuntu-security-status

usage: ***ubuntu-security-status***  with one of these three options
--help 
--thirdparty 
--unavailable

will show information about security support for packages.

---

### Post by TheFu on 2021-01-04
```
sudo ubuntu-support-status
```

ajgreeny nailed it. Don't install any non-LTS release.
I did an ssh remote lts-to-lts upgrade for my mother from 10.04 to 12.04 lubuntu, but I did this the day before I planed a trip to visit her.  
[LIST=1]
[*]make backup
[*]sudo apt update
[*]sudo apt full-uprade
[*]sudo reboot
[*]sudo do-release-upgrade
[/LIST]
It was fine, which surprised me. She only used programs from the canonical repos. No PPAs ad no manually installed .deb files.

Linux Mint isn't a bad choice either, though  wonder about the real ability to provide supprt for older DEs.

---

### Post by ajgreeny on 2021-01-04
> **TheFu said:**
> ```
sudo ubuntu-support-status
```

ajgreeny nailed it. Don't install any non-LTS release.
I did an ssh remote lts-to-lts upgrade for my mother from 10.04 to 12.04 lubuntu, but I did this the day before I planed a trip to visit her.  
[LIST=1]
[*]make backup
[*]sudo apt update
[*]sudo apt full-uprade
[*]sudo reboot
[*]sudo do-release-upgrade
[/LIST]
It was fine, which surprised me. She only used programs from the canonical repos. No PPAs ad no manually installed .deb files.

Linux Mint isn't a bad choice either, though  wonder about the real ability to provide supprt for older DEs.
That command which I also believed was the one to use, has now been replaced by ```
ubuntu-security-status [option]
```

I have edited my post above with the details; I hope it is helpful.

---

### Post by TheFu on 2021-01-04
So it has in 20.04:
```
$ ubuntu-security-status 
2201 packages installed, of which:
1648 receive package updates with LTS until 4/2025
 538 could receive security updates with ESM Apps until 4/2030
   5 packages are from third parties
  10 packages are no longer available for download
```And the new command doesn't need sudo.

---

### Post by ardouronerous on 2021-01-04
> **grahammechanical said:**
> I am 72 years old and it is true that I have been using Ubuntu since 2007. But I say this: Do not write off the older generation so easily. We oldies can learn new things. In fact we need to if we are to maintain our ability to think.

Show your grandfather how to download an ISO image and burn it to USB stick. Let him write down for himself the procedure. Then walk through with him an actual install. Again let him document the process. Show him where to find official and community documentation.

If the machine has enough hard disc space then show him how to dual boot with another install of Xubuntu and let him gain experience of upgrading the second install. You could start with 14.04. Then upgrade to 18.04 and then to 20.04. From then onwards he can upgrade this second install to 20.10: 21.04: 21.10: 22.04 and so on. If the installation is kept in a default state the upgrade should work. He will always have an up to date OS he can use. He can then upgrade the first install to 22.04 and have the second install to use should the upgrade break something.

Also, introduce him to Ubuntu Forums where he can learn about Linux and ask for help if needed.

Regards

Actually, one of the main issues with installing it himself is his eyesight, even with his prescribed eyeglasses on, his eyesight is poor, so a freshly installed Xubuntu wouldn't be usable for him, so I do a lot of tweaking after a fresh install, like enlarging the fonts for him on the system and on Firefox. So I can imagine him installing through the install process with the fonts as small as they are and the post install tweaking will be equally hard.

> **ajgreeny said:**
> To answer your actual question, which so far  everybody has avoided, you will need to consider how much, or which  packages, of Xubuntu 20.04 will be unsupported after April 2023.
The large majority of the packages that make up Xubuntu will remain  fully supported as they are the base packages that are common to all the  Ubuntu family of OSs.

Only the xfce4 xubuntu packages will be unsupported after that time, and  there is a command which I am having trouble finding at present that  allows you to list the unsupported packages. I will search for that  command and post it here once I find it.

So whilst I will never suggest that you can continue to use Xubuntu  20.04 risk free after April 2023, you alone can either accept, or not,  the risk of continuing its use with those relatively few unsupported  packages.  My gut feeling is that the risks, though most definitely  present, will be fairly small, though please wait for other users  comments before you make up your mind.

EDIT:
The command to show package support status is
ubuntu-security-status

usage: ***ubuntu-security-status***  with one of these three options
--help 
--thirdparty 
--unavailable

will show information about security support for packages.

Since my grandpa and I are using Xubuntu 20.04, here's the results:

```
ubuntu-security-status
1931 packages installed, of which:
1452 receive package updates with LTS until 4/2025
 478 could receive security updates with ESM Apps until 4/2030
   1 package is from a third party

Packages from third parties are not provided by the official Ubuntu
archive, for example packages from Personal Package Archives in
Launchpad.
For more information on the packages, run 'ubuntu-security-status
--thirdparty'.

Enable Extended Security Maintenance (ESM Apps) to get 1 security
update (so far) and enable coverage of 478 packages.

This machine is not attached to an Ubuntu Advantage subscription.
See https://ubuntu.com/advantage
```

> **TheFu said:**
> ```
sudo ubuntu-support-status
```

ajgreeny nailed it. Don't install any non-LTS release.
I did an ssh remote lts-to-lts upgrade for my mother from 10.04 to 12.04  lubuntu, but I did this the day before I planed a trip to visit her.  
[LIST=1]
[*]make backup
[*]sudo apt update
[*]sudo apt full-uprade
[*]sudo reboot
[*]sudo do-release-upgrade
[/LIST]
It was fine, which surprised me. She only used programs from the canonical repos. No PPAs ad no manually installed .deb files.

Linux Mint isn't a bad choice either, though  wonder about the real ability to provide supprt for older DEs.

Unfortunately in my experience, a remote upgrade doesn't work and is pretty risky since I wont be there to fix the issues if it arises.

I heard that Linux Mint XFCE is heavier than Xubuntu though.

---

### Post by TheFu on 2021-01-04
Worste case, he should know how to create an Xbuntu "live installer" flash drive.
And know how to boot, then run using that for emergency reasons.  HDD and SSD fail every day.

You can setup remote access via ssh and x2go.
Who is patching the home router?  That needs to happen monthly too.

---

### Post by ajgreeny on 2021-01-04
From what I've seen of Mint Xfce it is not any heavier than Xubuntu, though my install is a VM using QEMU/KVM so may not be a good comparrison.
For your peace of mind it may still be a worthy proposition bsfore you leave, as it will, as you say, be supported until 2025.
You may find that your current configurations for Xubuntu still work in Mint Xfce.

---

