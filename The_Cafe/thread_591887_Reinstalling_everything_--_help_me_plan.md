---
title: "Reinstalling everything -- help me plan"
date: 2007-10-25
forum: The Cafe
---

### Post by p_quarles on 2007-10-25
Okay, so a short two weeks after doing a fresh install of 7.10, I'm going to reinstall everything. Current setup is a dual-boot with Kubuntu 7.10 and Vista Home Premium. 

Reasons:
1) I rarely use Windows (I do need it, however), and its current partition is too large.
2) For those rare occasions, I'd rather have XP.
3) I need a separate home partition for an upcoming project. 
4) I have a dual-core Pentium D, and I've been sold on moving up to the 64-bit OS. 
5) The upcoming project is re-ripping my CD collection to FLAC, which will benefit from 64 bits.

The plan is to turn my current Linux partition into the new /home partition, and using the space freed up from Windows as the new root filesystem. That much is easy, but I could use advice/suggestions on a couple points.

1) What's the easiest way to get Firefox up-and-running? Should I go with the 32-bit workaround, or should I use the 64-bit version with nspluginwrapper and 64-bit generic Java? I understand they both work, but which is the least headache inducing?

2) My copy of XP is an old OEM reinstallation disk that came with my previous desktop (now a Debian server). I'm not entirely sure if I'm *supposed* to install this on a different machine, but I'm not going to feel bad about it, given that it is mine, and I'll only be running on one machine. My question is: is this going to cause any WGA headaches? If it might, I'm happy to keep Vista. This is an old disk, as I said, and I'd need to waste a few hours installing the latest service pack if I decided to use it. 

[mods -- feel free to move this if you can think of a better place for it. I couldn't :) ]

---

### Post by FuturePilot on 2007-10-25
1. Java 7 has a 64 bit browser plugin (and it's GPL!) Not sure what you would do for Flash. You could go with Gnash, but I've heard that's still buggy at best.

2. Not entirely sure about how that would turn out.

---

### Post by p_quarles on 2007-10-25
> **FuturePilot said:**
> 1. Java 7 has a 64 bit browser plugin (and it's GPL!) Not sure what you would do for Flash. You could go with Gnash, but I've heard that's still buggy at best.
Did not know about Java 7. I was thinking of going with Blackdown Java, but I'll look into this as well. 

Flash is the easy part, though. The Gutsy repos will install Flash with the nspluginwrapper automatically. Gnash is completely out: I've used it, and it's not quite "there."

---

### Post by wolfen69 on 2007-10-25
if the xp disk is a restore disk, you can only use it on the original computer that it came with. it wont even let you install.

---

### Post by p_quarles on 2007-10-25
> **wolfen69 said:**
> if the xp disk is a restore disk, you can only use it on the original computer that it came with. it wont even let you install.
I would much prefer that it simply refuse to install rather than refuse to verify a couple days later. I'll give it a try and see how it goes.

---

### Post by Eric the Grey on 2007-10-26
Step 1:  Make a backup of anything you need to keep (documents, etc)
Step 2:  Make a list of everything you'll need to download and re-install.
Step 3:  ADD THAT LIST to your backup!  It does no good sitting on the desktop you're about to format away... :lolflag:

Seriously, I'd sit and plan out your partitions first off.  Decide how much space you'll need for XP and install that first.  Windows seems happiest if it is the first thing there, and it will not offer to dual boot after it installs.

Beyond that, 

:cool: Eric the Grey

---

### Post by p_quarles on 2007-10-26
> **Eric the Grey said:**
> Step 1:  Make a backup of anything you need to keep (documents, etc)
Step 2:  Make a list of everything you'll need to download and re-install.
Step 3:  ADD THAT LIST to your backup!  It does no good sitting on the desktop you're about to format away... :lolflag:

Seriously, I'd sit and plan out your partitions first off.  Decide how much space you'll need for XP and install that first.  Windows seems happiest if it is the first thing there, and it will not offer to dual boot after it installs.

Beyond that, 

:cool: Eric the Grey
Way ahead of you. Everything important is backed up in several different places, I have a convenient method of cloning an installation ([link]("http://ubuntuforums.org/showpost.php?p=3537917&postcount=2")), and I have a GRUB disk if need be. Thanks, though.

---

### Post by p_quarles on 2007-10-26
If anyone is interested, the XP installation failed. The EULA on the installation disk didn't mention anything about the OEM, so I don't think that's the problem. It failed when it tried to read my hard drive. The box it came with is a few years old, with an IDE hdd. I used gparted to make an ntfs partition on the new box's SATA drive, but it didn't recognize it. 

Reinstalling Vista as we speak, and hoping it doesn't mess with my careful partitioning. 

Sigh. All this for a couple games and the ability to test web sites with Explorer and Safari. 

Haven't yet gotten around to installing 64-bit Ubuntu, so if anyone has any last minute advice on the Firefox issue, I'll be here on my laptop. :)

---

### Post by p_quarles on 2007-10-27
D'oh. Vista failed to install as well. I'm not hugely surprised, since it's already well-known that Vista and gparted don't really agree about what an ntfs partition is. 

Anyway, Kubuntu 7.10 x86-64 is now up and running. I'd still like to have Windows available, and left a chunk of space open for it. Any suggestions about how to format that empty space without wiping the drive are much appreciated.

---

### Post by -grubby on 2007-10-27
> **p_quarles said:**
> D'oh. Vista failed to install as well. I'm not hugely surprised, since it's already well-known that Vista and gparted don't really agree about what an ntfs partition is. 

Anyway, Kubuntu 7.10 x86-64 is now up and running. I'd still like to have Windows available, and left a chunk of space open for it. Any suggestions about how to format that empty space without wiping the drive are much appreciated.

how about formatting the Windows partition to FAT32?

---

### Post by p_quarles on 2007-10-27
> **nathangrubb said:**
> how about formatting the Windows partition to FAT32?
I kinda doubt that would work with Vista, since it's pretty picky about it's filesystem. I'll give that a try with my XP disk, though. Maybe I can fool it into thinking that I'm upgrading from Win <shudder> ME.

---

### Post by FuturePilot on 2007-10-27
> **p_quarles said:**
> Win <shudder> ME.
:twisted:

---

### Post by koenn on 2007-10-27
> **p_quarles said:**
> If anyone is interested, the XP installation failed. The EULA on the installation disk didn't mention anything about the OEM, so I don't think that's the problem. It failed when it tried to read my hard drive. The box it came with is a few years old, with an IDE hdd. I used gparted to make an ntfs partition on the new box's SATA drive, but it didn't recognize it.)
Windows XP Setup doesn't know how to deal with SATA. Note that during setup, you're prompted to "Press F6 if you need to load 3th party drivers for disk subsystems" or something along those lines. That's where you'd insert (a floppy with) drivers for scsi disks, raid controllers, or, in this case, SATA disks (which are somewhat similar to scsi disks)
In true MS-DOS style, XP expects those drivers to be on your A:\ drive.   USB-drives and CD's won't work, but there are workarounds, such as remastering the setyp CD to include the drivers. Google knows  where to find info. 

As for partitioning, when you repartition with a non-windows system (linux, gparted, ..) for use with windows, it's usually best to leave some unpartitioned space, and let Windows setup detect and format it while you're installing Windows. 

And legally, you can only use an OEM Windows on the machine it came with. Just so you know  ;) It shouldn't give any trouble with Product Activation and WGA - as long as you don't modify too much gardware afterwards, and don't need to activate more than 3 times.
A common trick is to save the %windir%\system32\wpa.dbl - it's where the product activation is registered, and it can save you from having to re-activate after a re-installation (if there haven't been too many hardware changes in between)

---

### Post by p_quarles on 2007-10-27
@koenn: Thanks very much. Just what I was looking for. If remastering doesn't work, I s'pose I can always throw a floppy drive onto the desktop box and work from there.

---

### Post by koenn on 2007-10-27
you're welcome.
now, let's  hope it works.

---

### Post by daynah on 2007-10-27
I'd work very hard on the XP one, even though it's a bit more work with the SATA. If youre doing this for games, then you want all the memory you can get. :)

---

### Post by p_quarles on 2007-10-27
> **daynah said:**
> I'd work very hard on the XP one, even though it's a bit more work with the SATA. If youre doing this for games, then you want all the memory you can get. :)
Heh, yeah, that's the plan. Particularly after my attempt to use the Vista recovery disks resulted in overwriting my partition table (even though it failed to install, I somehow ended up with *two *ntfs partitions and a bunch of free space). 

The gaming thing is actually kind of secondary. I'm trying to start freelancing in web design, and I actually *need *to be able to test things in Explorer and Safari. I'd like to have the games, but if nothing works I can always use Virtualbox to get the necessary stuff.

---

### Post by immrlizard on 2007-10-27
> **p_quarles said:**
> D'oh. Vista failed to install as well. I'm not hugely surprised, since it's already well-known that Vista and gparted don't really agree about what an ntfs partition is. 

Anyway, Kubuntu 7.10 x86-64 is now up and running. I'd still like to have Windows available, and left a chunk of space open for it. Any suggestions about how to format that empty space without wiping the drive are much appreciated.


Does your machine have the ability to boot from different drives as per a selection at  post time?

That is how I got around that problem.   I have xp on one drive and ubuntu on another and when it gets into the post there is a place to choose the drive it is supposed to boot from.   I do not like to mix and match on one drive.   History has shown that MS writes software that is defective by design and I wouldn't want to lose my ubuntu partition because of a problem in windows.    

I haven't tried the 64 bit version yet.   One day though.   It has been too nice outside to spend too much time playing with that.   Winter is on the way.   Maybe then.   I tried the 7.04 version of ubuntu studio and really liked it.   I have the 7.10 version ahead of the list for now.   I also am looking to add yet another drive and have a centos choice too since so many companies are using red hat now.   I may have to invest in another case for that though.   It looks to be a busy winter

---

### Post by p_quarles on 2007-10-27
Yeah, the BIOS does have that ability, it just doesn't have another hard drive, and I'm not exactly short on space at the moment. 

Honestly, I've been dual-booting for some time, and have never had a problem with Windows even noticing that it wasn't the only OS on the system. The only problem I've ever heard of is Windows overwriting the MBR and destroying GRUB, but that's easy enough to repair. 

And, yeah, go ahead and gloat about your weather. :D Up here in the north, it's not quite Winter, but I wouldn't call it call nice.

---

### Post by Frak on 2007-10-27
nspluginwrapper can fix your flash problem, I've used it and it runs fine.

---

### Post by sUSe- on 2007-10-27
Im very very confused though am new to Linux. 
When it comes to the "Prepare Partition" phase it appears my HD, it has no partitions it only apperas my HD ando some other space, marked as "free space" ---> 8 MB. 
Well I select my HD (120 gigs, 84700 megas used) click on edit partition
and it appears this new window: 

-----------------------------------------------------------------------------------------
EDIT PARTITION 

Edit a Partition

New Partition size in megabytes: (in this space do i select like the 20 gigs I wanna give for ubuntu 7.10 or the 90 gigs i wanna leave for windows, and the rest obvious its for linux)

Uses as: if a select 20 gigs in this space it should be ext3..... if a select 90 gigs i leave it like it appears, ntfs.

Mound Point: if I select 20 gigs, in this space it should be only "/".... if I select 90 gigs I leave it like it appears, /media/sda1. 

-----------------------------------------------------------------------------------------

I REALLY NEED AN ANSWER AM SO CONFUSED :S!!
PLEASE SOMEONE!!!!

---

### Post by Frak on 2007-10-27
It opens a new window so you can resize your partition, and Windows always allots 8 MB at the end of the drive just in case.

---

### Post by p_quarles on 2007-10-27
> **Frak said:**
> nspluginwrapper can fix your flash problem, I've used it and it runs fine.
nspluginwrapper is included in the x86-64 restricted extras package for 7.10, actually. My question was mainly about whether that would work better or worse than installing the 32-bit Firefox workaround. 

Anyway, I'm typing this on 64-bit Firefox, which has so far been doing everything, including Flash just fine.

---

### Post by Frak on 2007-10-27
> **p_quarles said:**
> nspluginwrapper is included in the x86-64 restricted extras package for 7.10, actually. My question was mainly about whether that would work better or worse than installing the 32-bit Firefox workaround. 

Anyway, I'm typing this on 64-bit Firefox, which has so far been doing everything, including Flash just fine.
I've noticed that both ways work the same on just about every 64-bit processor. The difference in performance is too small to really impact the users performance perception.

Though the 32-bit Firefox workaround is faster.

---

### Post by p_quarles on 2007-10-27
> **sUSe- said:**
> -----------------------------------------------------------------------------------------
EDIT PARTITION 

Edit a Partition

New Partition size in megabytes: (in this space do i select like the 20 gigs I wanna give for ubuntu 7.10 or the 90 gigs i wanna leave for windows, and the rest obvious its for linux)

Uses as: if a select 20 gigs in this space it should be ext3..... if a select 90 gigs i leave it like it appears, ntfs.

Mound Point: if I select 20 gigs, in this space it should be only "/".... if I select 90 gigs I leave it like it appears, /media/sda1. 

-----------------------------------------------------------------------------------------

I REALLY NEED AN ANSWER AM SO CONFUSED :S!!
PLEASE SOMEONE!!!!
The "new partition" size is what you'll be using for Linux. This new partition should be mounted as "/", and it should be formatted as ext3. Before you do any of this, though, make sure you back up your data and defrag the Windows drive. 

Anyway, this section of the forum is more for casual discussions than support. You'll get more help if you post a new question in this section:
[http://ubuntuforums.org/forumdisplay.php?f=73](http://ubuntuforums.org/forumdisplay.php?f=73)

---

