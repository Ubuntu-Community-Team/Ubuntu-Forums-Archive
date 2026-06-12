---
title: "Windows &gt; Ubuntu Studio"
date: 2016-05-21
forum: Ubuntu Studio
---

### Post by anon24 on 2016-05-21
Ok, so I installed Windows 10 on my PC. I tried to boot with the USB by holding shift while powering up with the USB connected to no avail. I formatted the drive in Ubuntu with the Ubuntu Studio ISO. My question is, do I have to redownload the ISO and then reformat the USB using Universal USB Installer?

---

### Post by anon24 on 2016-05-21
My other question is: 

Can I have Ubuntu installed on a separate hard drive in my computer? I have two solid state hard drives and I have Windows installed on one. Could I install Ubuntu Studio on the other?

---

### Post by QIII on 2016-05-21
With regard to your second question:  Can you dual boot Ubuntu with Windows 10 on separate drives?  Yes!  Separate drives work best.

With regard to the USB:  What are your machine's specs?  Have you set your UEFI/BIOS settings to allow the machine to boot from USB?

---

### Post by anon24 on 2016-05-21
Thanks for your quick reply! That's great, I may be getting ahead of myself, but I will need to change boot priority so that Ubuntu boots up before Windows, right?

In regards to USB, I ended up trying F11 on startup and that did allow me to see the USB and use it to boot. However, it doesn't, it just boots Windows 10 after I select the USB.

I have an MSI GS70 2QE

I turned off Fast Boot and also turned off Secure boot. I also have Boot option 1 as: USB CD/DVD

Edit: DUR! I changed Boot option 1 to my actual USB drive and it brought up Grub!

---

### Post by oldfred on 2016-05-21
I prefer to have them on separate drives, are your drives in a RAID configuration? Some MSI systems are.

But with UEFI it is not quite as easy. Best to disconnect one drive and install so it only sees that one drive.
But then UEFI's NVRAM forgets the UEFI entries for the disconnected drive and you have to manually add them back in. Some UEFI may see new drive and add entries on several normal (not fast) boot where it checks system.

Some other MSI systems:
 [SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

---

### Post by anon24 on 2016-05-22
I do not have any drives in RAID. In the bios it is in AHCI mode. All drives are separate entities. It is in UEFI mode... That's the mode I thought that it needed to be in in order to boot with Windows 10.

I have Windows installed on SDD. I want to install Ubuntu Studio on SDA. However, when I try... It says, "No root file system is defined. Please correct this from the partitioning menu."

---

### Post by oldfred on 2016-05-22
Using Something Else install option requires you to select or create partitions. I normally create in advance with gparted and use change button to select.
Default install is just / (root) & swap and that is the minimum you have to create. With something else you can also create a separate /home if desired. 
With UEFI you also have to have the ESP - efi system partition and it normally should be first on drive.

I think this assumes same drive but shows Something Else:
 How To Install Ubuntu Linux Alongside Windows 10 (UEFI)
[http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html) 
      
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot) 
    
      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by anon24 on 2016-05-22
So, I know how to make different partitions. However, I have no clue which option to go with. I guess, I want to use UEFI? I don't know whether to use gpt or msdos or what. I have no clue what would be easiest. I just want to be able to boot either Windows or Ubuntu Studio at startup. You lost me with all of the technical jargon as much as I appreciate it.

 A simple break down of exactly what partitions I need to make and how to flag them in gparted would be helpful. Please, give me some direction. 

When I've installed Ubuntu before, I let it do its thing and it created all of the partitions for me. I was not doing a dual boot at the time. I have no clue how to create partitions with flags and such.
  
[ATTACH=CONFIG]269221[/ATTACH]

---

### Post by oldfred on 2016-05-22
Windows in UEFI boot mode only boots from gpt partitioned drive.
Windows in BIOS boot mode only boots from MBR partitioned drive.
And you want Ubuntu booting in the same boot mode as Windows.

And with gpt Ubuntu can boot in BIOS or UEFI boot mode if you have correct supporting partition, either ESP or bios_grub.
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) 

I posted one suggestion of partitions in post #7, but each user has different needs. Even my own optimal partitioning changes by the time I get a new hard drive and I only keep main working hard drive for 3 or 4 years.

---

### Post by anon24 on 2016-05-22
Alright, so I guess I want to do UEFI. Is this how my partition table needs to look? How do I add flags to the partitions like you were talking about earlier?
[ATTACH=CONFIG]269223[/ATTACH]

---

### Post by oldfred on 2016-05-22
Click on green check mark at top to create partitions. 
I try not to queue too many operations at once.
You can right click on a partition to choose flags.

I also like to label partitions as that can help in remembering which is which. Installer unfortunately does not show labels so once I had created a large data partition and smaller / partition. Not paying attention, I installed to the data partition. No data in it yet so nothing lost but another reason to have good backups.

---

### Post by anon24 on 2016-05-22
Luckily, I don't have any data that I have to worry about other than Windows on sdd and I have a Windows restore USB just in case anything goes wrong. All of my data is on an external that is not hooked up to my rig right  now.

I labeled the partitions. Does this look right? Are there more partitions that need to add or any flags that I need to add before my install?

[ATTACH=CONFIG]269227[/ATTACH]

---

### Post by oldfred on 2016-05-22
Looks fine.

Just minor point. /root is only for root like /home is for a user. / is the correct top level system folder. But I put in version like yakkety or trusty as I have multiple / (root) partitions and want to know which is which.

---

### Post by anon24 on 2016-05-22
I changed the name to just / 

Are you saying just label wise you have it labeled as which version of Ubuntu is installed?

As far as it being top level? Do you mean that the root partition needs to be sda1? Or does that even matter?

Also, I'm still getting the error about no root system.

Do I need to change the mount point? If so, how do I do that?

Since it's going to be UEFI. I don't need the swap partition, right?


[ATTACH=CONFIG]269229[/ATTACH]

---

### Post by oldfred on 2016-05-22
The installer does not know what you did with gparted. And it does not read the labels.
So you have to click change, choose ext4, choose / for / partition.
And same for /home. 
But if a re-install where you have data in /home you choose ext4 but make sure NOT to tick format or it erases you /home data.
If you already have created swap you do not have to tell installer, it finds it automatically.

---

### Post by anon24 on 2016-05-22
I guess I forgot to make a swap partition before. Does this look right now?

[ATTACH=CONFIG]269230[/ATTACH]

Also, do I need to change UEFI to /boot?

---

### Post by anon24 on 2016-05-22
Alright, so I went through the install process. It said that the install was successful. How do I get Ubuntu to boot up? I saw in one of the tutorials it said something about changing the boot order? Do I have to go into "Try Ubuntu" in order to change the boot order?

Here is what I see when I am in the BIOS and when I hold down F11 at startup.
[ATTACH=CONFIG]269231[/ATTACH][ATTACH=CONFIG]269232[/ATTACH]

---

### Post by oldfred on 2016-05-22
You have two ubuntu, one is shim and the other grub. 
Shim is the version of grub for secure boot but will work with Secure boot off. Not sure which is which.

Does the ubuntu entry boot.

And you do show the ubuntu entries in UEFI to choose it first. 
What brand model system? Some need a work around to let you have a grub way to boot by default.

---

### Post by anon24 on 2016-05-22
MSI GS70 2QE

Actually, one of them is booting! I held F11 and selected one.
I guess that I have to hold down F11 in order to boot Ubuntu? It says no Media present if I don't.
Here is what efibootmgr says in Ubuntu (Low Latency):

[ATTACH=CONFIG]269242[/ATTACH]

Also, for some reason my wifi connection is not working. It keeps giving me an error.

---

### Post by oldfred on 2016-05-22
That is right I had forgotten Studio uses Low Latency kernel.

Some other MSI systems that should be similar.
 [SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912) 

If issues with wi-fi best to start a separate thread with that in title and model of wireless chip.
The users that know details on wi-fi issues want a script run to see all the details.
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
Wireless script if wired working :
wget -N -t 5 -T 10 [https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script](https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script) && chmod +x wireless_script && ./wireless_script
[http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222](http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222)
[http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385)
Wireless issues Broadcom BCM4312 wireless card on Dell Mini
[http://ubuntuforums.org/showthread.php?t=2239022](http://ubuntuforums.org/showthread.php?t=2239022)

---

### Post by anon24 on 2016-05-23
I don't see anyone that had the same problem in any of those threads. It's really a minor inconvenience as I can boot Ubuntu. I'm wanting it to boot to grub instead of having to hold F11 down on startup.

Also, strange, I just booted Ubuntu again. The wifi issue seems to have resolved itself.

---

### Post by oldfred on 2016-05-23
If you go into UEFI can you reorder boot to have ubuntu entry first?
Some allow that, others have modified UEFI to only boot by description and only valid description is "Windows Boot Manager". But we can often make work arounds to allow a fallback or hard drive entry work or edit BCD which requires boot into Windows & UEFI one time boot into Ubuntu from Windows setting of UEFI.

This says he was able to change in UEFI boot order.
[http://ubuntuforums.org/showthread.php?t=2218742&p=12997897#post12997897](http://ubuntuforums.org/showthread.php?t=2218742&p=12997897#post12997897)

---

### Post by anon24 on 2016-05-24
Sweet, thank you! That got it working! I had read that one, but somehow missed where the OP talked about that extra UEFI menu.

---

