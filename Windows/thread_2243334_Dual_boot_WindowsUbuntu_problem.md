---
title: "Dual boot Windows/Ubuntu problem"
date: 2014-09-08
forum: Windows
---

### Post by niko9 on 2014-09-08
I have accidentally deleted my partition that had Linux Ubuntu 12.04.02 LTS on it, while  maintaining Windows 7 on a separate partition. Having restarted  my computer Lenovo G560, I got the message: 

 error: unknown filesystem.
grub  rescue>

I can use recovery disc for windows7 to return to initial settings, but it will erase all current data on the disc. I also have back up windows installed on a separate partition, but I don't know how to get to it.  

Is it possible to save the data on the disc in this case?
And, is there a way to restore windows to the settings just before I deleted ubuntu partition?

Thx a lot!

---

### Post by coffeecat on 2014-09-08
Hello.

The problem is that the initial grub booting code in the mbr of the hard drive is looking for the rest of itself in the now-deleted Ubuntu partition. Hence the error.

By "recovery disc" I presume you mean the OEM manufacturer's recovery disc(s) which will restore your machine to its factory default configuration and, you are right, will erase your data and installed Windows applications. But you need to distinguish this from the Windows 7 repair disc which will restore the Windows bootloader for you. Have a look here:

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Where it says "Windows installation disk" in that wiki page, it is referring to the Microsoft Windows DVD, not the manufacturer&#8217;s recovery disc, which I think you are referring to. If Windows was booting OK before you erased the Ubuntu partition, and if you don't have either a Windows 7 installation disk or repair disk, you don't really need to "bootrec.exe /fixboot". So using an Ubuntu CD to re-install the equivalent of the Windows mbr (the equivalent of running "bootrec.exe /fixmbr") would probably be sufficient.

Another alternative strategy, if you want to restore your dual-boot, is simply to re-install Ubuntu, but use the "something else" option at the partitioning stage of the installer to re-create your Ubuntu partition(s) and install to them. If you re-install Ubuntu, grub will be re-installed and a dual-boot menu created.

---

### Post by niko9 on 2014-09-09
Coffeecat, thanks for your advices!

yes, you guessed well, I have manufacturer recovery disc

I will try to use that link you posted, lets hope for the best

if I understood you well, if I reinstall ubuntu, I will automatically get my dual boot back (keeping in mind to use "the something else" option?

---

### Post by coffeecat on 2014-09-09
> **niko9 said:**
> 
if I understood you well, if I reinstall ubuntu, I will automatically get my dual boot back (keeping in mind to use "the something else" option?

The reason I recommend the something else option is that some people are losing their Windows installation with one or other of the other options, and Ubuntu is being installed to the whole of the hard drive. I'm not familiar with all the details, but it would certainly be a wise precaution to use "something else". In fact, if I was in your situation I would boot the Ubuntu live DVD to the desktop and use gparted to create a new ext4 partition where the old one used to be and then simply specify which partitions the installer should use at the "something else" stage. You can create partitions with the something else option if you wish though - I'm merely expressing my preference for using gparted for partition work.

---

### Post by oldfred on 2014-09-09
If you can boot Ubuntu live installer you can install a Windows type boot loader to the MBR to boot Windows. It is not the official Windows version (copyright issues) but works the same way.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

You can install the Boot-Repair application that provides a gui for installing a new boot loader to MBR.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

But you have to copy & paste a few commands to install Boot-Repair when you can just copy & paste a few commands to install the Lilo boot loader's MBR (not full Lilo boot loader).

      
 Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader to boot partition with boot flag (Windows).

Boot flag must be on NTFS partition with Windows boot files for a Windows type boot loader to work.

---

### Post by niko9 on 2014-09-10
problem solved!

I simply re-installed ubuntu with my old DVD. Coffeecat, during instalation I used your alternative strategy, i.e. I chose something else option, as you advised. Then, I re-created root partition for my ubuntu. After instalation, in boot menu I had the option of choosing between old and new instaltion of ubuntu (alongside windows, of course). I opened the old instalation, updated it, and after restarting double offering of ubuntu in boot menu disappeared (somehow they merged into one).

So, everything turned out perfect, I didnt lose any OS or files, except that Firefox in windows is not working properly, i.e. it gets blocked. I dont know if it has something with all these arrangements.

Coffeecat and Oldfred, thanks a lot! :)

---

### Post by niko9 on 2014-09-10
btw, using live session with ubuntu instalation DVD, I realized how vulnerable my computer is. I had access to all files on my computer, including the files stored in windows part of the disc. So, all my passwords turned out to be useless when confronted to a simple ubuntu instalation disc. 

Does anybody know how to better protect ourselves? Is BIOS password strong enough to prevent such intrusions?

---

### Post by coffeecat on 2014-09-10
I'm glad it's all working now. However... 

> **niko9 said:**
>  After instalation, in boot menu I had the option of choosing between old and new instaltion of ubuntu (alongside windows, of course). I opened the old instalation, updated it, and after restarting double offering of ubuntu in boot menu disappeared (somehow they merged into one).

That sounds very odd. If you had deleted your original Ubuntu partition as you say in your first post, then you certainly wouldn't have two versions of Ubuntu on the hard drive, and Ubuntu installations do not merge themselves. I wonder if it was simply a matter of a kernel upgrade changing the appearance of the grub menu. Perhaps we ought to look at your partition layout. Post the output of these three terminal commands:

```
sudo fdisk -lu
sudo parted -l
mount
```

I can't remember whether parted is installed by default, so you may have to install parted before the second one will run.

> **niko9 said:**
> Firefox in windows is not working properly, i.e. it gets blocked.

That wouldn't be anything to do with re-installing Ubuntu. Since this thread is already in our Other OS section, perhaps we might be able to help, or perhaps you might want to get help on a Windows forum. Questions: What exactly do you mean by blocked? What error message do you get? Do you have any problem with Internet Explorer? Have you tried installing Google's Chrome web-browser to see if that works? If all web browsers are blocked perhaps this is a networking issue. If IE and Chrome work OK, then you would need to investigate Firefox's settings.

---

### Post by coffeecat on 2014-09-10
> **niko9 said:**
> btw, using live session with ubuntu instalation DVD, I realized how vulnerable my computer is. I had access to all files on my computer, including the files stored in windows part of the disc. So, all my passwords turned out to be useless when confronted to a simple ubuntu instalation disc. 

Does anybody know how to better protect ourselves? Is BIOS password strong enough to prevent such intrusions?

This has come up many times. It won't be difficult to find discussion threads on this issue. Bottom line is, if someone has physical access to your hardware, it is very difficult if not impossible to secure your data, unless you encrypt it. If you want technical advice on how to secure your system I suggest you start a thread in Security:

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

If you want to discuss this matter without necessarily asking for technical help, you can start a discussion thread here:

[http://ubuntuforums.org/forumdisplay.php?f=434](http://ubuntuforums.org/forumdisplay.php?f=434)

---

