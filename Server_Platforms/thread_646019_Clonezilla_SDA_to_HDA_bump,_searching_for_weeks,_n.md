---
title: "Clonezilla SDA to HDA bump, searching for weeks, no answers."
date: 2007-12-20
forum: Server Platforms
---

### Post by amaurynieto on 2007-12-20
Hello All - hit a brick wall, and was really looking forward
to your assistance, since I've been unable as of yet to find the answer
to my quandary:

I have an 80 gig SATA Hard Drive, and I've partitioned it threefold:

SDA1 - Windows XP (NTFS)
SDA2 - Storage (documents, and so on, FAT32)
SDA3 - Ubuntu 7.10 (ext3).

I've been successful in creating and restoring the images for SDA1 and SDA3 for whenever I need
to reset, or for backup purposes.

However, what i've been trying to do is to migrate the Ubuntu partition (SDA3) into an IDE disk (HDA)
on a different computer, with no partitions, and a different disk capacity.

I utilized a somewhat cryptic utility called "cnvt-ocs-dev" on my previously saved Ubuntu image folder COPY (i wasn't
dumb enough to mess with the real thing) and it changed the target device to hda3 instead of sda3. 

But when I try to deploy the image folder onto the disk, it says it's doing it, 
takes less than 2 seconds, says it's done, and does absolutely nothing.

When booting, I get GRUB GRUB GRUB GRUB, fills the screen, and does nothing.

I realize that by trying to restore only one partition onto a new disk, I am nullifying 
the MBR for the other two partitions which aren't there in the target HDA disk, but all I really
want is for SDA3 image partition to be the only partition on another HDA disk.

Is there a way I can do this? I've been racking my head for weeks now, and have been unable
to migrate because of all the information I stand to lose on my previously installed SDA3.

I don't even know that it's possible even if it were another sata hard-drive. But I've found scarce
information in few and far-between places on the net....

Could you please point me in the right direction? I'd be immensely grateful.

---

### Post by logos34 on 2007-12-20
Use [Partimage.]("http://www.partimage.org/Partimage-manual_Usage")  It's pretty straightforward.  Or the [dd command]("http://www.brunolinux.com/02-The_Terminal/The_dd_command.html").  And remember to [install grub to the mbr]("http://ubuntuforums.org/showthread.php?t=224351") of the target disk.

For example, in the case of dd:

> Copy one hard disk partition to another hard disk:

dd if=/dev/sda3 of=/dev/hda1 bs=4096 conv=notrunc,noerror

You want to copy sda3 to hda1. If partition hda1 doesn't exist, dd will start at the beginning of the disk, and create it.

DD copies everything--empty sectors included--so it takes a while.  So you may want to use Partimage instead, which reads only the used portion of the disk.

---

### Post by amaurynieto on 2007-12-23
Just to touch base here, I finally found a viable answer (which is probably an automated method of the reply I received), but it's a great deal simpler, and also has many more options.

It's called reloc-img - it's a great tool created by a fellow called Spiros Georgaras from Greece, for his Clonezilla Sys Resc CD, which you can find at:

[http://clonezilla-sysresccd.hellug.gr/index.html](http://clonezilla-sysresccd.hellug.gr/index.html)


Really quite the find. Most complete rescue CD I've found to date. It has more than the sysresccd. It has xp recovery, data wipers, super grub disk, clonezilla, reloc-img, and a plethora of other tools. It can be run on CD, or on USB. Impressive stuff.

Cheers, A.

---

### Post by HermanAB on 2007-12-23
Hmm, well, why on earth do you want to migrate an Ubuntu system in the first place?  It is much easier to just re-install and then you have the newest version too.  The only thing you need to copy is the data.

Cheers,

Herman

---

### Post by logos34 on 2007-12-23
> **amaurynieto said:**
> Just to touch base here, I finally found a viable answer (which is probably an automated method of the reply I received), but it's a great deal simpler, and also has many more options.

It's called reloc-img - it's a great tool created by a fellow called Spiros Georgaras from Greece, for his Clonezilla Sys Resc CD, which you can find at:

[http://clonezilla-sysresccd.hellug.gr/index.html](http://clonezilla-sysresccd.hellug.gr/index.html)


Really quite the find. Most complete rescue CD I've found to date. It has more than the sysresccd. It has xp recovery, data wipers, super grub disk, clonezilla, reloc-img, and a plethora of other tools. It can be run on CD, or on USB. Impressive stuff.

Cheers, A.

Yep, I have it.  Pretty nifty--it's got apps up the wazoo.  Only UBCD has more I think.

---

### Post by amaurynieto on 2007-12-27
> **HermanAB said:**
> Hmm, well, why on earth do you want to migrate an Ubuntu system in the first place?  It is much easier to just re-install and then you have the newest version too.  The only thing you need to copy is the data.

Cheers,

Herman

Herman - I sometimes get pretty busy, and it takes far less to restore a Clonezilla Image (less than 5 minutes, quite literally), instead of 30 minutes for a clean install, plus, I have an ATI card, so, re-download the fglrx if you want Catalyst 7.11, or use Envy, then I use a lot of different programs, Python scripts that require lots of libs, at very best, restore all your apps with APTonCD (which itself is a form of restore), and there went another 20 minutes of your time. 

Not to mention taking the time to "migrate" your home directory. Or taking the time to move the VDI's from VirtualBox onto somewhere else. 

This on an AMD 64 x2 with 2 gig ram and 512 ATI card... So, indeed, this is why I was bumped and decided to invest the hour it would've taken me to clean re-install in googling, posting, and implementing the answer i found, and indeed, sharing with the rest of the community.

Another good reason is if you're a systems integrator, or in an IT position as some of us are, or have been at certain companies, where time again, is a factor, and manpower and/or support hours are a profit margin issue.

Bottom line is, I got it working wonderfully, appreciate the feedback, and to me, Nothing beats being able to boot SYS RESC CD from Spiros Georgaras on a USB disk, firing up my dvd rom, waiting 5 minutes and having my identical system, just as I left it in case I mess something up later on in my laptop, or if I want to have the same system at work than I do at home without investing insane amounts of time.



Cheers!

---

