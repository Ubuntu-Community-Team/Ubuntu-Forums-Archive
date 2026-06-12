---
title: "How do I install Windows 7 after installing Ubuntu Studio 14.04.1?"
date: 2014-09-17
forum: Ubuntu Studio
---

### Post by davidgrz on 2014-09-17
I have found many guides explaining how to install a dual boot of Windows 7 and Ubuntu, however all of them seem to recommend installing Windows 7 first and use the same drive.

I have a different setup. 

I have already installed Ubuntu Studio 14.04.1 on a 1 terabyte hard drive that I have, which is what I am currently using.

I have a separate 500 gigabyte hard drive where I would like to install Windows 7 for certain programs.

Is it possible to do this? I would like to keep them on separate hard drives if possible, as I will be using Ubuntu as the main OS.

Another option is using a virtual machine to run Windows 7 in Ubuntu, but from what I have read that is error prone and I need to use AutoCAD in Windows.

I would appreciate any advice on the matter. I used Linux a long time ago and have recently come back to use Ubuntu for my personal computing needs as I can't stand Microsoft Windows anymore. Unfortunately some of the programs I need are currently only available for Windows.

I am using an HP with an AMD Phenom X4 Processor.

:mad:

---

### Post by QIII on 2014-09-17
Hello!

BIOS or UEFI?  If UEFI, hold on.  I haven't ever dual booted a UEFI system but others have.

Assuming BIOS, since that's not the most current of processors:

Unplug your Ubuntu drive.  Be sure you get the right one unplugged.  That will make sure you don't foul up Ubuntu.

Install Windows 7 on the 500GB drive as you normally would.

When that's done, reconnect the Ubuntu drive.  Make sure your BIOS is set to boot first to your Ubuntu drive.

Go to the terminal and update GRUB

```
sudo update-grub
```

should find Windows 7.

This is a lot less complicated when you use two drives, which is why I always did it that way.

---

### Post by davidgrz on 2014-09-17
Yes I do use BIOS.

I am going to try that. I'll let you know how it works out. I appreciate the quick response.

Thanks.

;)

---

