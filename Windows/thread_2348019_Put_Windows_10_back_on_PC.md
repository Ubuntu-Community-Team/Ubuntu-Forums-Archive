---
title: "Put Windows 10 back on PC"
date: 2016-12-30
forum: Windows
---

### Post by westparkgirl on 2016-12-30
Ok, so the short of it is this - I want to put Windows 10 back on my computer.  Here's why - I purchased a computer from a rent to own store;  they had a program installed which locked out customers behind on their payments.  Keep in mind I PURCHASED this computer, I own it completely.  About a year later(maybe 3 months ago now) there was a routine update for Windows 10.  This update triggered this lockout program, which should have been uninstalled but wasn't. The rent to own company said they could probably fix it but would need to send it away.  Having worked for them in the past I knew that it would be sent away for 6 weeks and probably come back unfixed. The store manager had long since done away with the unlock key, so no luck there. Long story short, I had to install Linux on the PC to get it to function. Now, this is the laptop my wife uses...but its a gaming laptop, so she wants Windows 10 back. The video card she has doesn't play nice with Linux, so she can't even get Wine or PlayonLinux to work (It's a Nvidia GeForce series, can't remember exactly the type). I don't want to pay, or at least not pay much for Windows 10, since I already owned it on the same computer.  Don't get me wrong, I am not trying to get it illegally, but I don't even know where to start.  Any help is appreciated!

---

### Post by QIII on 2016-12-30
Hello!

I'm assuming you don't have an install disk?

Is there a valid, legal, holographic sticker on the case with a Windows Product Key?  Something you recieved in the paperwork with that key?

---

### Post by westie457 on 2016-12-30
Windows 10 can be reinstalled at any time provided either it came pre-installed or was an upgrade from Windows 7/8.1.
The license number is usually not needed.
I have used this procedure on at least two computers in the last month.

If using a non-Windows computer go here. [https://www.microsoft.com/en-gb/software-download/windows10ISO](https://www.microsoft.com/en-gb/software-download/windows10ISO)

Follow the instructions on the page to download the iso.

When this has completed plug in a USB stick (capacity 8GB is large enough), close any autorun prompts.
Open 'Disks' utility > highlight the entry for the usb stick > click the top-right Menu button > select 'Restore Disk Image' choose the iso you downloaded.
[B]
IMPORTANT
Double-check[/B] that the destination is the usb stick. Do not worry about the size difference warning. Click 'Start Restoring', enter your password in the pop-up window.

Windows Activation reads the information already on your computer and compares that with info held on Microsoft servers.

---

### Post by westparkgirl on 2016-12-31
Thank you QIII and Westie!  I normally reply much more quickly, but I've come down with a bug and have been in bed since I posted :frown: [CENTER][COLOR=#000000]:-({|=.  Anyway - yes, it does have a holographic sticker, but no paperwork.  So, according to you Westie, it should work.  We have our (very!) small business paperwork on it, so once we get that transferred onto another PC, we'll get to work on that.  I have a followup question as well - since my wife has been using Linux, she wants to keep it as a dual-boot with Win 10 (hooray!).  I know it's a bit of a process when you already have Win10 on the laptop, but how is it going this way?  Will I have to overwrite everything then re-install Linux?  Thanks again! [/COLOR][/CENTER]

---

### Post by oldfred on 2017-01-01
Is System UEFI or BIOS. And  then if UEFI with Windows must be gpt partitioned or if BIOS with Windows must be MBR partitioned.

And Windows in BIOS mode only installs to a primary NTFS partition with the boot flag. Its default BIOS install is two primary partitions, one small 100MB boot partition. But Boot partition is more for if you want to encrypt Windows. And MBR(msdos) has the 4 primary partition limit.

If UEFI, lots of UEFI info in link in my signature below. Windows will want several extra partitions but the limit is 128 partitions and that can be changed if needed.

---

### Post by westparkgirl on 2017-01-01
Ok, maybe a dumb question, but I can't find a clear answer - how do I find out if it's UEFI or BIOS?

---

### Post by oldfred on 2017-01-01
Since partitions must be MBR for BIOS or gpt for UEFI they will show it.

sudo parted -l

I had this in noted, not sure if Windows 10 same or not:
 To ascertain the type of Platform Firmware on a Windows 8 computer, open Run ( WinKey+ R ), type "msinfo32" and click OK. This opens the System Information window. Select System Summary (on the left panel) and check for the Items "BIOS Mode" and "Secure Boot State". The BIOS Mode value can be UEFI/Legacy, and the Secure Boot State value can be On/Off when UEFI Mode and Unsupported when Legacy Mode.

---

### Post by westparkgirl on 2017-01-01
Well, it's running the latest Mint, so not Windows:P. How would I go about that? EDIT - sorry, apparently I can't read this morning. Please disregard my wuestion

---

### Post by westparkgirl on 2017-01-01
This is the output for sudo parted -l

Model: ATA ST1000LM014-1EJ1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  538MB   537MB   fat32           EFI System Partition  boot, esp
 2      538MB   994GB   993GB   ext4
 3      994GB   1000GB  6226MB  linux-swap(v1)

So, does this mean it's UEFI?

---

### Post by yancek on 2017-01-01
Your output does show an EFI partition so your Mint is installed EFI and you would need to install windows EFI.   Your second partition takes up almost the entire drive so there is no space on which to install windows until you shrink that partition.  You can use GParted partition manager in Mint to do that.  It is on the install media for Mint.  When I installed windows 10, I used the 'Custom' install option so I could select the space/partition on which to install it.  If you don't use that option, it will probably overwrite everything.  The windows installer overwrote my Linux code in the MBR.  I don't used EFI so I'm not sure what will happen but I would expect it to create separate windows boot files on the EFI partition.

---

### Post by westparkgirl on 2017-01-01
Thanks.  I really appreciate all your help.  I think for now, I'll just overwrite with Windows.  Then, I may partition Linux back on later..

---

### Post by westparkgirl on 2017-01-01
So I followed the instructions, got Windows 10 ISO onto the USB stick, formatted the HD to NTSC and, in the process, got rid of linux. That's where it all went downhill. Tried to reboot from USB, but apparently it isn't a Bootable USB drive. Should've tested that first I guess. Basically, she has a computer with no OS right now. Can anyone offer any help/suggestions? I have a Windows 7 machine and an old Linux desktop. Any help is appreciated!

---

### Post by oldfred on 2017-01-01
You have to have a bootable flash drive or DVD. But you have to make sure you are using correct way to boot flash drive. Many are not a USB device, but another hard drive.

Windows sites have instructions for using Windows to create installers.
And if system is UEFI, you must be sure to boot Windows installer in UEFI boot mode.

---

