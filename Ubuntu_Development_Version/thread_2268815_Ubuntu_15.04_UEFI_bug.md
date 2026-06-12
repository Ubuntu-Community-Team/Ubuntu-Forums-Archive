---
title: "Ubuntu 15.04 UEFI bug?"
date: 2015-03-11
forum: Ubuntu Development Version
---

### Post by polochamps on 2015-03-11
Hi,

I have a UEFI problem during installation.
Installer says ESP than the usual EFI partition seen on older version of Ubuntus.
[IMG]http://i1289.photobucket.com/albums/b519/polochamps2004/Screenshot%20from%202015-03-10%20140330_zpskhzfiqdv.png[/IMG]
 

Had this weird looking notification window that clearly says "Debian".
[IMG]http://i1289.photobucket.com/albums/b519/polochamps2004/Screenshot%20from%202015-03-10%20134744_zps95nnihro.png[/IMG]


I needed to execute these commands to boot properly.

[http://ubuntuforums.org/showthread.php?t=2223856&p=13025073#post13025073](http://ubuntuforums.org/showthread.php?t=2223856&p=13025073#post13025073)
```
This is my final post with a summary of my problem and the corresponding  solution in order to avoid to waste your time on resolving it.

The first thing to do is to check if you boot your live Ubuntu system in UEFI mode
     Code:
     [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 
If the answer is "EFI boot on HDD" then you can proceed otherwise you have to modify your boot setting into the BIOS [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Then you have to: 1) restore your efi partition and 2) reinstall the GRUB
1) To restore your efi partition 
First install efi boot manager
     Code:
     sudo apt-get install efibootmgr 
check that your partition is GPT and that you have an efi partition as first partition of your drive [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
     Code:
     sudo gdisk -l /dev/sda 
Then you have to mount your Ubuntu system partition and efi partition. In my case the Ubuntu is located in /dev/sda2
     Code:
     sudo mkdir -p /mnt/system
sudo mount /dev/sda2 /mnt/system 
while the efi partition is located in /dev/sda1
     Code:
     sudo mount /dev/sda1 /mnt/system/boot/efi 
Finally you have to install one entry into the UEFI BIOS boot list with the following command
     Code:
     efibootmgr -c -d /dev/sda -p 1 -w -L ubuntu 
Now you have installed the efi entry for the Ubuntu system.

2) To install the GRUB you have two possibilities. First, for both you have to install this
     Code:
     sudo apt-get install grub-efi-amd64 
and now your live Ubuntu is able to install UEFI GRUB.

The first possibility is to manually install the GRUB with these following commands
     Code:
     sudo  grub-install --boot-directory=/mnt/system/boot --bootloader-id=ubuntu  --target=x86_64-efi --efi-directory=/mnt/system/boot/efi --recheck  --debug /dev/sda 
```

What seems to be the problem and will it be resolved on the next Beta or RC?

Thank you

---

### Post by oldfred on 2015-03-11
I cannot read find print - old eyes :)

Did you originally install older version with legacy mode, so now new version sees grub in MBR, or a legacy boot? 
They are trying to fix the major bug where installer did not correctly see old installs, erased them,  and have made major changes to try to let users know what is changing or being erased.

If you are totally overwriting everything what difference is it making?

And Ubuntu is based on Debian so an unreleased version may still have references to Debian.

---

### Post by polochamps on 2015-03-11
> **oldfred said:**
> I cannot read find print - old eyes :)

Did you originally install older version with legacy mode, so now new version sees grub in MBR, or a legacy boot? 
They are trying to fix the major bug where installer did not correctly see old installs, erased them,  and have made major changes to try to let users know what is changing or being erased.

If you are totally overwriting everything what difference is it making?

And Ubuntu is based on Debian so an unreleased version may still have references to Debian.

AFAIK this the latest version (06-Mar-2015).

Sorry but I can't really understand what you're saying so please correct me if I misunderstood your point. ;)

> so now new version sees grub in MBR, or a legacy boot?

I think it's GPT right? My UEFI is set to disabled CSM so if an OS installation is set to MBR it will not be seen as an option during boot. 

or

If what you mean by "install older version with legacy mode" is I installed an older version of Ubuntu in legacy mode?
No. I always set my UEFI to disable all legacy compatibilities including USBs.

There was a similar bug (if not exactly) on elementary OS Freya that has been resolved.

> If you are totally overwriting everything what difference is it making?

Overwriting? You mean the commands I executed? The difference is I get to make an OS boot and function as what it's intended or supposed to do out of the box.

> And Ubuntu is based on Debian so an unreleased version may still have references to Debian.

Ah. My point is that the "message window" we're seeing does not exist on the older versions of Ubuntu.
What I'm trying to unravel here is what are the "new" changes that breaks the UEFI installation.

Thank you

---

### Post by cariboo on 2015-03-11
I've done a couple of Ubuntu installs alongside Windows 8.1 in UEFI mode, and aside from needing the Ubuntu Boot repair package, things went the way they are supposed. This is on a newly purchased Toshiba notebook.

I do have to say that after playing with Windows 8.1 for a couple of days, I switched the bios to legacy mode, wiped the hard drive and did a fresh install of Vivid. I also have an Ubuntu Next iso that works when I boot from it to try, so that will be my next experiment, once I resize the hard drive. :)

---

### Post by ventrical on 2015-03-12
> **polochamps said:**
> AFAIK this the latest version (06-Mar-2015).

Sorry but I can't really understand what you're saying so please correct me if I misunderstood your point. ;)



I think it's GPT right? My UEFI is set to disabled CSM so if an OS installation is set to MBR it will not be seen as an option during boot. 

or

If what you mean by "install older version with legacy mode" is I installed an older version of Ubuntu in legacy mode?
No. I always set my UEFI to disable all legacy compatibilities including USBs.

There was a similar bug (if not exactly) on elementary OS Freya that has been resolved.



Overwriting? You mean the commands I executed? The difference is I get to make an OS boot and function as what it's intended or supposed to do out of the box.



Ah. My point is that the "message window" we're seeing does not exist on the older versions of Ubuntu.
What I'm trying to unravel here is what are the "new" changes that breaks the UEFI installation.

Thank you

We had a good discussion here :  [http://ubuntuforums.org/showthread.php?t=2259055](http://ubuntuforums.org/showthread.php?t=2259055)

.. maybe there is a tid-bit of info there as I recall seeing that notification screen also. 

Regards..

---

### Post by polochamps on 2015-04-13
Update: Added bug link.

Bug:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1418706](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1418706)

---

