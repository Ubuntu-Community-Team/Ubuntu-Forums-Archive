---
title: "Windows 10 on USB drive and Lubuntu 16.04 as main OS on HDD"
date: 2016-08-25
forum: Windows
---

### Post by Halbarad on 2016-08-25
Hi, I have a laptop HP 250G (4 GB, i5, UEFI) with Lubuntu 16.04 as the only OS. 
((Some background. I made up my mind to install this Ubuntu flavor as my only OS some three years ago and I am very happy with my choice. However, from time to time I need to use some Windows software: Photoshop CS5, some Canon software and the deprecated MS Word, which I need for checking that some complex documents (with many tables etc.) are correctly viewed by MSOffice users. I installed Oracle VirtualBox. It works quite well with XP, which is all I need. But since I upgraded to Ubuntu 16.04 and to VB 5.1.2 my Canon software has become extremely slow and memory consuming -- I guess there is a bug somewhere. At any rate, I thought it would be nice to have Windows 10 as a secondary OS on a fast USB 3 drive such as a Sandisk Cruzer Extreme, which is at least as fast as my HDD.))
I already have Kubuntu 16.04 live with persistence on a USB3 drive. It boots (UEFI) and it runs smoothly -- I'm planning to install it properly on a USB drive sooner or later. Windows 10 is another matter.
After browsing a bit, I learned that Windows 10 can be booted and entirely run from USB flash drive, in a mode that is called "Windows to go". See [ http://www.easyuefi.com/wintousb/]("http://www.easyuefi.com/wintousb/")
Thus, I downloaded the Win10 ISO 64 from the Microsoft site, I transferred it to a computer with a Win7 OS, downloaded the WinToUSB program and run it as Administrator on the same PC. WinToUSB wrote the Win10 OS onto a 32GB USB3 flash drive.
Then I went back to my HP Lubuntu PC. I checked the UEFI parameters: no secure boot, no Legacy, USB3 enabled on boot, USB HDD first in the boot sequence -- as I said, Kubuntu already boots from USB.
I plugged in the Win10 USB drive and switched on the PC. Nothing -- it led me to the usual grub screen for Lubuntu. I tried several times, no luck. Then I checked the boot menu again. Under UEFI OS I now had two choices: Ubuntu and Windows (!). I set Windows first and restarted. And Windows started -- well, not really. I got a Windows icon on my screen and Windows 10's turning balls. And the balls turned and turned. And turned. After half an hour, something like an installation procedure began, with the usual questions about time zone etc. The system was not responsive, everything was very very slow. (And the balls kept turning.) After half an hour, Windows 10 told me about some generic error in installation and crashed. Everything else failing, I had to switch off the PC by keeping the power button pressed for five seconds.
After that, I plugged off the USB drive and switched on again, but the system did not boot. I pressed ESC, F10, F9, switched on and off (power button for five seconds) many times. I couldn't even enter the boot menu. They say that UEFI integrates deeply with the OS -- it does for sure. It integrates so deeply that it almost disintegrates when the OS (Windows) badly crashes during installation. This seems to me crazy, but it is a matter for another post. At about my tenth attempt I eventually entered the boot screen! I reset the Ubuntu OS to the first position and everything has been working since then.
Except for the following: (i) my boot menu *still* has an option for Windows UEFI boot -- which in my opinion means that Windows has tampered with the EFI FAT32 partition of my HDD. (It is the only one partition it could tamper with and it punctually did.); (ii) I do not have any "Windows to go" USB drive.
My question is: has anyone succeeded where I failed? Have I made a mistake somewhere (please just avoid saying my mistake was to trust Windows, I keep repeating that to myself).  I could even try again, but I'm very much scared by the possibility that I destroy my PC.
EDIT: in my EFI partition (FAT32) I actually have two Microsoft directories: one is in /boot/efi, the other in /boot/efi/EFI. Does any UEFI guru suggest I can safely erase these directories?

---

### Post by yancek on 2016-08-25
The standard message you will get when trying to install any windows to a usb drive is:

> "windows setup does not support configuration or installation to a disk connected through usb or IEEE 1394 ports". 

I've read a little about "Windows to go" but never tried it.  I would think that if you are using EFI with Lubuntu, you will need EFI with windows and the efi files for both systems will go on the same drive, same partition.  I think your actual problem is in using windows to go and you would be much better off at a windows forum or the microsoft site for a solution on putting windows on a usb drive.

It  isn't really clear whether you have the windows 10 installation medium on a usb drive and are trying to install it or if you have it installed some how and can't boot it?

Good luck.

---

### Post by Halbarad on 2016-08-25
Thank you for your reply, Yancek. Yes, Windows 10 actually needs EFI, but for a "Windows to go" the bootloader ought to be on the usb drive -- the HDD should be untouched. I don't have the Windows installation medium on usb, I used WinToUSB to format the usb and write the contents of the iso installation file on it. --- I confess I heartily dislike Windows and I feel I am just wasting some time but I'm going to give another stab at it, maybe by making an EFI boot partition myself on the flash drive. Or I might physically disconnect the HDD before booting from the usb drive. It looks like I am going to learn something about EFI and bootloader location...

---

### Post by oldfred on 2016-08-25
With Ubuntu I have to create the ESP on the flash drive.
And then copy from the ESP on sda to the ESP on the flash drive.

External devices only boot with UEFI from /EFI/Boot/bootx64.efi. 
But bootx64.efi can be a Windows file or a grub file. And with grub the version on an installer is different than a direct install of  grub to a flash drive or full install of Ubuntu. Grub has lots of settings/options to include drivers, etc. The installer's version of grub is a minimum version of grub for the install configuration. And a full install has all the drivers.

In the Windows 7 instructions, it shows copying the Windows .efi boot files into /EFI/Boot and renaming Windows .efi to bootx64.efi.
       How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)

---

### Post by Halbarad on 2016-08-26
Thank you so much, oldfred. As it happens, I have found out that three (!) tutorials about WinToUSB were to say the least misleading. The tutorials advertised WinToUSB as a tool for generating a "Windows to go" environment on USB and they suggested a detailed procedure for doing so. But the procedure they suggested was in fact the one for generating a USB *installation* drive for Windows. Therefore my USB drive, so prepared, didn't work as I meant it to. WinToUSB can actually generate a "Windows to go" environment, but this is a kind of clone of the working Windows system installed on the same PC on which WinToUSB runs. It normally uses a huge space on disk; I don't know how it handles drives and, above all, it cannot be updated and repaired. Therefore, it isn't the kind of stuff I was looking for. I think I'll follow your suggestions and links.
Even before doing that, though, I'd like to understand EFI a bit better. The very first thing I wish to focus is perhaps this: is it possible to have two completely independent EFI systems on HDD and USB drive? I can have two independent EFI partitions of course. But is it possible to arrange things so that the PC boots (UEFI) from USB drive (if plugged in) and boots (UEFI) from HDD if no USB bootable drive is found? 
When I UEFI installed Kubuntu on a USB drive I succeeded and I specified that the bootloader for Kubuntu should be on sdb, that is the USB drive, but after booting Kubuntu from USB Lubuntu would not boot any more from HDD: with the Kubuntu USB drive unplugged I just got a minimal grub on boot. It was easy to repair everything with boot-repair but I am still a bit puzzled about the way UEFI boot behaves. So, before fiddling with Windows I'll carefully study the stuff on UEFI boot install and repair at the link you provide in your signature.

---

### Post by oldfred on 2016-08-26
I have tried multiple full installs of Ubuntu to my internal sdb drive and external flash drives. And every time I specify to install grub to that drive. During install it even (quickly at bottom) says installing grub to sdb. And it overwrites my main working install's grub in sda. I quickly learned to backup my ESP.

But it turns out that only real difference is a 3 line grub.cfg that is a configfile or chainload entry to the full grub.cfg in the install. So now I just replace my main working installs grub.cfg in ESP, or even have edited UUID & partition info.

While internal drive boots from grub menu of main working install & I do not have to have an ESP on sdb, I do have to have an ESP on the external drive, so it can boot on its own.
And external drives only boot from the /EFI/Boot/bootx64.efi in the ESP. If full install, you also have to edit fstab with external drive's ESP, not internal drive's ESP.

---

### Post by sudodus on 2016-08-26
If you want a portable *installed* Ubuntu or Ubuntu flavour (Kubuntu, Lubuntu, ..., Xubuntu) booting from UEFI and BIOS, you can try the following link,

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

I don't think Windows will be easy to boot from directly from USB. If your computer is powerful enough, it should be possible with an Ubuntu flavour installed in a fast USB 3 pendrive with VirtualBox and Windows as a guest [operating system in a VirtualBox virtual machine].

---

### Post by sudodus on 2016-08-26
An alternative is a Windows Preinstallation Environment, but those are very small systems, mainly intended for test and repair jobs.

You find several good links, if you browse the internet for **Windows Preinstallation Environment**.

---

### Post by Halbarad on 2016-08-26
@ sudodus
> **sudodus** If your computer is powerful enough, it should be possible with an Ubuntu flavour installed in a fast USB 3 pendrive with VirtualBox and Windows as a guest [operating system in a VirtualBox virtual machine].
I actually have a VirtualBox and Windows XP as a guest in my main system, which is Lubuntu 16.04 installed on my only internal HDD. (Laptop HP 250G3, 4GB and some kind of i5.) I have disabled my internet connection on the guest XP and I must say it runs remarkably fast: after some tweaking my experience with Photoshop CS5, even with raw enhanced photos (about 50 MB) is excellent, everything is much faster and more responsive than in my wife's Win7 machine -- which steadily slows down in time. I have also solved my problem with the Canon software after my latest upgrades. And so I am not under any pressure and can make new trials just for the pleasure of learning and of reaching a better control of my system.
> **sudodus** An alternative is a Windows Preinstallation Environment, but those are very small systems, mainly intended for test and repair jobs.
You find several good links, if you browse the internet for Windows Preinstallation Environment. 
I am aware of that: I have browsed around a bit and have found out some interesting projects. But this is really not what I am looking for. I am in fact beginning to realize that what I was looking for -- a functional Windows booting from USB -- is for the time being a delusion; and even this is a solution.
After all it's not *so* bad that I have to give up and I must keep Windows in its virtual little cage. It's a dangerous animal. I've eventually installed Windows 10 as a virtual machine and I find it chilling in spite of some superficial similarities with Linux. They protect me, watch me, influence me... gosh. OK, I'm desperately off topic. At any rate, I am getting more and more interested in the basics as it were: as things stand I'd be happy if I just succeeded to put together a USB drive with an *installed* Linux (Ubuntu flavor or not) that UEFI-boots without killing, or at least stunning, my main grub on the HDD. I have read sudodus' very interesting posts about a Swiss-army knife USB pendrive for 32, 64, UEFI and BIOS systems -- quite an accomplishment -- but my aim is simpler and much less ambitious: just a 64 pendrive with UEFI boot, and I'd so much like to find the precise spot on which to perform surgery in order to make things work.

@ oldfred
>  **oldfred** I have tried multiple full installs of Ubuntu to my internal sdb drive and external flash drives. And every time I specify to install grub to that drive. During install it even (quickly at bottom) says installing grub to sdb. And it overwrites my main working install's grub in sda. I quickly learned to backup my ESP.
It's of some comfort to be a company, if not a crowd. I've also backed up my ESP(s) but: my backup copy is not going to be of much use if I can't boot into the PC at all, as it happened after my disastrous attempt with Windows 10.
>  **oldfred** While internal drive boots from grub menu of main working install & I do not have to have an ESP on sdb, I do have to have an ESP on the external drive, so it can boot on its own.
And external drives only boot from the /EFI/Boot/bootx64.efi in the ESP. If full install, you also have to edit fstab with external drive's ESP, not internal drive's ESP.
Wow, this looks like a piece of very substantial advice. I checked my USB Kubuntu pendrive (full install) and there is no /EFI dir, only /boot/efi, which is empty. Moreover, the drive has an msdos partition table, according to gparted; I think this means mbr. I am sure I set the Kubuntu installer to format an EFI partition. Perhaps I should manually make a gpt partition table before installing? .... OK, wait. I clearly have to read the stuff about UEFI boot install and repair before going on. And then I need to make some trials etc. After that I'll come back with questions or reports. Perhaps I had better start a new thread then -- provided that I still have a working PC ;-)

EDIT: @ oldfred Your stuff is a mine of gold. Thank you so much.

---

### Post by oldfred on 2016-08-26
I did not think you could use MBR for UEFI. But the installer is usually MBR with one FAT32 partition and boots either UEFI or BIOS.

Then we saw multiple cases of users who installed to a second drive that was MBR partitioned, but UEFI boot from a gpt partitioned sda with the ESP. And there is a specification for MBR UEFI boot.

But gpt is the standard for use with UEFI. And I just started using gpt with my BIOS systems back with about 10.10. Then when UEFI started becoming popular (Windows 8) I knew eventually I would want UEFI on a new system. So I automatically with every new or reformatted drive add an ESP of 100 to 500MB unless flash drive then 100MB as first partition, and a 1 or 2MB bios_grub to the beginning of every drive. Now almost every drive I have is gpt.

---

### Post by sudodus on 2016-08-27
> **Halbarad said:**
> I have read sudodus' very interesting posts about a Swiss-army knife USB pendrive for 32, 64, UEFI and BIOS systems -- quite an accomplishment -- but my aim is simpler and much less ambitious: just a 64 pendrive with UEFI boot, and I'd so much like to find the precise spot on which to perform surgery in order to make things work.


This link, [Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS), is not to the Swiss-army knife USB pendrive for 32, 64, UEFI and BIOS systems, but to a 64-bit only system, that boots in UEFI and BIOS mode. The UEFI bootloader is installed for removable media, which may help avoid damage, when 'in contact with' an internal drive with an UEFI system.

From ```
man grub-install
```

```
--removable
              the installation device is removable. This option is only available on EFI.
```

This system can be flashed from a compressed image file to a USB pendrive, USB SSD, USB connected flash card or whatever, similar to how operating systems are flashed to mobile phones and other hand-held devices. After installation, there is a simple text mode interface with menus, so that you can easily install a graphical desktop environment, for example Lubuntu to keep it light-weight. See this link, [Mini system with 'text' screen user interface](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#Mini_system_with_.27text.27_screen_user_interface).

Maybe you want to build such a system yourself. Fine :-)

It might help if you start by installing 'my' system, and after that build your own system in another drive. Then you can compare things, which should make it easier for you to find a working solution.

---

### Post by Halbarad on 2016-08-27
@ oldfred and sudodus

Thank you so much. It looks like I have some work for the next nights. You -- both of you -- are doing a lot to make Linux available to many. Can I just ask a silly question. I installed the latest version of Clonezilla for an overall backup of my system -- just in case. Those Clonezilla people have actually been able to produce a USB pendrive that boots in a UEFI system without overwriting anything in sda -- it boots a kind of barebone Ubuntu 16.04. Their pendrive is MBR partitioned, it has an EFI and a boot directory -- the boot directory does not contain another efi, which strikes me as sort of tidy. I'd also like to take a more detailed look into their solution. Maybe you have already done so? The rough hunch behind my question is: perhaps one could boot any kind of Ubuntu in that way, not just a Clonezilla version. So, one might think of cloning (a part of) Clonezilla... At any rate I'm very much interested in the mini-system with text user interface. Sorry for not checking that before...

---

### Post by oldfred on 2016-08-27
Not used Clonezilla, but that sound just like standard Ubuntu live installer. Which is both a live system with or without persistence. 

 [http://askubuntu.com/questions/295701/what-would-be-the-differences-between-a-persistent-usb-live-session-and-a-instal](http://askubuntu.com/questions/295701/what-would-be-the-differences-between-a-persistent-usb-live-session-and-a-instal)
Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by sudodus on 2016-08-27
The most basic installer of Ubuntu is the mini.iso. You can use it to create a minimal installed system (and only the program packages that you really want).

[***mini.iso***, minimal install, netboot iso]("http://ubuntuforums.org/showthread.php?t=2230389&p=13211730#post13211730")

It is much more complicated to create an iso file (that can boot from CD as well as from USB). One method is to start from the following links

[Short help text to install and run the 9w 'NioWill' installer](https://help.ubuntu.com/community/9w/Manual)

[Will Haley: create-a-custom-debian-live-environment](http://willhaley.com/blog/create-a-custom-debian-live-environment/)

---

### Post by Halbarad on 2016-08-27
I had a look around -- just a look, there is a huge quantity of material. I'm going to try both the mini-iso and oldfred's direct approach, that is using a regular installer, but I'm working hard in this period and I just have some time late at night. A couple of questions (but please, don't feel under any "moral obligation" to reply; if you can't I'll follow the usual route and learn by browsing + trial and error).

@ sudodus I downloaded the mini-iso for Ub. 16.04, it's some 55 MB. If I mount it I only see an empty partition called Firmware, is that alright? And I read a post of yours in which you said "Unfortunately the mini.iso does not work in UEFI mode". This is too bad, because I'd precisely like to learn how to work in UEFI mode.

@ oldfred Please just tell me if I understand correctly:
say, I partition my usb drive in advance as gpt and I make the partitions you suggest
> gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
(I'd leave out the 1 MB bios-grub part)
plus a / partition of some 25 GB, ext2 or ext4 (I'd take away the journaling later)
no swap file -- or can I use the one on my HDD? Would this make the installer covet my HDD?? Everything seems possible. At any rate, my Lubuntu has never used my swap file in several years. 
Given these conditions, would the Ubuntu installer use the USB EFI partition as it were spontaneously and leave my HDD EFI and HDD grub alone? I mean, isn't this the intended goal of the whole job?
Would I then have a grub on my flash drive, so that I might even install another Linux system in dual boot? (this is just theoretical for a 32GB but it might make sense with a fast 128 GB USB drive)

I must go to sleep now, it's very late in my part of the world. Thank you for your advice.

---

### Post by oldfred on 2016-08-27
I have full Ubuntu on 16GB drive as BIOS boot with gpt.
And I have full Ubuntu with UEFI boot on a 64GB flash drive, but with a flash drive I use only 100MB for ESP as I do not expect to ever get complex UEFI boot on that drive.

I lied, I actually used 500GB on this 64 GB flash drive, not sure why now?

```
Disk /dev/sdc: 62.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name      Flags
 1      1049kB  525MB   524MB   fat32        efi64     boot, hidden, esp
 2      525MB   22.5GB  22.0GB  ext4         System64
 3      22.5GB  62.0GB  39.4GB  ext4         data      msftdata

```

---

### Post by sudodus on 2016-08-28
> **Halbarad said:**
> @ sudodus I downloaded the mini-iso for Ub. 16.04, it's some 55 MB. If I mount it I only see an empty partition called Firmware, is that alright? And I read a post of yours in which you said "Unfortunately the mini.iso does not work in UEFI mode". This is too bad, because I'd precisely like to learn how to work in UEFI mode.

I think a system made from mini.iso should look like that. Can you boot from it (in BIOS mode)?

When you browse to the web directory where you find the mini.iso file, select the parent directory, and you will find a file, which contains the md5sum of mini.iso (one of the lines in that file).

Run the command ```
md5sum mini.iso
``` in your computer and check that the result matches the line in the file 'in the parent directory'. Then you can be sure that the mini.iso was downloaded correctly.

It works well to install mini.iso into a USB drive with a tool that *clones* the iso file into the USB drive. (It works with several other tools too, but not all versions of all tools.)

-o-

If you want to install in ***UEFI*** mode, you can use the ***Ubuntu Server amd64*** iso file and get the same result as if mini.iso would have worked in UEFI mode. You can install for example standard Ubuntu, Lubuntu or Xubuntu this way if you wish. And you can install a minimal system with only text interface, and after reboot install your own selection of program packages.

Please check with md5sum that the download was successful or use the torrent method, that has a built-in check of the md5sum. It works well to install the Ubuntu Server iso file into a USB drive with a tool that *clones* the iso file into the USB drive. (It works with several other tools too, but not all versions of all tools.)

---

### Post by Halbarad on 2016-08-29
Just a report.
1. I completely failed in my attempts to install Ubuntu to USB drive using the official installer (is it ubiquity?)
I made live USBs of Kubuntu, Ubuntu Desktop and Gnome and tried to install them to two different target drives, 16GB USB2 and 32GB USB3. I made a gpt partition table in the target drives and made an EFI partition (FAT32, flags esp and boot) and EXT4. Then I chose something else in the installer and selected my partitions. I also selected "do not use" for the EFI partitions in my HDD and in the live USB. Then I started installation and the installer complained that it couldn't unmount the cdrom (?). But it went on and got immediately stuck after the file check. I think I should retry without forcing it not to use the EFI partitions in HDD or at least in the USB drive. So, more to do.
2. I tried the uefi-n-boot, the lazy option ;-) that is the Ubuntu 64 gamma 12GB. It works perfectly, I added noatime, disabled journaling, set swappiness to 5, installed and upgraded lots of stuff and booted the drive several times. My HDD grub has not been affected in the least. I wonder what the system would do if I tried to install another Linux (or perhaps even a Windows) in dual boot on the same drive (with boot-repair and all in the case of Windows). I only have a suggestion. It would be good if one that is looking for a USB install were immediately directed to a page called "Ubuntu USB install: the easy way" and just got some neat and quick directions, such as: 1 download ISO 2 install mkusb 3 flash the ISO ("and you get a real working OS on USB, not just a lame Ubuntu-to-go"). And then, as an option, noatime and journaling etc. Many hasty people just run away when they find a page full of links, ramifications and alternatives. At the end you should surely give a link to the the fuller treatment and the wider range of options that is provided at the present web page. But 29 people out of 30 would simply ignore it. And why should the 29 be left out. After many years with Linux I have come to think that it should work like an onion or an artichoke: the user is invited to learn more and to get in greater control of the system, but there are a loto of things she can do and enjoy even without being an expert. I'd also emphasize that the ISO size of the "12GB" thing is some 850 MB -- people tend to become depressed when they think that 12 GB of code are required to run a USB system.
So, thank you. Everything I've installed works: I just don't like Unity. I'll try to install KDE Plasma Desktop alongside Unity: if the system survives this it deserves a prize for stability.

---

### Post by sudodus on 2016-08-29
Congratulations to a working system :-)

I understand your views about too complicated instructions. Unfortunately I am not a salesman or teacher, but I understand what you write, and I think you are right, those instructions can be and should be made simpler, at least the 'first layer' that a beginner will see. I will think about it, and when I have time, I can start writing that layer. Would you be willing to help me by proof reading and discussing how to improve details?

I think it is possible to install another Ubuntu based system alongside the current one. But it would be tricky to avoid overwriting some aspects of the boot system of the internal or external drive. And it is possible to install KDE alongside Unity in the already installed standard Ubuntu system, but there might be conflicts between the two desktop environment systems, and it would be a bloated system.

I suggest that you select another compressed iso file: [dd_text_16.04-UEFI-n-BIOS_2016-05-27_intel-4-pendrive-7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_text_16.04-UEFI-n-BIOS_2016-05-27_intel-4-pendrive-7.8GB.img.xz)

according to [UEFI-and-BIOS/stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative).

After installing this mini-system from the 318 MiB iso file into 7.8GB in a USB pendrive, you can start by moving the swap partition and increasing the size of the root partition to use the whole USB drive. Do that with ***gparted*** when booted from another drive.

Then you boot into the mini-system and use the installer submenu to install the flavour of Ubuntu that you prefer, (Kubuntu, Lubuntu ... Xubuntu), and reboot.

---

### Post by Halbarad on 2016-08-30
I should be willing to help as I can. Sometimes I am very busy and I don't have free time even late in the night, but I think this wouldn't be too big a task.

Short report: installing KDE (Plasma Desktop env.) alongside Unity gave some expected problems (icons disappearing, minor conflicts). The interesting thing is that the pendrive grub somewhat changed and asked me to boot in the pendrive Ubuntu *or* in my HDD Ubuntu -- which was sort of invisible to the pendrive grub before. I guess this depends on some kind of grub update that performed a complete scan of the system boot partitions. At any rate, your system is solid: the HDD grub was not affected.

Ok, time for a new trial tonight...

---

### Post by sudodus on 2016-08-30
Yes, you were probably running ```
sudo update-grub
``` indirectly, when you installed and updated your system, and it found the other operating system in the connected drive.

Good luck with the new trial tonight :-)

---

### Post by Halbarad on 2016-08-30
I'm writing this one from my Kubuntu system installed on USB drive ;-)
Good news first (there aren't really any bad news): it works well, it boots faster than my HDD Lubuntu, even if I have a sense that it is a bit slower than the 12GB version of the ISO. Updates, upgrades, new installs are ok. Nothing crashed up to now.
And now the glitches: when it booted for the first time there were several errors (almost unreadable on the screen) and I had some trouble to type the password because several lines suddenly filled up with other characters, but I insisted and succeeded at my second trial. Then the main menu showed up, but it was continually pushed up by error notifications. The errors were always the same two:
ieee80211 phy0: rt2800_wait_wpdma_ready Error - WPDMA TX/RX busy [0X00000068]tc 4 (-5)
Device failed to enter state 4 (-5)
I had an idea that the errors might disappear on update-upgrade, so I managed to select update & dist_upgrade (in spite of the menu lines going up).
After the update and upgrade everything worked. During the upgrade I was given the option to select a new grub file but I didn't.
I installed Kubuntu, then (from Lubuntu) disabled journaling, redirected /etc/fstab to my HDD swap file and deleted the pendrive swap file. I also extended the ext4 partition to some 16GB.
The next boot was basically smooth and flawless, except for a message about /boot/... not found which flashed on the screen just before the grub menu appeared. The message keeps being displayed on boot, without exception.
Kubuntu works well, I installed some programs, the Italian keyboard etc. However, the wireless didn't work; I enabled it with rfkill and restarted the network service, then I also rebooted, but the Kubuntu network manager (which surely is no ordinary network manager and must have some K name) reported "Wireless: failed to request scan". The wireless worked in the 12GB installation and in my previous Kubuntu live with persistence. Before fiddling with module blacklisting etc. I just tried to power off and unplug the ethernet cable before booting. This made the trick; moreover, after recognizing the wireless the first time it kept recognizing it also the following times, even with the ethernet cable plugged in on boot. 
OK, this is all for the moment. In my opinion, the first install process would somewhat gain from being entirely automated up to the update & dist-upgrade. If you just warn the user that she shouldn't worry about error messages at the beginning and should wait for the updates to download and to install, the whole process may feel smoother and safer as it were. I'd also take away the first password session, which might be tricky. And a question: do you think I could use dd for cloning my installed system to another 32GB pendrive? Or I might backup the whole thing with Clonezilla.

The work you have done seems to me important. With a large and fast pendrive (I have a 32GB Sandisk Cruzer Extreme, which is faster than my HDD; I have been told that the 64GB is faster in reading) I could perfectly run my PC without internal HDDs. This might be the beginning of a change in the way of using PCs. Light PCs (just processing boxes) and external USB HDDs and/or pendrives, especially if portable, could bring about significant changes: make things lighter, more dynamic. What is my own in my PC would essentially reside in my pendrive or USB HDD. It's a real pity that Linux is not much more popular than it presently is. It is not only that a true install of Windows in a USB key seems to be very difficult, if possible at all; a Windows system based on drivers would make portability difficult. It might be just a dream but it makes me smile to think of Linux users just carrying around their portable OSs with ease while others trudge with their heavy systems...

---

### Post by sudodus on 2016-08-31
> **Halbarad said:**
> I'm writing this one from my Kubuntu system installed on USB drive ;-)
Good news first (there aren't really any bad news): it works well, it boots faster than my HDD Lubuntu, even if I have a sense that it is a bit slower than the 12GB version of the ISO. Updates, upgrades, new installs are ok. Nothing crashed up to now.

:-)
> 
And now the glitches: when it booted for the first time there were several errors (almost unreadable on the screen) and I had some trouble to type the password because several lines suddenly filled up with other characters, but I insisted and succeeded at my second trial. Then the main menu showed up, but it was continually pushed up by error notifications. The errors were always the same two:
ieee80211 phy0: rt2800_wait_wpdma_ready Error - WPDMA TX/RX busy [0X00000068]tc 4 (-5)
Device failed to enter state 4 (-5)
I had an idea that the errors might disappear on update-upgrade, so I managed to select update & dist_upgrade (in spite of the menu lines going up).
After the update and upgrade everything worked. During the upgrade I was given the option to select a new grub file but I didn't.
I installed Kubuntu, then (from Lubuntu) disabled journaling, redirected /etc/fstab to my HDD swap file and deleted the pendrive swap file. I also extended the ext4 partition to some 16GB.
The next boot was basically smooth and flawless, except for a message about /boot/... not found which flashed on the screen just before the grub menu appeared. The message keeps being displayed on boot, without exception.
Kubuntu works well, I installed some programs, the Italian keyboard etc. However, the wireless didn't work; I enabled it with rfkill and restarted the network service, then I also rebooted, but the Kubuntu network manager (which surely is no ordinary network manager and must have some K name) reported "Wireless: failed to request scan". The wireless worked in the 12GB installation and in my previous Kubuntu live with persistence. Before fiddling with module blacklisting etc. I just tried to power off and unplug the ethernet cable before booting. This made the trick; moreover, after recognizing the wireless the first time it kept recognizing it also the following times, even with the ethernet cable plugged in on boot. 

Thanks for describing these problems and how to fix them :-)
> 
OK, this is all for the moment. In my opinion, the first install process would somewhat gain from being entirely automated up to the update & dist-upgrade. If you just warn the user that she shouldn't worry about error messages at the beginning and should wait for the updates to download and to install, the whole process may feel smoother and safer as it were. I'd also take away the first password session, which might be tricky.

Those are good points. I will look into them. First of all, I think an update & dist-upgrade should be done of the system and a new compressed iso uploaded. 16.04 LTS is much improved now.

Maybe it is not a good idea to set log in to the text screen without a password for security reasons? On the other hand, physical access = full access to the data unless they are encrypted for an experienced linux user. So, when there is time for me, I will try to improve the system along your guidelines.
> 
And a question: do you think I could use dd for cloning my installed system to another 32GB pendrive? Or I might backup the whole thing with Clonezilla.

*Short answer:* Yes and yes.

*Long answer:* You can use mkusb too, read from the source drive and write to another drive (with dd under the hood). Clonezilla should work much faster, because it clones only used blocks, and it makes a big difference if only a small fraction of the drive space is used.

dd is a very powerful beast. If you fail to harness it, your family pictures might be devoured. It deserves the nicknames 'disk destroyer' and 'data destroyer'.
> 
The work you have done seems to me important. With a large and fast pendrive (I have a 32GB Sandisk Cruzer Extreme, which is faster than my HDD; I have been told that the 64GB is faster in reading) I could perfectly run my PC without internal HDDs. This might be the beginning of a change in the way of using PCs. Light PCs (just processing boxes) and external USB HDDs and/or pendrives, especially if portable, could bring about significant changes: make things lighter, more dynamic. What is my own in my PC would essentially reside in my pendrive or USB HDD. It's a real pity that Linux is not much more popular than it presently is. It is not only that a true install of Windows in a USB key seems to be very difficult, if possible at all; a Windows system based on drivers would make portability difficult. It might be just a dream but it makes me smile to think of Linux users just carrying around their portable OSs with ease while others trudge with their heavy systems...

I agree, linux could bring about significant changes. Let our minds be flexible and use linux in new ways :-)

---

### Post by yancek on 2016-08-31
> It is not only that a true install of Windows in a USB key seems to be very difficult, if possible at all; 

It's not possible with the windows installer and of course, that is by design.  When you 'license' windows, you are basically getting permission from them to use it on one and only one computer.  Microsoft wants users to pay the licensing fee to use their OS on each and every computer they use.  It's been that way from the beginning.

You are allowed to make a backup but if you were able in some way to clone a system and put it on another drive, I would think you would be violating the EULA.

---

### Post by Halbarad on 2016-08-31
@ yancek I don't agree with you. From a legal point of view, installing a single copy of the OS on a pendrive or on an external HDD is quite the same as installing it on an internal HDD. You just use it on a single machine at a time. You may unplug your internal HDD with Windows and move it to another machine -- the hardware constraints would be severe but you would not be violating any EULA.

@ sudodus I keep installing stuff and the system is solid. Can I just ask you how you managed to have the pendrive recognized as sda during installation? I found that out from fstab.
My next step will be, to install some Ubuntu (preferably good old Lubuntu) to an external USB disk. And then I could even wipe out my internal HDD and use it for storage... or for Clonezilla backup copies ;-)

---

### Post by yancek on 2016-08-31
> @ yancek I don't agree with you. From a legal point of view, installing a  single copy of the OS on a pendrive or on an external HDD is quite the  same as installing it on an internal HDD. You just use it on a single  machine at a time. You may unplug your internal HDD with Windows and  move it to another machine -- the hardware constraints would be severe  but you would not be violating any EULA.

Good luck installing windows on a pendrive or external usb hard drive.  The windows  installer won't do that.  I was going to install windows 10 to test it and got the message from the installer indicating windows would not install to a usb drive.  Everything I've read indicates the same.  Below is a quote from the EULA of windows 7 Home Premium Section 4.b.  So I guess it would depend upon the definition of 'device'.  Does it mean the computer as a whole or a physical drive?

>                            [FONT=Segoe UI][SIZE=2]Every time you transfer the software to a new device, you must remove the software from the prior device. You may not transfer the software to share licenses between devices.[/SIZE][/FONT]

                          

And to clarify, in my previous post I stated " When you 'license' windows, you are basically getting permission from them to use it on one and only one computer."  So if you were able to somehow install windows on a pendrive or external usb drive, you should be able to use it on that same computer which was my original point.  I think you will have serious difficulty doing that.  Reading through the EULA on my machine with windows 7, the below would seem to confirm this, that a 'device' means the computer not the drive.  According to the previous section I posted, if you moved the windows install from an internal drive to another drive you would have to remove it from the internal.  If you were able to attach the drive without using a usb that might work.

>    	 	 	 	    [FONT=Segoe UI, serif][SIZE=2]**Device.**[/SIZE][/FONT][FONT=Segoe UI, serif][SIZE=2] In this agreement, &#8220;device&#8221; means a hardware system (whether physical or virtual) with an internal storage device capable of running the software[/SIZE][/FONT]
  

---

### Post by sudodus on 2016-08-31
> **Halbarad said:**
> @ yancek I don't agree with you. From a legal point of view, installing a single copy of the OS on a pendrive or on an external HDD is quite the same as installing it on an internal HDD. You just use it on a single machine at a time. You may unplug your internal HDD with Windows and move it to another machine -- the hardware constraints would be severe but you would not be violating any EULA.

Laws and lawyers do not always work according to what we consider common sense ;-)
> 
@ sudodus I keep installing stuff and the system is solid. Can I just ask you how you managed to have the pendrive recognized as sda during installation? I found that out from fstab.
My next step will be, to install some Ubuntu (preferably good old Lubuntu) to an external USB disk. And then I could even wipe out my internal HDD and use it for storage... or for Clonezilla backup copies ;-)

Good catch :-)

I removed the internal drive. And it worked like that in my Toshiba laptop (from 2013). I think it works like this - selects sdb for the live drive (leaving sda for what would be the target drive).

If it does not work in your computer, it is possible to use a HDD or SSD connected internally or via eSATA, and use small partitions, so that it is possible to clone with dd to a smaller drive and fix the partition table backup at the tail end of the drive afterwards with gdisk.

---

### Post by westie457 on 2016-08-31
> [COLOR=#000000]Good luck installing windows on a pendrive or external usb hard drive. The windows installer won't do that. I was going to install windows 10 to test it and got the message from the installer indicating windows would not install to a usb drive. Everything I've read indicates the same. Below is a quote from the EULA of windows 7 Home Premium Section 4.b. So I guess it would depend upon the definition of 'device'. Does it mean the computer as a whole or a physical drive?[/COLOR]

It is possible to install Windows 7 and newer to a USB hard drive on the condition that the Windows Boot files are in the bootable partition of the main internal drive.
This means that the USB drive will only work with the machine with the correct Windows boot files.

The laptop I am using to post this has Windows 7 in a primary partition (/sda3) and Windows 10 in a logical partition (/sda9) the boot files are in /sda2.

---

### Post by yancek on 2016-08-31
> It is possible to install Windows 7 and newer to a USB hard drive on the  condition that the Windows Boot files are in the bootable partition of  the main internal drive.

Your post doesn't show anything indicating that as all the partitions you refer to, sda2, sda3 and sda9 are on the same hard drive.  Installing windows on a logical partition isn't a problem.  I had W2K installed on a logical years ago with w98.  Do you have an actual install of windows on another drive?

---

