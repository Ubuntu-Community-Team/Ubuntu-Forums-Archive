---
title: "Syncing files and setting across OSes?"
date: 2007-10-07
forum: The Cafe
---

### Post by Carbonfish on 2007-10-07
Hi all,

I know that there have been older posts about this, but I thought that I'd ask fresh and see what your opinions are.

I am currently running the two systems that you can see in my signature (Mac OS X on an iBook G4, and Edgy on an old IBM T23 ThinkPad), and here's the thing, I am trying to wean myself off of Apple's proprietary business model, especially now that they are being such corporate dicks about locking stuff down, and I use my Ubuntu ThinkPad most of the time, but I have to use the iBook for some stuff. 
 So here's my question:

 What's the best way to set up my LaCie 250 GB external HD so that I can share files between both systems?

The ThinkPad doesn't have Firewire capability, but the external drive has a USB port, so file transfers would just be slow, but will I have compatibility issues? I realize that GNU isn't UNIX, but I don't know what will work and what won't.

I have been running Ubuntu for a bit over a year now, and am not a complete n00b, but I haven't tried any file sharing between systems before, so am not sure where to start. Hence the questions...

TIA

KC

---

### Post by LaRoza on 2007-10-07
File sharing is easy in my experience. However, I never used a Mac.

The easiest method is having a separate partition for data that can be shared. In your case, with two mobile computers, and external drive seems the ideal method.

---

### Post by Carbonfish on 2007-10-08
Thanks for the reply LaRoza,

Yeah, I don't see any problems with the hardware, but I'm just wondering about whether or not I will have any file compatibility problems between the Mac and the Linux box.

Thank again,

KC

---

### Post by Scruffynerf on 2007-10-08
Shouldn't do, although file compatibility issues are more centered around the software applications rather than the OS.

Eg: 
My OpenOffice on Ubuntu can happily read MS Office and OpenOffice on Windows.
OpenOffice on Windows doesn't have a problem with OpenOffice documents on Ubuntu.
Cannot get MS Office to see OpenOffice documents (native format) properly.

Whilst I'm not a Mac person, it seems that if Ubuntu and Mac can both read and write to the file system, you should be good to go, apart from Mac specific application file extensions - such as Quark.

---

### Post by Carbonfish on 2007-10-08
Okay, thanks for that Scruffynerf.

I guess that I'll just play with it and see what shakes out.

KC

---

### Post by Carbonfish on 2007-10-09
Well, I guess it isn't going to be as easy as I thought. When I plug in the external drive, both volumes mount (I have the drive partitioned into two volumes and have about 100GB of empty, non-allocated space) and have the proper volume names and everything, but Ubuntu says that I don't have permission to write to the drives. 

Any suggestions?

 I don't want to frak around too much with the permissions as the external drive is where I keep the bootable clone of the drive in my iBook. I back up the whole drive once a week or so, and really can't afford to lose the backup.

Oh yeah, I almost forgot to mention that both volumes refuse to unmount from the Ubuntu box. I had to force them to unmount, which made me a bit nervous.

KC

---

### Post by Scruffynerf on 2007-10-09
What filesystem is the external partitioned at?

IF it is NTFS, you may need the application NTFS-3g in order to enable write access to NTFS partitions.

---

### Post by Carbonfish on 2007-10-12
Sorry about not keeping up with this thread. Thanks for the reply. 

Yeah, it's NTFS. I'll look for the application you suggested and go from there.

Thanks again,

KC

---

### Post by Carbonfish on 2007-10-14
Well this isn't going to give me that air of credibility that I try so hard to project, but I don't know what the hell I was thinking when I said that I thought that my external HD was formatted in NTFS. Its not!

It is formatted in HFS+ format, since that's the default format of my iBook.  

So given that my external drive is NOT NTFS, anybody have any suggestions about how I can get my Ubuntu box to have write permissions and how I can get the drive to unmount after it has mounted?

TIA and sorry for the idiocy,

Kent

---

### Post by Scruffynerf on 2007-10-14
Carbon,

Not having used a Mac since the apple II, I've had to resort to google for something.

About the only thing I can point you to would be the thread: [http://ubuntuforums.org/showthread.php?t=4411]("http://ubuntuforums.org/showthread.php?t=4411"), which may have some joy for you.

cheers

Scruffy.

---

### Post by Carbonfish on 2007-10-15
Thanks again Scruffy,

You know, now that I think about it OS X is supposed to play nice with FAT 32 format drives and Ubuntu is supposed to as well. Could I eliminate all of these problems by reformatting the external drive in FAT 32?

I could do that in about 10 minutes rather than having to rewrite fstab and creating mount points for HFS+ partitions, etc.

What do you think?

KC

---

### Post by Scruffynerf on 2007-10-15
Might be easier.

Keep in mind that a) Reformatting will wipe any and all data on that hard drive, and b) FAT32 does not support files over 4GB in size - so any and all sizable .iso files or DVD images cannot live on a FAT32.

You will most likely still have to change the permissons in Ubuntu to allow write access though.

Scruffy

---

### Post by peitschie on 2007-10-15
In my experience using ntfs-3g under Feisty, or simply using the supplied ntfs driver under Gutsy has no issues reading & writing ntfs.  I would actually recommend giving that method a shot first...

---

### Post by Scruffynerf on 2007-10-15
> **peitschie said:**
> In my experience using ntfs-3g under Feisty, or simply using the supplied ntfs driver under Gutsy has no issues reading & writing ntfs.  I would actually recommend giving that method a shot first...

The OP's machine is a Mac. Can Mac's format to NTFS now?

---

### Post by Carbonfish on 2007-10-17
Thanks again for the feedback, this time to both of you. This may be a silly question, but I have not thought about it before, so haven't thought to ask it, but can I format each partition independently of each other?

That way I could keep a 30 GB HFS+ partition for the bootable clone of the HD in the iBook and format the rest of the drive FAT32  to share between the Mac and the Linux box.

Is that possible or does the whole drive have to be formatted before partitioning?

Thanks again,

Kent

---

### Post by Scruffynerf on 2007-10-17
Nope, you can format individual partitions.

Think of it this way - most OS's (Windows family, linux family) tend to view each partition as it's own hard drive - a partition is a section of a physical unit.

Hence, in linux in places like the fstab or grub, you may see notation like "hda0,1" These notations are referring to Hard Drive (or SATA Drive) 1, partition 2.

Look at it this way, I have 2 physical IDE hard drives. Drive 1 has three partitions - 1 NTFS for windows boot, 1 Ext3 partition for Linux boot and 1 Linux swap. My 2nd hard drive has 2 partitions - NTFS for windows data, and a Ext3 for /home.  Funnily enough, I've also setup ubuntu to read and write to the NTFS drives, and windows to read/write the Ext3 drives.

I do not use FAT32, as I have some files that are around 40Gb in size

You should be able to resize your existing hard drive from 1 partition (whole of Hdd) to a smaller size, and create a new Ext3 partition.

[COLOR="Red"]BE CAREFUL THOUGH - CHANGING PARTITION SIZES OFTEN RESULTS IN DATA LOSS.[/COLOR]

---

### Post by Carbonfish on 2007-10-20
Once again, Thanks Scruffynerf.

I see that you're from Adelaide. I live near Portland, Oregon in the States, but back in 1990 I spent a couple of months in Adelaide visiting friends and had a fantastic time in your beautiful city. I got to meet some wonderful people, watched some great local footie (or is that spelled with a 'y'?) at the Woodville South Football Club (home of the "Cats"), and ate Pie Floaters off of a cart somewhere downtown. 

Great times.  I still drank beer back then, and even though I can't touch the stuff anymore, I have fond memories of having a cold VB and watching a game from the side of the field (or do you call it a pitch for football as well?).

Anyway, thanks again for your help and encouragement.

Kent

---

### Post by HermanAB on 2007-10-21
Bear in mind that a Mac is BSD which is a kind of Unix and Linux is a kind of Unix.  Each comes with a cornucopia of file systems.  Therefore, it should be really easy to share files between them.  

Linux certainly supports HFS.  See the mount man page:

-t vfstype
              The  argument following the -t is used to indicate the file sys&#8208;
              tem type.  The file system types which are  currently  supported
              include:  adfs,  affs,  autofs,  coda, coherent, cramfs, devpts,
              efs, ext, ext2, ext3, hfs, hpfs,  iso9660,  jfs,  minix,  msdos,
              ncpfs,  nfs,  nfs4,  ntfs,  proc,  qnx4, ramfs, reiserfs, romfs,
              smbfs, sysv, tmpfs, udf, ufs, umsdos, usbfs, vfat,  xenix,  xfs,
              xiafs.   Note  that  coherent, sysv and xenix are equivalent and
              that xenix and coherent will be removed at  some  point  in  the
              future — use sysv instead. Since kernel version 2.1.21 the types
              ext and xiafs do not exist anymore. Earlier, usbfs was known  as
              usbdevfs.

---

### Post by Scruffynerf on 2007-10-21
> **Carbonfish said:**
> Once again, Thanks Scruffynerf.

I see that you're from Adelaide. I live near Portland, Oregon in the States, but back in 1990 I spent a couple of months in Adelaide visiting friends and had a fantastic time in your beautiful city. I got to meet some wonderful people, watched some great local footie (or is that spelled with a 'y'?) at the Woodville South Football Club (home of the "Cats"), and ate Pie Floaters off of a cart somewhere downtown. 

Great times.  I still drank beer back then, and even though I can't touch the stuff anymore, I have fond memories of having a cold VB and watching a game from the side of the field (or do you call it a pitch for football as well?).

Anyway, thanks again for your help and encouragement.

Kent

No problems. Footie/Footy is interchangable, although the latter is being used more. Mind you, I don't actually follow Aussie Rules that much anymore.

Heh. It really is a small world.

---

