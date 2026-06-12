---
title: "Dual Boot - Fail to boot after WINDOWS update"
date: 2019-08-28
forum: Ubuntu/Debian BASED
---

### Post by frank105 on 2019-08-28
Hi again - SHOCKING NEWS - Windows Update results in failure to boot!!!
I have a dual boot Win 10/ Peppermint Linux laptop
Toshiba Satellite A665 with 8gb ram.

Everybody was happy until last weekend when I broke down and let Windows install their big May (I think) update.  Guess what - reboot gives me:
	Error:  Unknown file system.
	Entering rescue mode...
	Grub rescue>

So reading around I did find some answers.  So I typed Set to show my current setup
	Grub rescue>set
	cmdpath=(hd0)
	prefix=(hd0,msdos7)/boot/grub
	root=hd0,msdos7

Then after a bit of testing with trial and error I found that typing:
	Grub rescue>set prefix=(hd0,msdos6)/boot/grub
	Grub rescue>insmod normal
	Grub rescue>normal

Boots right into Grub.  

I have rebooted this way a couple more times and Windows has completed this glorious upgrade...  But in all of my research - I found that this is the answer to get in - but I can't find how do I fix my pc so it just boots to grub?  

Oh and - for fun I downloaded the latest Win 10 iso and did a usb boot to try and have it try to repair the boot&#8230; but the usb fails to boot.  An older version of Win iso boots but the repair doesn&#8217;t find any problems.  

Anyway - thanks as always!

Frank

---

### Post by howefield on 2019-08-28
Thread moved to the "*Debian/Ubuntu Based*" forum.

---

### Post by oldfred on 2019-08-28
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by frank105 on 2019-08-28
Hey Fred - I should have known - Grub troubles you gotta ask Fred.

I will get ya that report in a few. 

Thanks in advance,

Frank

---

### Post by frank105 on 2019-08-28
Here is a pastelink of the results 
[URL="http://paste.ubuntu.com/p/3wWGyfDW4V/"]http://paste.ubuntu.com/p/3wWGyfDW4V/
[/URL]
You can ignore anything SDC related - I am trying to copy over any important info to my external drive as we speak - just in case. 

Soooo - my simple cause of the problem - check my work to see if I learned anything yet - I think the Win 10 update added a partition to my drive.  Since this laptop is older and does not use GPT or UEFI the bios boot is based on the partition number.  By adding the partition - the numbering is all off?  Actually that doesn't sound exactly right - since it seems it is trying to find Grub on msdos7 and it is actually on msdos6.  You would think adding a partition it would be looking on 5 and now it is number 6?  Anyway - I thought I finally knew something...

OH - one more thing - I did this from the local install of Peppermint.  I am guessing this is okay?  If you need me to boot to a usb ubuntu I can. 

Thanks again,

---

### Post by oldfred on 2019-08-28
Looks like UEFI system, but everything installed in BIOS boot mode.

With BIOS, Windows since Windows 7, normally updates partition table & "forgets" to include the Linux partitions. It looks like yours are still there. Maybe they finally fixed that??

But now Windows seems to want a new recovery partition just after the main install. Recently saw one user who could not boot & it may have been that start of his Linux partition was moved.
You have all your Linux partitions inside the extended (no unallocated showing). 
But is your sda5 corrupted?

And yes it seems strange that grub in MBR and comment in fstab refer to sda7 as /.

If you can manually boot into your install, you can just reinstall grub to MBR. Otherwise use Boot-Repair's advanced options (choose install & MBR) to reinstall grub. Boot-Repair's autofix wants to install grub to MBR of all drives which most do not want. Wehn only one drive that is ok.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo parted -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by frank105 on 2019-08-29
Thanks Fred,

Hmm...  I was poking around and couldn't mount sda5... Not sure what is on there or what I had it for?  I tinker too much.

I ran fsck on it - 
[INDENT] $ sudo fsck /dev/sda5
[sudo] password for cupcake: 
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
/dev/sda5: clean, 11/2056192 files, 174088/8224512 blocks
[/INDENT]

And here is my partition table [INDENT]sudo parted -l
Model: ATA WDC WD10JPVX-22J (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  577MB   576MB   primary   ntfs            boot
 2      577MB   63,5GB  62,9GB  primary   ntfs
 3      63,5GB  64,4GB  970MB   primary   ntfs            diag
 4      64,4GB  1000GB  936GB   extended
 5      64,4GB  98,1GB  33,7GB  logical   ext4
 6      98,1GB  991GB   893GB   logical   ext4
 7      991GB   1000GB  9021MB  logical   linux-swap(v1)
[/INDENT]

I would like to mount it and see what is there but... on with the first problem.  
I ran[INDENT]cupcake@cupcake-Satellite-A665 ~ $  sudo grub-install /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.
cupcake@cupcake-Satellite-A665 ~ $  sudo update-grub 
Generating grub configuration file ...
Found background image: grub-background.png
Found linux image: /boot/vmlinuz-4.15.0-23-generic
Found initrd image: /boot/initrd.img-4.15.0-23-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 10 on /dev/sda1
done
[/INDENT]

Gonna reboot and let ya know how it goes!!

Thanks again,

---

### Post by frank105 on 2019-08-29
Rebooted and tried both OS's and all is well in the world. 

Still going to look into that sda5 issue.  

Fred - thanks as always for your help!   You are the grub guru

Regards,
Frank

---

### Post by frank105 on 2019-08-29
Fred - I am not sure you are still following this thread - thanks as always 

But - I did sorta mount sda5 and all that is in there is lost+found folder that I am not allowed to open?  even as root?  I am going to guess though that the partition is part of a plan that I probably aborted a while back... and I forgot to write down what I was doing.  If you are following this and have thoughts on what I might try to confirm this suspicion - I am all ears and appreciative.

Frank

---

### Post by oldfred on 2019-08-29
It sounds like just a formatted partition without data.
Not sure then if Windows resized it and fsck repaired it, but erased any data, or you never had any data in it?

---

### Post by frank105 on 2019-08-31
Fred

Thanks for the followup.  Yep - really looks like an empty partition.  I was up to something... but forgot all about it.  

Chat with ya the next time I mess GRUB up.  Until then - take care,

Frank

---

