---
title: "OS Specific Grub"
date: 2016-02-06
forum: Ubuntu, Linux and OS Chat
---

### Post by obsidian3 on 2016-02-06
Hey guys, I have a question about the grub bootloader.

Pretty much all the popular linux distributions come with their own customized grub bootloader. Some have such customizations that can't even be accomplished using Grub Customizer.

So when you have multiple distros installed on your desktop, the last installed distro will always overwrite the grub with their custom grub look. I always like to use multiple linux distros and sometimes install new ones that come out.

Either way, my favorite custom grub menu is from Deepin, it's awesome looking and can't be obtained by simply using Grub Customizer.

Let's say I'm going to install a new linux distro and during the install process, it doesn't give me the option to not install grub then overwrites my Deepin grub to theirs. Does anyone know a way to boot into Deepin and manually set that custom grub bootloader to be used instead of the newly installed one? Or does it get completely overwritten and it's not possible to revert back?

Only way I see this working is to install Deepin again.

Please don't suggest just using virtual machines instead. I like having a multiple distro boot.

---

### Post by kansasnoob on 2016-02-06
**[COLOR="#FF0000"]Do not jump into trying anything until you've taken time to fully learn and understand what you're doing![/COLOR]** But here's a few beginning hints.

Before we can give any advice at all we really need to know if you have a standard BIOS system or a newer UEFI system. I'm guessing standard BIOS with msdos partition tables on all drives, you can find out by running:

```
sudo parted -l
```

eg;

```
lance@lance-desktop:~$ sudo parted -l
[sudo] password for lance: 
Model: ATA WDC WD1600AABB-5 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
**Partition Table: msdos**

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  105GB  105GB   primary   ext4            boot
 2      105GB   160GB  54.5GB  extended
 8      105GB   123GB  17.5GB  logical   ext4
 7      123GB   141GB  17.5GB  logical   ext4
 6      141GB   158GB  17.3GB  logical   ext4
 5      158GB   160GB  2136MB  logical   linux-swap(v1)


Model: ATA WDC WD800BB-63JK (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
**Partition Table: msdos**

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  76.7GB  76.7GB  primary   ext4            boot
 2      76.7GB  80.0GB  3289MB  extended
 5      76.7GB  80.0GB  3289MB  logical   linux-swap(v1)


Model: ATA ST3160318AS (scsi)
Disk /dev/sdc: 160GB
Sector size (logical/physical): 512B/512B
**Partition Table: msdos**

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  137GB  137GB   primary   ext4            boot
 2      137GB   160GB  23.0GB  extended
 6      137GB   157GB  20.0GB  logical   ext4
 5      157GB   160GB  3040MB  logical   linux-swap(v1)

```

In that specific scenario the Ubuntu system on /dev/sda1 is always in control of booting because if I install another OS on that drive I choose to install it's grub to the pbr rather than the mbr - eg; /dev/sda6 thru /dev/sda8. And I likewise select the proper mbr or pbr for the installations on the other two drives so they'll be bootable if I either change the boot order in BIOS or if I remove any of the other drives.

This can be accomplished with Ubuntu or Debian during installation with a bit of learning, or it can be corrected after installation using this command:

```
sudo dpkg-reconfigure grub-pc
```

I'm no longer knowledgeable of any distros other than Ubuntu and Debian so things may be totally different in Deepin.

If you were to use [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") to create a boot info script and post that info here we could then give more accurate info, **[COLOR="#FF0000"]but only use it to create the boot info NOT TO REPAIR THE BOOT![/COLOR]**

---

### Post by obsidian3 on 2016-02-07
Thanks for your reply.

Here is my _sudo parted -l_ results.  Sda is my Windows drive. Sdb is my Mac drive. And sdc is my Linux drive. My boot drive is sdc.

```


Model: ATA OCZ-ARC100 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  120GB  120GB  primary  ntfs         boot


Model: ATA WDC WD3000HLFS-7 (scsi)
Disk /dev/sdb: 300GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name                  Flags
 1      20.5kB  210MB  210MB  fat32        EFI System Partition  boot, esp
 2      210MB   299GB  299GB  hfs+         Computer
 3      299GB   300GB  650MB  hfs+         Recovery HD


Model: ATA OCZ-ARC100 (scsi)
Disk /dev/sdc: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  240GB   240GB   extended                  boot
 5      2097kB  70.0GB  70.0GB  logical   ext4
 6      70.0GB  72.0GB  2000MB  logical   linux-swap(v1)
 7      72.0GB  142GB   70.0GB  logical   ext4
 8      142GB   172GB   30.0GB  logical   ext4
 9      172GB   181GB   8589MB  logical   ext4
10      181GB   196GB   15.0GB  logical   ext4


```

Deepin is Debian based.

> This can be accomplished with Ubuntu or Debian during installation with a bit of learning
By this, you mean there is always a way to install a debian or ubuntu based distro without the grub? I've noticed anything using the Ubuntu type installer doesn't give the option.

> sudo dpkg-reconfigure grub-pc
So I can install my new distro, boot up Deepin and run the command to reconfigure the deepin grub? If that's true, this is the perfect solution.

---

### Post by kansasnoob on 2016-02-07
> By this, you mean there is always a way to install a debian or ubuntu based distro without the grub? I've noticed anything using the Ubuntu type installer doesn't give the option.

With the Ubuntu installer you only see the option when using advanced partitioning, which they call "Something Else". Towards the bottom of that screen you can select where to install grub.

Using the standard Debian installer (text based) you can always select where to install grub or choose not to install it anywhere.

But I see the Mac drive has an EFI system partition so hold on and let's get some more advice here. I've fiddled with UEFI a little bit but not enough to be proficient at it, and I've never messed with Mac at all. I'd think it's going to be fairly imperative that you install all other OS's in standard BIOS mode. Do you usually just disconnect the Mac drive when installing to the others?

---

### Post by kansasnoob on 2016-02-07
> So I can install my new distro, boot up Deepin and run the command to reconfigure the deepin grub? If that's true, this is the perfect solution. 

Yes, you could hand control back over to Deepin using that method. But you also have to repeat that in each Linux OS with grub 2 because each time a kernel update (or some others) trigger updating grub dpkg remembers where it was installed during installation and messes things up again.

Just as examples look at my drives above.  The OS on sda1 is my main OS so it's grub is installed to /dev/sda and that drive is set to boot first in BIOS. The operating systems I install on sda6, 7, & 8 get their grub installed to the same partition the OS is installed on. While booted into the OS you can check where it's / is just by running df. So if I'd goofed and installed grub to the mbr (sda) while replacing the OS on sda6 I'd run dpkg-reconfigure grub-pc and change it to be installed on /dev/sda6.

So, yeah I'd boot into Deepin first and use that command to install grub to that drives mbr (it would be interesting to see what a boot info summary says about the mbr of the Windows drive). Then once Deepin is in charge of boot I'd boot each Linux OS and use that command to place its grub on its own / partition.

My biggest concern is that the Mac drive be left alone entirely!

---

### Post by obsidian3 on 2016-02-07
> With the Ubuntu installer you only see the option when using advanced  partitioning, which they call "Something Else". Towards the bottom of  that screen you can select where to install grub.
Ah, well shoot. Never noticed that then.

> Using the standard Debian installer (text based) you can always select  where to install grub or choose not to install it anywhere.
Yeah, Debian always gives you that option. I think it's the very last option.

> Yes, you could hand control back over to Deepin using that method. But  you also have to repeat that in each Linux OS with grub 2 because each  time a kernel update (or some others) trigger updating grub dpkg  remembers where it was installed during installation and messes things  up again.
Eh, that perfect solution deflated a little then, haha. But as long as I can skip the grub install then I should be fine, the ubuntu installer was the main one I didn't know did allow skipping that.

> Just as examples look at my drives above.  The OS on sda1 is my main OS  so it's grub is installed to /dev/sda and that drive is set to boot  first in BIOS. The operating systems I install on sda6, 7, & 8 get  their grub installed to the same partition the OS is installed on. While  booted into the OS you can check where it's / is just by running df. So  if I'd goofed and installed grub to the mbr (sda) while replacing the  OS on sda6 I'd run dpkg-reconfigure grub-pc and change it to be  installed on /dev/sda6.
I hear ya, I believe all my grub bootloaders are on their own / partitions. That's a lot of good information though, thank you.

> So, yeah I'd boot into Deepin first and use that command to install grub  to that drives mbr (it would be interesting to see what a boot info  summary says about the mbr of the Windows drive). Then once Deepin is in  charge of boot I'd boot each Linux OS and use that command to place its  grub on its own / partition.
Everything currently is set up correctly, just wanted to make sure before I installed a another distro. Tomorrow, I'm going to be adding Mint to the bunch which uses that similiar ubuntu installer so I'll go into advanced partitioning like you suggested to avoid installing grub. If I run into grub issues though, I'll use your suggestions about reconfiguring the other distro grubs.

> Do you usually just disconnect the Mac drive when installing to the others?
Nope.

> My biggest concern is that the Mac drive be left alone entirely!
Hah, you are absolutely correct. I forgot to mention that's actually fine though because Yosemite doesn't work with my current gpu, waiting on my new gpu to add that to the mix.

---

### Post by kansasnoob on 2016-02-07
I had to perform a test install of the proposed 14.04.4 image which may be released next week so I took a couple of pics. I installed the OS on /dev/sda6 so also installed it's grub to /dev/sda6:

[ATTACH=CONFIG]267177[/ATTACH]

[ATTACH=CONFIG]267178[/ATTACH]

Somewhat unrelated but since I have a swap partition on each drive so each drive can operate independently of the other(s) I had to select "Do not use" from the drop down menu:

[ATTACH=CONFIG]267179[/ATTACH]

That also comes in handy for USB installs where I absolutely don't want any existing partitions on the internal drive(s) messed with. I also use that if I'm performing an installation where I absolutely do not want the existing EFI system partition to be touched. I'm still learning UEFI:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I've gained more than a few gray hairs struggling with UEFI, maybe it's true that you can't teach old dogs new tricks ;)

---

### Post by LostFarmer on 2016-02-07
The ubuntu installer if booted in EFI mode , you have NO option.  It will install grub efi files in the boot drive EFI partition.  It does not matter what you select.  In mbr boot then your selection is honored.

On my 2 ASUS laptops, after having to replace the bios chip due to making changes to the efi boot firmware, I only install all new linuxs in legacy/mbr mode and select to put grub in its partition. Then boot into the efi installed linux and run update-grub. 

 I do the last differently but do not advice my way, I selected to have a small ext2 partition that contain the content of a normal boot/grub files and manual edit grub.cfg, and purge all installs of grub.

I do have a Macbook Pro early 2011 and I can NOT install linux in mbr mode ( no display). So the above will not work.  Does not matter due to the small hdd size. 

You can make a copy of the /EFI/ [Deepin folder] , and after new linux install , copy it back to EFI partition.  Boot into deepin and run 'update-grub'. If Deepin does not use /EFI/ubuntu name , you can just re-register the deepin efi entire as first boot efi option. You can use mac OS program 'bless' or linux 'efibootmgr'.  
My understanding some linux want to make there own efi partition and that would only require putting deepin efi entire as first.                                                                                                   

as kansasnoob stated in his first post , understand what is being done before you do it.
     kansasnoob I'm and old dog of 63 and have fun learning new tricks. :)

---

### Post by obsidian3 on 2016-02-09
Thanks Kansasnoob for your continued help. I appreciate your information. I've been installing some test virtual machines to fully understand the grub, mbr, efi and everything. Thanks for your UEFI link.

> I do the last differently but do not advice my way, I selected to have a  small ext2 partition that contain the content of a normal boot/grub  files and manual edit grub.cfg, and purge all installs of grub.
Even though you don't advise to do that, it seems like a great idea. To uninstall the grub from every other distribution but only keep the one you use. I wouldn't make it on an entirely different partition but just keep my Deepin grub and purge the rest (because I believe I have all the other distro grubs still installed on their corresponding partition). How come you don't advise to do that or would what I'm thinking of be perfectly fine?

> as kansasnoob stated in his first post , understand what is being done before you do it.
I agree! :mrgreen:

---

### Post by LostFarmer on 2016-02-09
> Even though you don't advise to do that, it seems like a great idea. To  uninstall the grub from every other distribution but only keep the one  you use. I wouldn't make it on an entirely different partition but just  keep my Deepin grub and purge the rest (because I believe I have all the  other distro grubs still installed on their corresponding partition).  How come you don't advise to do that or would what I'm thinking of be  perfectly fine?
  I would have no problem ,  just as long as you remember that you can not delete the Deepin install without intalling grub on a different distro first.  Or you will not be booting with out a pain.

There are may ways to do things.  Just to let you know- even if you install the other distribs in MBR mode ,when you boot them from Deepin gurb, they will be booting in EFI mode. When they do a kernel update, it is likely if grub is not purged , it will do a grub-efi update.  When a kernel us updated , part of the process is to run update-grub to put new kernel in grub.cfg. 

I do not know what folder name Deepin uses in the efi partition. If it uses its own name , depending you your comps bios/firmware , you could put it first by going into the bios/firmware settings.  Could be easiest and safest.  I notice Deepin is Debian based so it is not likely the folder is /efi/ubuntu. Some comps it is easy to change EFI option and others ?.

You also must remember when any other distro updates its kernel , you will need to run 'update-grub' from Deepin to get the new kernel in grub/cfg.

---

### Post by oldfred on 2016-02-10
With Mulitple installs and/or multiple drives I like to run Boot-Repairs Summary Report. It is better than the older bootinfoscript and actually includes all of a somewhat updated version of bootinfoscript. I still run bootinfoscript as part of my rsync backup, just to have latest data.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

While Boot-Repair usually fixes issues with most standard type installs, the more complex the configuration the less likely the auto fix will work. But the advanced modes can simplify for newer users some of the updates like when a chroot is needed.

Oldfred likes changes and solving issues.
When doing his new build in 2006 he heard of this new UEFI thing. But UEFI motherboard was server only, over $3000 and did not support PC operating systems. When UEFI started with Windows 8, oldfred was thinking of replacing 2006 system, and started converting all new drives to gpt for BIOS boot but with an ESP, so easily converted to UEFI boot. But a new SSD on old system made it so good that could not justify new system. Finally last year built new UEFI system.

---

