---
title: "loading Ubuntu OS"
date: 2013-03-18
forum: Ubuntu Development Version
---

### Post by dozoclown on 2013-03-18
Is there a program that would load Ubuntu with one click? I have problems with 13.04. I have tried to make a DVD and USB thumb drive. I can creat both but neither one works. I like Ubuntu except for getting loaded. I have a laptop running 12.10 and a desktop running 10.04. I don't have a clear understanding to why I have to creat a disk. It seems there is something easy that I'm doing wrong.

---

### Post by @tomic on 2013-03-18
Firstly, unless you are experienced with Ubuntu, I would not recommend that you use 13.04 as it hasn't been released yet. Rather stick with stable installations, as they are less likely to give you problems.

Can you describe the nature of the problem with booting to USB or CD. Are you able to successfully write?
I would recommend that you use unetbootin to create a flash disk:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Also I would recommend you format it first to fat32.

Also, make sure your bios enables you to boot to USB first.

As far as I know, there is no one-click to install Ubuntu, as it is a full operating system, and can't be run as an app from within windows.

What you could try is to download Virtualbox and install it as a Virtual Machine.

---

### Post by alphacrucis2 on 2013-03-18
You could update 12.10 to 13.04 in place via 

```
sudo do-release-upgrade -d
```

The -d tells it to consider dev releases which 13.04 still is at this point. Be warned it will take quite a while as all your installed packages will get upgraded. Remember that 13.04 is intended for testing purposes only until it is officially released.

10.04 can be upgraded in place to 12.04 (LTS to LTS) using the GUI update manager and you probably want to do it before 10.04 desktop support runs out in April.

---

### Post by dozoclown on 2013-03-18
when I click on the wubi.exe icon I get an error message from the archive manager.

---

### Post by #1udancqSHv% on 2013-03-18
Hi dozoclown - are you having problems getting Ubuntu to boot at all? Is the PC you're trying to install on quite new? Came with Windows 8? If so, it might be a UEFI/SecureBoot issue.

If it looks like this might be the case, it's a tough one to get around. The only way I was able to load _**any**_ Linux distro on my new laptop was by disabling SecureBoot in BIOS (UEFI).

Let me know if I'm barking up the right tree, and I'll try to offer some further help. Even better, you might get advice from someone who has real expertise in this area! ;)

---

### Post by fantab on 2013-03-18
WUBI Installer runs and installs Ubuntu within Windows as any other Winodows program would. It is not a recommended way to install Ubuntu. If you want my advice, then don't use WUBI instead use your Ubuntu LiveCD/DVD/USB to "[TRY UBUNTU]("http://www.ubuntu.com/download/help/try-ubuntu-before-you-install")". Install Ubuntu to dual-boot when you are ready.

The problem you are having could be a bad download of ubuntu.iso image. Check the integrity of the downloaded ubuntu.iso with [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM"). If the test fails then re-download Ubuntu, preferably via [bit torrent]("http://www.ubuntu.com/download/desktop/alternative-downloads"). Then [burn]("http://www.ubuntu.com/download/help/try-ubuntu-before-you-install") it to the media using appropriate and recommended tool.

I personally, prefer CLEAN INSTALL to version upgrades. Upgrades are often not without issues and not to mention time consuming.

---

### Post by rich4421972 on 2013-03-18
Secureboot on Win8 can be overidden by your computer's BIOS. Wait for your boot splash screen to appear (before Windows 8 starts) You might have to try a few times but you need to keep trying until you can access your BIOS and change your boot sequence. If you are talking about using auto login (starting ubuntu without entering your password), you can still do this by adjusting your settings in system tools==>settings==>All settings==> user settings and clicking on the enable autologin button. Best wishes. :)

---

### Post by liquidsix on 2013-03-19
if you are installing with wubi.exe, and are getting the archiving error, try disabling your firewall or your entire anti-virus software. Worked for me.

---

### Post by Bucky Ball on 2013-03-19
*Thread moved to **Ubuntu +1 (Raring Ringtail)**.*

There are known issues with 13.04 Wubi. 13.04 is not a good place to start unless you are into testing and reporting issues/bugs to help devs. I would consider 12.04 LTS and perhaps a dual-boot (Wubi can be problematic anyway and is not intended as a permanent solution, more to test and see if you like before installing Ubuntu but you can check it out and see if things are working from the regular Ubuntu install disk anyhow). Good luck.

---

### Post by dozoclown on 2013-03-19
It's a older pc (x60 lenovo tablet laptop). I just wanted to try Raring since it was new. I'm just going to wait untill Raring has been out longer!!!

---

### Post by kaldor on 2013-03-19
> **dozoclown said:**
> I'm just going to wait untill Raring has been out longer!!!

Raring is not out yet. You're using a preview version (probably a beta or daily build) which is intended for early testers and quality assurance. For release schedule, see the wiki page here: [https://wiki.ubuntu.com/RaringRingtail/ReleaseSchedule](https://wiki.ubuntu.com/RaringRingtail/ReleaseSchedule)

You're always welcome to file bugs and such, though :)

---

### Post by grahammechanical on 2013-03-19
> [COLOR=#000000] I don't have a clear understanding to why I have to creat a disk. It seems there is something easy that I'm doing wrong.[/COLOR]

How are we supposed to get a copy and install Ubuntu unless we have a Ubuntu install DVD? I do not have a Windows OS. How would I install Windows unless I purchased a copy of Windows on a DVD?

I have been running Raring Ringtail since development work first started on it back in November. Install images of development releases are built every day. I have tested several install images of Raring Ringtail and up until last week ago I always needed to change the boot parameters using some of the F6 options. Other testers did not have this problem. As far as my machine is concerned the problem has been fixed but something like it may still exist as regards your machine. The F6 options have been a part of installing Ubuntu since before I started using it 5 years ago. There has always been a problem installing Linux on some machines.

As you do not explain how the installer is not working there is not much advice that can be given to you. We need to know the signs and symptoms of the problem.

Regards.

---

### Post by mr john on 2013-03-19
Hi dozoclown, welcome to testing. Sorry about the rudeness of some people here. There's a bug with Wubu 13.04. The installer doesn't work yet. I'd wait for it to be fixed before trying a Wubi install for 13.04. If you subscribe to the bug in the link below you should be informed by email when a fix is committed.

[https://bugs.launchpad.net/wubi/+bug/1155704](https://bugs.launchpad.net/wubi/+bug/1155704)

I am the bug reporter and am interested in seeing this work too. The more testers we have the better. Please only add to the bug report if you experience issues relating to the original issue.

---

### Post by Bucky Ball on 2013-03-19
> **dozoclown said:**
> It's a older pc (x60 lenovo tablet laptop). I just wanted to try Raring since it was new. I'm just going to wait untill Raring has been out longer!!!

It is not out at all (late April). It is not released yet so problems are to be expected.

---

### Post by dozoclown on 2013-03-27
As I said I just wanted to try Raring since it was new. I just tried again and Raring loaded fine. I'm using it now! If it messed up something I have two other PC's I can use. Thank you all for your help!

---

### Post by fantab on 2013-03-27
I am glad that you finally installed 13.04. Just remember to update it daily until its final release.

---

