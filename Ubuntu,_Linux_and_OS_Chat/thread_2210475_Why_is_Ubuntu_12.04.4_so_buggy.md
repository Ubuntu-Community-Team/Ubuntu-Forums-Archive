---
title: "Why is Ubuntu 12.04.4 so buggy?"
date: 2014-03-11
forum: Ubuntu, Linux and OS Chat
---

### Post by xinghua31 on 2014-03-11
I'm having quite a few issues with Ubuntu 12.04.4 that I didn't experience with previous version of Precise. 

I've tried to install the 32 Bit version 4 times, but I'm met with 2 very large issues. The UEFI installer doesn't work, and selecting it resets my PC for some reason. If I use the non-UEFI installer and use nomodeset to bypass the blackscreen I get otherwise, I'm still left with an unbootable system, even when I've selected the 3rd party drivers (AMD CCC) option from the installer. All it boots to is a black screen showing 'Checking battery state'. Using CTRL+ALT+the F* keys also has no effect.

On the 64 Bit side, I'm having issues with Unity. Again, I've tried installing multiple times, using a differently downloaded ISO each time. 
Issue 1 is the close/minimise/maximise buttons will randomly not show up when a maximised program is running in Unity. The menubar is still there and everything, just no buttons..
Issue 2 is the fact that opened programs will randomly not show up in the Unity launcher/dock, meaning that if you minimise them without releasing the bug has happened, they go into oblivion. This is pretty easy to workaround by dragging all programs from the Unity menu into the dock, but it's still annoying.

Why has this happened? How did such a buggy release get the ok to ship? :/

---

### Post by deadflowr on 2014-03-11
If 12.04.4 is causing installation problems, but versions 12.04.3 and older don't, then why not download and install from the older releases.
You can get the all here
[http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)

scroll down to the list section, you would want one that says desktop, and iso.
(example
Ubuntu-12.04-desktop-amd64.iso

---

### Post by Bucky Ball on 2014-03-11
If you want support for your existing problems please post separate threads with descriptive titles for each problem. You are asking three (or more) questions here and the thread title only refers to one of them. 

A generic thread title like 'Why is 12.04.4 so buggy?' will not get you much help with your actual issues. That title indicates a thread that should be in this section of the forum, but this is not a support section. While you should feel free to discuss why 12.04.4 is so buggy here, don't expect too much actual support regarding fixing your issues. Good luck.

---

### Post by buzzingrobot on 2014-03-11
The third-party software option in the installer does not install video drivers. That can be done via the "Additional Drivers" facility after installation.

When you create your other threads, don't forget to include details of your hardware and the details of any error messages, preferably the exact wording.

---

### Post by Bucky Ball on 2014-03-11
> **buzzingrobot said:**
> 
When you create your other threads, don't forget to include details of your hardware and the details of any error messages, preferably the exact wording.

Indeed. And you might want to have a scan of the third link in my signature prior to posting them, too. Good luck.

---

### Post by grahammechanical on 2014-03-12
> [COLOR=#333333][FONT=Ubuntu]To install Ubuntu in EFI mode:[/FONT][/COLOR]

[LIST]
[*=left][FONT=inherit]_Use a 64bit disk of Ubuntu _([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555"))[/FONT]
[*=left][FONT=inherit]Use a supported version of Ubuntu. Support for UEFI appeared in 11.10, but has become more reliable in next versions. Support for UEFI[SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2.[/FONT]
[*=left][FONT=inherit]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in EFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below)[/FONT]
[*=left]Then:
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I never install Ubuntu and tick "Install third party software." On versions other than 12.04 it brings in a proprietary video driver and that driver can break the first reboot. My advice? Never tick to install third part software. Then the reboot will use Nouveau the open source video driver. We can install Ubuntu Restricted Extras after installation and also experiment with video drivers as well. And yes, I do mean experiment.

Regards.

---

