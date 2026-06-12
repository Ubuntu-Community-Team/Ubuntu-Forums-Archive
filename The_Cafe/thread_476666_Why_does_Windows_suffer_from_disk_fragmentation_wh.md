---
title: "Why does Windows suffer from disk fragmentation when Linux doesn't?"
date: 2007-06-17
forum: The Cafe
---

### Post by Ultra Magnus on 2007-06-17
Hi I was just wondering whether anyone knows why Windows suffers so much from disk fragmentation whereas Linux doesn't appear to?

This was one of the reasons I decided to go with Linux because fragmentation really does kill the performance after a while and on a large hard disk it can take ages to defragment.

My reason for asking is this... I want to duel boot with vista and Ubuntu (Ubuntu being my main OS) but windows can't read ext3 so i'm going to have a small partition formated as fat32 to exchange files over etc.

Is the file systems microsoft uses that cause the fragmentation? - I was thinking of just keeping all my files on the fat32 partition, but if its a specific problem with the filesystem then i'll just keep them on my home partition and swap them across as and when i need to.

Any suggestions?
Thanks!

Jim

---

### Post by Bachstelze on 2007-06-17
Windows can read (and write to) ext3 if you install a driver for it :


[http://fs-driver.org/](http://fs-driver.org/)

About fragmentation, you have some info there :

[http://en.wikipedia.org/wiki/File_system_fragmentation](http://en.wikipedia.org/wiki/File_system_fragmentation)

---

### Post by prizrak on 2007-06-17
Fragmentation is a file system problem, not OS. It is on the filesystem how to handle fragmentation and general disk I/O performance.

---

### Post by FuturePilot on 2007-06-17
The swap file plays a big roll in chopping up your data.

---

### Post by vexorian on 2007-06-17
Yes, you shall try having a swap partition! aka, get 2 GB of your hd format and make windows save pagefile on that partition only.

---

### Post by prizrak on 2007-06-17
> **vexorian said:**
> Yes, you shall try having a swap partition! aka, get 2 GB of your hd format and make windows save pagefile on that partition only.

And slow your system down to a crawl. Everytime it tries to swap it will have to spin to get to that partition. Best thing to do in Windows is put swap file on a different HDD that is sitting on another IDE controller, if it's SATA then doesn't matter.

---

### Post by SoloSalsa on 2007-06-17
Fragmentation is not *just* the file system.  Every time anything is cut in half, there is a 'fragment'.  The file system has rules.  In FAT(and FAT**), the rule is ignore fragments, and how to clean them when choosing to do so.  In others, file system frowns upon making fragments, and tries to go around making one, and further, fragment maintenance is taken care of routinely, *by* the file system handler, so it never gets excessively messy like Windows will.  Just imagine Windows with a driver that accesses FAT like it always does, but the driver says '*wait! do not use this small space; skip ten clusters right, where there is an opening, and put the file there*', and also says '*do not even bother: there is no room right now.  push those pieces together; good; now put the file down here*'.

Or, maybe *I* should be the only one imagining this...  I am not sure if it is right, but from what I understand, this is the reason.  But this is **just** as I know it, and I am not educated or guaranteed right.

---

### Post by blah blah blah on 2007-06-17
> **prizrak said:**
> Fragmentation is a file system problem, not OS. It is on the filesystem how to handle fragmentation and general disk I/O performance.

the file system &#8714; OS

---

### Post by KiwiNZ on 2007-06-17
You can deminish fragmentation in windows by creating a fixed swap file on a seperate partition as opposed to the dymanic swap that is the default

---

### Post by init1 on 2007-06-17
The way fat/ntfs+windows works is that the files are added to the first available part of the file system like this:
|fileone;filetwo----|
|------------------------|
|------------------------|
|------------------------|
|------------------------|
|------------------------|
|------------------------|

Now, if you add to the files, then fragments will occur 

|fileone;filetwo;fil|
|eonefrag;filetwo|
|frag-------------------|
|------------------------|
|------------------------|
|------------------------|
|------------------------|

Eventually, lots of fragments will occur, and it the file system has to search for them
Now one a ext2/ext3 partition, the files are spaced out to give them room to grow

|fileone--------------|
|------------------------|
|------------------------|
|filetwo---------------|
|------------------------|
|------------------------|
|------------------------|

---

### Post by Tomosaur on 2007-06-17
Linux does suffer fragmentation, but it only really happens when the drive is almost full, and the OS needs to store files wherever they can fit. It also depends on the filesystem you use.

RAM can also become fragmented, but since RAM is volatile, all you need to do to fix it is reboot your computer (or close a whole bunch of programs and start using some others. There are also RAM defragmenters, but I've only ever used one on Windows).

---

### Post by Compucore on 2007-06-17
I think the simple reason windows has this problem and it is not as bad as linux would have it show up. Whenever you modify a file whether its a written document done in a word processor or in the spreadsheets. Files may be either expanded or decreased with the amount of information that is in there. Depending on what you add or remove from the document in questions. So what happens is when you save the current document as is or give it another name to save it under a different name. The computer when it is writteng it to the hard drive will take a look at where it can place it on the hard drive. Now sometime when writting it to the drive itself if the drive or the operating system has seen that a certain part of a file canot be save in the next block of free space. It will move that block to another part of the disk where it is available. Now in windows usually your files do not get defragment at the same time while saving it to the hard drive. Its not part of a regular routine of taking care of that on a day to day basis. Linux does not have to worry so much because it takes care of how the file is save by looking where it can place the whole file in one shot. So you do not get the file a little bit here, then there and at another place on the hard drive. Linnux will look at it and see that I need XXX amount of space for and XXX amount size for this file to be written to. This is what I was told by a couple of other tachs that deal with unix boxes themselves. 

Compucore

---

### Post by HermanAB on 2007-06-17
The NTFS which has now been in use for 5 years at least doesn't suffer from fragmentation.  All modern file systems are tree like structures and are not affected much by fragmentation the way that FAT was.  So, NTFS, Ext2/3, ReiserFS, JFS, XFS, ZFS are all OK.

Cheers,

Herman

---

### Post by Polygon on 2007-06-18
> **HermanAB said:**
> The NTFS which has now been in use for 5 years at least doesn't suffer from fragmentation.  All modern file systems are tree like structures and are not affected much by fragmentation the way that FAT was.  So, NTFS, Ext2/3, ReiserFS, JFS, XFS, ZFS are all OK.

Cheers,

Herman

your joking right? ntfs DOES suffer from fragmentation. I play games on windows, and guess where they are installed? on a ntfs partition. And i check that drive with a defragmenter, it was horribly fragmented.  Ever wonder why microsoft includes a defragmenter with windows?

---

### Post by Circus-Killer on 2007-06-18
just to backup up polygon, yeah, ntfs fragments like a....you know. seriously, when i first installed XP, i was glad to see ntfs part of the system because i too was led to believe that there would be minimal fragementation.

needless to say, i was wrong, and understand fully why the windows defrag tool is included with XP (and vista too). if im not mistaken, winFS was supposed to do away with fragmentation problems, but of course winFS never made it to vista.

---

### Post by prizrak on 2007-06-18
> **blah blah blah said:**
> the file system &#8714; OS

Was that supposed to be an "&" sign? Either way you are actually wrong, the filesystem is what handles how the files are written on the disk the OS only talks to the filesystem. You can have FAT and Ext3 on Windows as well as NTFS, on Linux you can have like 20 different filesystems.
> The NTFS which has now been in use for 5 years at least doesn't suffer from fragmentation. All modern file systems are tree like structures and are not affected much by fragmentation the way that FAT was. So, NTFS, Ext2/3, ReiserFS, JFS, XFS, ZFS are all OK.

Umm yean NTFS will fragment like nobody's business. All the other ones you mention also fragment very well, they all handle fragmentation differently though. Ext3 handles it in a way that makes very little difference in performance, NTFS just plain sux at it.

---

### Post by SoloSalsa on 2007-06-18
What init1 said is a great base explanation.  Though, NTFS *does* space things, just not as optimally as other systems.  NTFS works a bit better for different volume sizes when the cluster size is tweaked, but partitions are hardly ever defines with specific parameters like that.

---

### Post by PatrickMay16 on 2007-06-18
Fragmentation does happen to linux's filesystems, too. Just not as much as it happens to windows's filesystem, I heard. So there's never often a need to defrag in linux.

However, it is possible to defrag linux filesystems, using the pydefragtools by jdong. 
[http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)

Today I defragmented my /usr, /etc/, /opt, and home folders using the pydefragtools, to see if there would be any performance gains. I haven't really noticed any big differences, but Unreal 2003 loaded to the menu a fair bit quicker, and folders full of images have their thumbnails loaded much quicker in nautilus.

---

