---
title: "I Want to try windows 10 but have partion problems"
date: 2014-10-03
forum: Windows
---

### Post by yuvio100 on 2014-10-03
I am an Ubuntu user who wants to try out Windows 10. I got the .iso file onto my usb and when I get to the point of picking the disk, all the disks say they cant install the OS. and it fails formating when I try to format my other 2 disks

Sorry, couldnt find the right thread to post this too

---

### Post by Elfy on 2014-10-03
*Thread moved to **Other Operating Systems and Projects**.*

---

### Post by oldfred on 2014-10-03
Assuming Windows 10 is like all the previous versions:

UEFI or BIOS? And are drives then gpt or MBR(msdos)?

Windows only boots from gpt partitioned drives with UEFI.
Windows and Ubuntu only boot from MBR drives with BIOS. 

You cannot mix boot modes & partitioning types, and how you boot install media UEFI or BIOS is how it will want to install and then partitions must match.

Windows in BIOS mode on MBR drives either wants a blank drive so it can create its normal 100MB boot partition and main NTFS install. But, you can install to one NTFS primary partition with boot flag if drive is MBR. Make sure BIOS is set to boot from Windows drive if you have other drives. Windows will install its 100MB boot partition to the BIOS boot drive and has been know just to overwrite the first 100MB as it does not see the Linux partitions. Maybe they fixed some of their bugs?

Many say it should be first partition, but requirement is just that it be primary. But Windows may create issues if the primary is after your extended partition. Best to have backup of partition table as well as full backup of system.

If a UEFI system it wants additional partition(s) also.

---

### Post by Tar_Ni on 2014-10-03
I am not sure but I think that's because you need a Windows OS in the first place in order to try the Windows beta. So if you are not a Windows user, that may explain why it fails to detect the OS and proceed to installation.

---

### Post by yuvio100 on 2014-10-03
Windows is offering the best (Windows Technical Preview) to everyone who wants to try it out

---

### Post by yuvio100 on 2014-10-03
So there's no way too dual boot windows and Ubuntu?

---

### Post by MartyBuntu on 2014-10-04
FWIW, Windows 10 Preview works well in VirtualBox...

---

### Post by buzzingrobot on 2014-10-04
The Win10 preview site has a link that appears to offer an install on an existing Windows machine, as well as links to iso images.  (The product key is there, too.) The 64-bit images are approx. 3.8 gigs. I've seen howto's for burning the image on a bootable USB stick (Neowin has one: [http://www.neowin.net/news/guide-how-to-install-windows-10-from-a-usb-drive](http://www.neowin.net/news/guide-how-to-install-windows-10-from-a-usb-drive)).  They assume use of a Windows terminal, but outline the partition structure that needs to be created on the USB stick, which could be done with gparted.

If a DVD drive is available, that's less hassle.

(I'm tempted to play with Win10 on another machine.  But, from what I've seen and read the wonky font rendering hasn't been improved, so I know I'd tear it down in a few hours.)

---

### Post by andrew.46 on 2014-10-04
Indeed the Windows 10 preview works nicely on Virtual Box and this would probably be the safest way to check it out. I see that somebody has even compiled and installed the Usenet client slrn on this Preview:

[http://slrn.sourceforge.net/images/slrn_windows10_setup.png](http://slrn.sourceforge.net/images/slrn_windows10_setup.png) 

A great combination of a 20 year old NNTP client and the latest and greatest from Microsoft....

---

### Post by oldfred on 2014-10-05
It seems Windows 10 Technical Preview logs everything you do, so they can improve system, but then it logs everything on your system and everything you do:

  It is not intended for normal use and it is not intended for production environments.
[http://yro.slashdot.org/story/14/10/05/1222201/test-version-windows-10-includes-keylogger](http://yro.slashdot.org/story/14/10/05/1222201/test-version-windows-10-includes-keylogger)

---

### Post by buzzingrobot on 2014-10-05
> **oldfred said:**
> It seems Windows 10 Technical Preview logs everything you do, so they can improve system, but then it logs everything on your system and everything you do:

  It is not intended for normal use and it is not intended for production environments.
[http://yro.slashdot.org/story/14/10/05/1222201/test-version-windows-10-includes-keylogger](http://yro.slashdot.org/story/14/10/05/1222201/test-version-windows-10-includes-keylogger)

People freak out about this and use it as another excuse to bash Microsoft, but if anyone reads the information displayed at the preview download site, it's all spelled out:

> Also, if your PC runs into problems, Microsoft will likely examine your  system files. If the privacy of your system files is a concern, consider  using a different PC. For more info, read our [privacy statement]("http://windows.microsoft.com/en-us/windows/preview-privacy-statement").     

That privacy statement details how and what is collected.

I'm not especially an MS fan but they've made it quite clear that they released this preview specifically in order to collect feedback. I wouldn't rely on or trust to only voluntary written feedback from users, if it were me.

---

### Post by mips on 2014-10-05
sudo fdisk -l

---

### Post by yuvio100 on 2014-10-05
How do I use Virtual Box to get Windows 10?

---

### Post by andrew.46 on 2014-10-06
> **yuvio100 said:**
> How do I use Virtual Box to get Windows 10?

Install VirtualBox, download the Windows 10 iso and then install. [Instructions here]("https://www.virtualbox.org/wiki/Linux_Downloads") for VirtualBox under Ubuntu... If you have problems with virtualisation there is a section of these forums dedicated to the subject.

Be aware that Windows 10 + VirtualBox do not support the Guest Additions as yet, hopefully this will come soon...

---

### Post by mips on 2014-10-06
> **buzzingrobot said:**
> The Win10 preview site has a link that appears to offer an install on an existing Windows machine, as well as links to iso images.  (The product key is there, too.) The 64-bit images are approx. 3.8 gigs. I've seen howto's for burning the image on a bootable USB stick (Neowin has one: [http://www.neowin.net/news/guide-how-to-install-windows-10-from-a-usb-drive](http://www.neowin.net/news/guide-how-to-install-windows-10-from-a-usb-drive)).  They assume use of a Windows terminal, but outline the partition structure that needs to be created on the USB stick, which could be done with gparted.

If a DVD drive is available, that's less hassle.

(I'm tempted to play with Win10 on another machine.  But, from what I've seen and read the wonky font rendering hasn't been improved, so I know I'd tear it down in a few hours.)

There's an easy way to create bootable Windows USB install media in linux.

You will need gparted(repos), ms-sys(PPA or compile from scratch) & a Windows dvd or iso image.

Insert your usb stick and open gparted. 
Delete whatever partitions you have on the device so it's blank. 
From the menu go Device-->Create Partition Table and select 'ms-dos'. 
Next create a single NTFS partition on the usb stick and set the label to msdos. 
Next right click on the partiton and go Manage Flags and choose the 'boot' option. 
Apply all settings and exit gparted.

Next we need to write a windows bootloader to the MBR of the USB stick,
```
sudo ms-sys -7 /dev/sdX
```

Where 'X' is the device identifier for your usb stick, do not add the number after the letter as that is the partition and we wan't to write to the MBR. The -7 designates the type of MBR, 7 will work with Vista->Win10 just running ms-sys will give you a list of other mbr versions if you wan't to use older versions of windows.

Next insert you windows dvd and copy the entire contents of the dvd over to the USB stick. If you have a iso image you will have to mount it with the 'loop' parameter (Vista & newer) or use a gui like FuriusISO to mount it with the loop option selected and then copy the files across.

You can now boot Windows from the USB stick. This method works every time and never fails. You can also edit the contents of the usb as it's writable unlike the results of those gui tools which give you some form of dummy chainloader effect.


Sorry for the wall of text explanation but it's actually only a few steps you have to which will take you less than 5min (excluding the copy of the dvd to usb)

---

### Post by sudodus on 2014-10-06
Thanks for those instructions *mips* :-)

[COLOR=#696969]I can also confirm that a plain clone of the WPT (Windows Technical Preview) ISO file to a pendrive (using dd or mkusb) does not work (at least not with the 64-bit version). isohybrid cannot make it bootable from USB.[/COLOR]

---

### Post by sudodus on 2014-10-07
I installed WPT (Windows Technical Preview) giving it the whole disk (SSD 60 GB). It seems this 64-bit version needs UEFI. I used Windows to shrink the partition leaving 15 Gibibytes. Then I booted an Ubuntu pendrive, used gparted to create partitions for Ubuntu and installed Ubuntu 14.04.1 into it (1.5 Gibibytes for swap).

***It worked without issues to create a dual boot system in my Toshiba computer*** with the following specs.

[http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/)

So I needed no Boot Repair or anything like that. Of course I avoid fast boot and secure boot.

---

### Post by lammert-nijhof on 2014-10-07
I have a relative old Desktop AMD X3 with a classical BIOS. I have installed the windows 10 in the old way and installed windows 10 in a primary partition and afterwards restored the Grub boot-loader. In my case windows uses the third partition after a primary partition for Ubuntu 14.04 and SWAP. After installing Windows 10, I've installed Ubuntu 14.10 in the fourth partition, which restored in my case the grub boot-loader. In fact I reply using Windows 10, that system is a big improvement after Windows 8. For some reason Microsoft keeps releasing a good system after releasing first a crap version of it, think ME/XP, Vista/7 and now 8/10.

---

### Post by bcschmerker on 2014-10-08
Thanks for the heads up on new developments from Microsoft Corporation.  I saw a linked article at Google+® recently; although some speculate Win10 to be a LinUX-based OS, what I see of Win10 is still OS/2-based, as the Technical Preview highlighted on an article elsewhere on the Web, judging from the build number, uses Windows® NT MultiProcessor Kernel 6.4.9814.  The HUD-style Start Menu in the tech preview uses the Win8.x Start Screen format rather than the Unity format already in use with Ubuntu® 12.04-up.

Having run into multiple SNAFUs on dual-boot attempts (Microsoft® Windows® NT 5-up requires specific NTFS and FAT32 partitions), I'm already planning on putting Win10 on a Win-specific machine; I don't see Win10 being able to read or write ext*n* any more than do Win 6, 7, 8, or 8.1.

---

### Post by sports fan Matt on 2014-10-09
All things aside, I don't mind the preview of Windows Ten.  I never adopt early but if it looks like this I may purchase the preview.

---

### Post by yuvio100 on 2014-10-09
Thank You So much! I downloaded it and use this helpful tutorial: [http://www.cnet.com/how-to/how-to-install-windows-10-technical-preview-as-a-virtual-machine/](http://www.cnet.com/how-to/how-to-install-windows-10-technical-preview-as-a-virtual-machine/)

---

