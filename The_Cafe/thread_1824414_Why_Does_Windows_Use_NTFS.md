---
title: "Why Does Windows Use NTFS?"
date: 2011-08-13
forum: The Cafe
---

### Post by dniMretsaM on 2011-08-13
I've always wondered why Windows use NTFS. It seems to me that ext* would be a better option. Mainly because ext* does not require the very time consuming process of defragmentation. So what are MS's reasons?

---

### Post by haqking on 2011-08-13
> **dniMretsaM said:**
> I've always wondered why Windows use NTFS. It seems to me that ext* would be a better option. Mainly because ext* does not require the very time consuming process of defragmentation. So what are MS's reasons?

Because Windows is Proprietary as is NTFS, it is their own Filesystem.

Same reason they use Internet Explorer and not firefox

There are many things they could do which would be better, but that why we have Linux ;-)

Dave Cutler is to thank i suspect from DEC with VMS (which if you like weirds facts...IBM-HAL and VMS-WNT......all one letter removed in alphabet...LOL strange fact for the night

---

### Post by 3Miro on 2011-08-13
It is hard to advertise this "feature" to non-tech people, the most they can say is "you don't have to defrag". It is easier to give a silent defrager that works in the background.

---

### Post by dniMretsaM on 2011-08-13
> **haqking said:**
> Because Windows is Proprietary as is NTFS, it is their own Filesystem.

Same reason they use Internet Explorer and not firefox

There are many things they could do which would be better, but that why we have Linux ;-)

Dave Cutler is to thank i suspect from DEC with VMS (which is you like weirds facts...IBM-HAL and VMS-WNT......all one letter removed in alphabet...LOL strange fact for the night

I kind of guessed as much, but I wondered if there were any technical advantages that I was unaware of.

---

### Post by haqking on 2011-08-13
> **dniMretsaM said:**
> I kind of guessed as much, but I wondered if there were any technical advantages that I was unaware of.

see here for comparisons

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

---

### Post by CompyTheInsane on 2011-08-13
> **dniMretsaM said:**
> I kind of guessed as much, but I wondered if there were any technical advantages that I was unaware of.
Built-in file compression and encryption.

---

### Post by 3Miro on 2011-08-13
> **compugeek32 said:**
> Built-in file compression

This has nothing to do with the file system. You can have file compression on any format.

---

### Post by haqking on 2011-08-13
> **3Miro said:**
> This has nothing to do with the file system. You can have file compression on any format.

NTFS has built in File Compression without the need for 3rd pary software.

I think thats what he meant, doesnt EXT need a patch (ecompress or something similar)

---

### Post by el_koraco on 2011-08-13
I think NTFS has some advantages regarding server deployment, like those junction points, but I know next to nothing about filesystems, so don't take my word for it.

---

### Post by 3Miro on 2011-08-13
> **haqking said:**
> NTFS has built in File Compression without the need for 3rd pary software.

I think thats what he meant, doesnt EXT need a patch (ecompress or something similar)

It is true that Windows has inbuild file compression, however, NTFS does not. The file compression can just as easily work with fat or ext or whatever else. The compression is not married to the file system.

My point is that MS can easily get ext + compression if they wanted to, this cannot be a reason to stick to NTFS.

---

### Post by 3Miro on 2011-08-13
> **el_koraco said:**
> I think NTFS has some advantages regarding server deployment, like those junction points, but I know next to nothing about filesystems, so don't take my word for it.

I doubt this. Considering how widespread Linux is on the servers, if NTFS gave any real advantage there, Linux would have gotten a better NTFS support in the kernel (right Linux NTFS support is outside of the kernel, the kernel has read only support).

---

### Post by dniMretsaM on 2011-08-13
> **haqking said:**
> see here for comparisons

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

Thanks for this, very informative!

> **compugeek32 said:**
> Built-in file compression and encryption.
I noticed that it had built in encryption when I was looking at the Wiki page. That is indeed pretty handy, although I wouldn't consider it a reason to use it over ext*.

---

### Post by haqking on 2011-08-13
> **3Miro said:**
> It is true that Windows has inbuild file compression, however, NTFS does not. The file compression can just as easily work with fat or ext or whatever else. The compression is not married to the file system.

My point is that MS can easily get ext + compression if they wanted to, this cannot be a reason to stick to NTFS.


I think i would disagree but i might be misreading you.

File comression is a feature of NTFS not windows itself.

[http://en.wikipedia.org/wiki/NTFS#File_compression](http://en.wikipedia.org/wiki/NTFS#File_compression)

[http://www.ntfs.com/ntfs-compressed.htm](http://www.ntfs.com/ntfs-compressed.htm)

It just so happens that you are most likely to be using windows with NTFS.  If it was a Windows feature then it would exist in FAT and it doesnt

[http://vlaurie.com/computers2/Articles/filesystems.htm](http://vlaurie.com/computers2/Articles/filesystems.htm)

[http://www.pcguide.com/ref/hdd/file/ntfs/other-c.html](http://www.pcguide.com/ref/hdd/file/ntfs/other-c.html)

A common MCSE question used to be about the advantages of using NTFS and the answer was compression for individual files and folders

---

### Post by Spice Weasel on 2011-08-13
Ext does fragment, it just doesn't have any de-fragmentation tools.

---

### Post by del_diablo on 2011-08-13
> **Spice Weasel said:**
> Ext does fragment, it just doesn't have any de-fragmentation tools.

There is offline defragmentation tools.

---

### Post by ctrlmd on 2011-08-13
for security like setting permissions on files and folders groups and users
and support large volumes

---

### Post by haqking on 2011-08-13
> **Spice Weasel said:**
> Ext does fragment, it just doesn't have any de-fragmentation tools.

apart from

defragfs
e4defrag
shake
defrag (which is a shell script)

---

### Post by haqking on 2011-08-13
> **ctrlmd said:**
> for security like setting permissions on files and folders groups and users
and support large volumes


all of which you can do in Linux

---

### Post by del_diablo on 2011-08-13
NTFS lacks a decent offline defragmention tool it seems.

---

### Post by 3Miro on 2011-08-13
> **haqking said:**
> I think i would disagree but i might be misreading you.

File comression is a feature of NTFS not windows itself.

[http://en.wikipedia.org/wiki/NTFS#File_compression](http://en.wikipedia.org/wiki/NTFS#File_compression)

[http://www.ntfs.com/ntfs-compressed.htm](http://www.ntfs.com/ntfs-compressed.htm)

It just so happens that you are most likely to be using windows with NTFS.  If it was a Windows feature then it would exist in FAT and it doesnt

[http://vlaurie.com/computers2/Articles/filesystems.htm](http://vlaurie.com/computers2/Articles/filesystems.htm)

[http://www.pcguide.com/ref/hdd/file/ntfs/other-c.html](http://www.pcguide.com/ref/hdd/file/ntfs/other-c.html)

A common MCSE question used to be about the advantages of using NTFS and the answer was compression for individual files and folders

There is no real disagreement, it is a poteito/potahto thing.

My point is that there is nothing inherit in ext that prevents MS form using ext with compression, hence compression cannot be the reason for MS to avoid ext.

I used compression on windows 95 back in 1997, it was a neat feature, but I can hardly imagine it being useful today (except in very few cases).

---

### Post by haqking on 2011-08-13
> **del_diablo said:**
> NTFS lacks a decent offline defragmention tool it seems.

it lacks one built in yes though there are many available.

ext does not really suffer from fragmentation unless its above 90% or so yet there is still defrag tools available for it

anyways the point of the OP was why do MS use it.

it was answered with it is MS proprietary like everything else they use.

The comparisons have been posted also

---

### Post by haqking on 2011-08-13
> **3Miro said:**
> There is no real disagreement, it is a poteito/potahto thing.

My point is that there is nothing inherit in ext that prevents MS form using ext with compression, hence compression cannot be the reason for MS to avoid ext.

I used compression on windows 95 back in 1997, it was a neat feature, but I can hardly imagine it being useful today (except in very few cases).

OK yeah i read that better than i did before, i get your point.

its late ;-)

---

### Post by dniMretsaM on 2011-08-13
> **Spice Weasel said:**
> Ext does fragment, it just doesn't have any de-fragmentation tools.

Really? I'd read multiple places that it doesn't.

---

### Post by haqking on 2011-08-13
> **dniMretsaM said:**
> Really? I'd read multiple places that it doesn't.

if you look back on previous page i posted various tools available for defrag on ext.

It is true that it really doesnt and never needs to be defragged and most sys admins never will.

above 90% it can a little

---

### Post by dniMretsaM on 2011-08-13
> **haqking said:**
> if you look back on previous page i posted various tools available for defrag on ext.

It is true that it really doesnt and never needs to be defragged and most sys admins never will.

above 90% it can a little

Oh ok.

---

### Post by Phrea on 2011-08-13
> **dniMretsaM said:**
> I've always wondered why Windows use NTFS. It seems to me that ext* would be a better option. Mainly because ext* does not require the very time consuming process of defragmentation. So what are MS's reasons?

Are you serious...??

---

### Post by dniMretsaM on 2011-08-13
> **Phrea said:**
> Are you serious...??

Um, yeah. Why do you think I posted this?

---

### Post by Phrea on 2011-08-13
> **dniMretsaM said:**
> Um, yeah. Why do you think I posted this?

I actually have no idea.  
It's open source vs proprietary MS.  

It's a very strange and complete moot question.

---

### Post by dniMretsaM on 2011-08-13
> **Phrea said:**
> I actually have no idea.  
It's open source vs proprietary MS.  

It's a very strange and complete moot question.

It was just a question. Relax. I just wondered if there were any technical advantages to NTFS. Why is that such a horrible thing to wonder? And do you like the word moot? I just saw you (kind of) used it in another thread.

---

### Post by haqking on 2011-08-13
> **Phrea said:**
> I actually have no idea.  
It's open source vs proprietary MS.  

It's a very strange and complete moot question.

either way it is a vaiid question and generated a discussion which brought up interesting views.

---

### Post by kaldor on 2011-08-13
> **Spice Weasel said:**
> Ext does fragment, it just doesn't have any de-fragmentation tools.

Ext* seems to be much less noticeable when it does fragment. I have never defragged on Linux, while on Windows XP it was mandatory after a while.

---

### Post by PhillyPhil on 2011-08-13
> **Spice Weasel said:**
> Ext does fragment, it just doesn't have any de-fragmentation tools.

Very, very, very minimal fragmentation.

> **Phrea said:**
> I actually have no idea.  
It's open source vs proprietary MS.  

It's a very strange and complete moot question.
?
No more strange or moot (don't see how a *question* can be moot anyway) than the other questions people ask here...

---

### Post by Thewhistlingwind on 2011-08-13
Because ext is a dead end and in the future Linux will probably use btrfs?

---

### Post by el_koraco on 2011-08-13
> **Thewhistlingwind said:**
> Because ext is a dead end and in the future Linux will probably use btrfs?

Nothing probable about it, certain. You can use btrfs today is you feel like testing, and people have used it for a year without problems.

---

### Post by ctrlmd on 2011-08-13
> **haqking said:**
> all of which you can do in Linux

ya but everyone like to do it their way since he asked i answered im not comparing

---

### Post by Thewhistlingwind on 2011-08-13
> **el_koraco said:**
> Nothing probable about it, certain. 

Luck is always a factor.;)

On my next install I'm using btrfs for /home, I've got backups.

Besides, it should be stable by this point anyway.

---

### Post by Dr. C on 2011-08-13
I can see two reasons:

1) Licensing / Legal. The key components of ext2/3/4 are distributed under the GPL. Add this GPL code to Microsoft Windows and distribute the derived work and major components of Microsoft Windows would have to be distributed under the GPL also.

2) The permission structure is totally different between NTFS and ext2/3/4

---

### Post by uRock on 2011-08-14
> **Spice Weasel said:**
> Ext does fragment, it just doesn't have any de-fragmentation tools.

+1 I find that after about 6 months everything starts getting slower and a fresh install will speed things up. Can't blame it on fragmentation, but that is only because there are no tools to prove a defrag is needed.

---

### Post by PhillyPhil on 2011-08-14
> **uRock said:**
> +1 I find that after about 6 months everything starts getting slower and a fresh install will speed things up. Can't blame it on fragmentation, but that is only because there are no tools to prove a defrag is needed.

Or perhaps: can't blame it on fragmentation because you have no idea whether that is the case or not?

You are very unlikely to have fragmentation of your ext FS, and even less likely to have enough to notice!

There are plenty of tools for ext defrag, some have been listed in this thread already.

---

### Post by sidzen on 2011-08-14
"I kind of guessed as much, but I wondered if there were any technical advantages that I was unaware of."

At the time it was invented (circa 1993), New Technology File System was better than FAT16.  See Wikipedia excerpt below:
________________
    
NTFS (New Technology File System)[1] is the standard file system of Windows NT, including its later versions Windows 2000, Windows XP, Windows Server 2003, Windows Server 2008, Windows Vista, and Windows 7.[5]
    
NTFS supersedes the FAT file system as the preferred file system for Microsoft’s Windows operating systems. NTFS has several improvements over FAT and HPFS (High Performance File System) such as improved support for metadata and the use of advanced data structures to improve performance, reliability, and disk space utilization, plus additional extensions such as security access control lists (ACL) and file system journaling.
    
[http://en.wikipedia.org/wiki/NTFS](http://en.wikipedia.org/wiki/NTFS)

---

### Post by uRock on 2011-08-14
> **PhillyPhil said:**
> Or perhaps: can't blame it on fragmentation because you have no idea whether that is the case or not?

You are very unlikely to have fragmentation of your ext FS, and even less likely to have enough to notice!

There are plenty of tools for ext defrag, some have been listed in this thread already.

Like I said, there is NO app that can tell you how fragmented the system is. The four apps listed in an earlier post are not very helpful in testing for actual speed gains. Please take the time to research said options.

I have seen the noticeable change in speed after reinstalling in fresh partitions.

---

### Post by PhillyPhil on 2011-08-14
> **uRock said:**
> I have seen the noticeable change in speed after reinstalling in fresh partitions.

As it's extremely unlikely you have any significant fragmentation at all before reinstall, the "change in speed" is equally unlikely to be because of defragmentation.

---

### Post by blueturtl on 2011-08-14
Let's pose the question in a different way: Why shouldn't Windows use NTFS? Or what would using another file system accomplish? Microsoft only moved away from FAT when it was painfully obsolete and causing problems.

Microsoft's goal is to sell as may licenses as possible, not to make the best product possible. If you accept that proposition, a lot of their bad design calls make perfect sense! Before someone points out making the best product is necessary to win in a market system, let me point out that history is abundant with examples of products that were superior to those of Microsoft and yet are now all but forgotten.

All you really need is aggressive marketing and leverage on the distribution. I'm not trying to divert the thread off subject. In my opinion any question posed "Why does Microsoft do this?" or "Why doesn't Microsoft do that?" can be covered by my answer: they lack motivation (due to lack of viable competition) and they don't have any pride in their products whatsoever.

A bit provocative, I know.

---

### Post by Spice Weasel on 2011-08-14
ext4 is a fairly new file system and there are still a few stability problems (data corruption, etc) that need to be fixed. NTFS is about as stable as it gets when it comes to file systems.

Also:

```

# xfs_db -r /dev/sda5
xfs_db> frag
actual 69338, ideal 65632, fragmentation factor 5.34%
xfs_db>

```

Recently defragged XFS file system on Linux.

---

### Post by haqking on 2011-08-14
> **uRock said:**
> +1 I find that after about 6 months everything starts getting slower and a fresh install will speed things up. Can't blame it on fragmentation, but that is only because there are no tools to prove a defrag is needed.

There are tools, they just are not used much, see my post from earlier below:

> **haqking said:**
> apart from

defragfs
e4defrag
shake
defrag (which is a shell script)

---

### Post by Aquix on 2011-08-14
The way I understand it Microsoft want nothing more than to move to a new filesystem. But like with all their products they have to always consider backwards compability in both software and hardware since they have a huge interest in keeping their enterprise customers happy. It's been the story for decades.

---

### Post by BigSilly on 2011-08-14
> **Spice Weasel said:**
> ext4 is a fairly new file system and **there are still a few stability problems (data corruption, etc) that need to be fixed**. NTFS is about as stable as it gets when it comes to file systems.

Really? I didn't know that, and it's a bit worrying as I use EXT4 on my external drive for personal back up. Would you recommend switching to NTFS then?

---

### Post by alexan on 2011-08-14
Contray to Windows, Linux DON'T need a specific FS; thanks to VFat you can make your Linux run on virtually any FS. with given time ext evolution was sort of "naturally elected" as best and adattable FS for Linux. sort of democratic election if you think about it. But doesn't exist only ext for Linux; there are other "candidate" around (see phoronix articles)!
Windows was made for a differen propuse: build and develop "imposed standards" which bring money to the company behind it; demicracy is not the issue: speed and efficiency far over acceptable level is not necessarily. said so, ntfs may be a good FS with tons of $$ investment in software engenieering but nothing that other OS but windows can use.
Ext eventually could make Windows run faster... but the MS would "fix" the next windows in order to have the same speed with NTFS and ABSOLUTELY NOT with ext

---

### Post by KUU on 2011-08-14
I know of another filesystem called NFS+ that's geared for UNIX (like) systems, is that not similar to NTFS?

---

### Post by haqking on 2011-08-14
> **KUU said:**
> I know of another filesystem called NFS+ that's geared for UNIX (like) systems, is that not similar to NTFS?

no not at all,

NTFS is proprietary designed by and for microsoft. (dave cutler from DEC actually)

NFS was developed by Sun microsystems for accesing data across a network in similar fashion as if locally held

read the links already provided in the thread for information on filesystem comparisons etc

---

### Post by uRock on 2011-08-14
> **haqking said:**
> There are tools, they just are not used much, see my post from earlier below:

Those tools may have the ability to defrag an EXT system, but they can not report as to the severity of the fragmentation. From Googling those tools, some of them are still in development and don't appear to have a finish date.

---

### Post by dniMretsaM on 2011-08-14
> **Aquix said:**
> TBut like with all their products they have to always consider backwards compability in both software and hardware since they have a huge interest in keeping their enterprise customers happy.

MS Office?

---

### Post by mcduck on 2011-08-14
> **uRock said:**
> Those tools may have the ability to defrag an EXT system, but they can not report as to the severity of the fragmentation. From Googling those tools, some of them are still in development and don't appear to have a finish date.

Try e2fsck, for example. :) It does report the count (and percentage) of non-contiguous files, although you might have to force the check to see the result if the filesystem is clean.

```
sudo e2fsck -fvn /dev/sda1
```

---

### Post by disabledaccount on 2011-08-14
For me it looks like just another topic where obvious things are discussed again and again. Uncle Google clearly explains why extX doesn't fragment the files. For my 1.5TB storage I get 0.1% fragmentation after ~3years of extensive usage - nothing to comment.
NTFS has big problems with fragmentation, it can't cooperate efficiently with Raid controllers (not aware of stripe size), and the best defragmenting tools were not written by MS -> eg. contig (really the best one) is artwork by Sysinternals.
Another good question is why MS (having NDA's with HW manufacturers) needed YEARS to find out that sector 63 is not good for 1st partition.

edited: uRock: thank You for good lesson about what the forum really is.

---

### Post by haqking on 2011-08-14
> **uRock said:**
> Those tools may have the ability to defrag an EXT system, but they can not report as to the severity of the fragmentation. From Googling those tools, some of them are still in development and don't appear to have a finish date.

Yeah i agree as to the reporting.

Sorry i re-read your post and saw that you mentioned about reporting.

I was just saying there are tools available thats all.  

Peace

---

### Post by PhillyPhil on 2011-08-14
> **Spice Weasel said:**
> ext4 is a fairly new file system and there are still a few stability problems (data corruption, etc) that need to be fixed. NTFS is about as stable as it gets when it comes to file systems.

Also:

```

# xfs_db -r /dev/sda5
xfs_db> frag
actual 69338, ideal 65632, fragmentation factor 5.34%
xfs_db>

```

Recently defragged XFS file system on Linux.

??
Why have you suddenly introduced xfs into the discussion?
What does it have to do with the OP's question about ext, or the discussion so far about the (lack of) fragmentation of ext?

ext3 is also about as stable as a fs gets.

---

### Post by PhillyPhil on 2011-08-15
> **mcduck said:**
> sudo e2fsck -fvn /dev/sda1
On sda1 of my desktop running 10.04 (installed on release of 10.04), using 86.2% of partition capacity, ext4 partition, e2fsck reports:

137 non-contiguous files (0.1%)

I'll let that speak for itself.

---

### Post by uRock on 2011-08-15
> **PhillyPhil said:**
> On sda1 of my desktop running 10.04 (installed on release of 10.04), using 86.2% of partition capacity, ext4 partition, e2fsck reports:

137 non-contiguous files (0.1%)

I'll let that speak for itself.
Did ya run it from a LiveCD or some other image?```
E2FSCK(8)                                                            E2FSCK(8)



NAME
       e2fsck - check a Linux ext2/ext3/ext4 file system

SYNOPSIS
       e2fsck  [  -pacnyrdfkvtDFV ] [ -b superblock ] [ -B blocksize ] [ -l|-L
       bad_blocks_file  ]  [  -C  fd  ]  [  -j   external-journal   ]   [   -E
       extended_options ] device

DESCRIPTION
       e2fsck is used to check the ext2/ext3/ext4 family of file systems.  For
       ext3 and ext4 filesystems that use a journal, if the  system  has  been
       shut  down  uncleanly without any errors, normally, after replaying the
       committed transactions  in the  journal,  the  file  system  should  be
       marked  as clean.   Hence, for filesystems that use journalling, e2fsck
       will normally replay the journal and exit, unless its superblock  indi&#8208;
       cates that further checking is required.

       device  is  the  device  file  where  the  filesystem  is  stored (e.g.
       /dev/hdc1).

       Note that in general it is not safe to run e2fsck on  mounted  filesys&#8208;
       tems.  The only exception is if the -n option is specified, and -c, -l,
       or -L options are not specified.   However, even if it is  safe  to  do
       so,  the  results  printed by e2fsck are not valid if the filesystem is
       mounted.   If e2fsck asks whether or not you should check a  filesystem
       which  is mounted, the only correct answer is ``no''.  Only experts who
       really know what they are doing should consider answering this question
       in any other way.

OPTIONS
       -a     This  option  does  the same thing as the -p option.  It is pro&#8208;
              vided for backwards compatibility only;  it  is  suggested  that
              people use -p option whenever possible.

       -b superblock
              Instead  of  using  the  normal  superblock,  use an alternative
              superblock specified by superblock.   This  option  is  normally
              used  when the primary superblock has been corrupted.  The loca&#8208;
              tion of the backup superblock is dependent on  the  filesystem's
              blocksize.    For  filesystems  with  1k  blocksizes,  a  backup
              superblock can be found at block 8193; for filesystems  with  2k
              blocksizes,  at  block  16384;  and  for 4k blocksizes, at block
              32768.

              Additional backup superblocks can be  determined  by  using  the
              mke2fs  program  using  the  -n  option  to  print out where the
              superblocks were created.   The -b option to mke2fs, which spec&#8208;
              ifies blocksize of the filesystem must be specified in order for
              the superblock locations that are printed out to be accurate.

              If an alternative superblock is specified and the filesystem  is
              not  opened  read-only,  e2fsck  will make sure that the primary
              superblock is  updated  appropriately  upon  completion  of  the
              filesystem check.

       -B blocksize
              Normally,  e2fsck will search for the superblock at various dif&#8208;
              ferent block sizes in an attempt to find the  appropriate  block
              size.   This  search  can  be fooled in some cases.  This option
              forces e2fsck to only try locating the superblock at a  particu&#8208;
              lar blocksize.  If the superblock is not found, e2fsck will ter&#8208;
              minate with a fatal error.

       -c     This option causes e2fsck to use badblocks(8) program  to  do  a
              read-only  scan  of  the device in order to find any bad blocks.
              If any bad blocks are found, they are added  to  the  bad  block
              inode  to  prevent them from being allocated to a file or direc&#8208;
              tory.  If this option is specified twice,  then  the  bad  block
              scan will be done using a non-destructive read-write test.

       -C fd  This option causes e2fsck to write completion information to the
              specified file descriptor so that the progress of the filesystem
              check  can  be monitored.  This option is typically used by pro&#8208;
              grams which are running e2fsck.  If the file  descriptor  number
              is  negative, then absolute value of the file descriptor will be
              used, and the progress information will be suppressed initially.
              It  can later be enabled by sending the e2fsck process a SIGUSR1
              signal.  If the file descriptor  specified  is  0,  e2fsck  will
              print  a  completion  bar  as  it goes about its business.  This
              requires that e2fsck is running on a video console or terminal.

       -d     Print  debugging  output  (useless  unless  you  are   debugging
              e2fsck).

       -D     Optimize  directories  in filesystem.  This option causes e2fsck
              to try to optimize all directories, either by reindexing them if
              the  filesystem  supports directory indexing,  or by sorting and
              compressing directories for smaller directories, or for filesys&#8208;
              tems using traditional linear directories.

              Even  without the -D option, e2fsck may sometimes optimize a few
              directories --- for example, if directory  indexing  is  enabled
              and  a  directory  is  not  indexed and would benefit from being
              indexed, or if the index structures are corrupted and need to be
              rebuilt.  The -D option forces all directories in the filesystem
              to be optimized.  This can sometimes make them a little  smaller
              and  slightly  faster  to  search,  but  in practice, you should
              rarely need to use this option.

              The -D option will detect directory entries with duplicate names
              in  a  single  directory, which e2fsck normally does not enforce
              for performance reasons.

       -E extended_options
              Set e2fsck extended options.  Extended options are  comma  sepa&#8208;
              rated,  and  may  take  an argument using the equals ('=') sign.
              The following options are supported:

                   ea_ver=extended_attribute_version
                          Set the version of  the  extended  attribute  blocks
                          which   e2fsck   will  require  while  checking  the
                          filesystem.  The version number may be 1 or 2.   The
                          default extended attribute version format is 2.

                   journal_only
                          Only replay the journal if required, but do not per&#8208;
                          form any further checks or repairs.

                   fragcheck
                          During pass 1, print a detailed report of  any  dis&#8208;
                          contiguous blocks for files in the filesystem.

       -f     Force checking even if the file system seems clean.

       -F     Flush  the  filesystem  device's buffer caches before beginning.
              Only really useful for doing e2fsck time trials.

       -j external-journal
              Set the pathname where the external-journal for this  filesystem
              can be found.

       -k     When combined with the -c option, any existing bad blocks in the
              bad blocks list are preserved, and any new bad blocks  found  by
              running  badblocks(8)  will  be added to the existing bad blocks
              list.

       -l filename
              Add the block numbers listed in the file specified  by  filename
              to  the list of bad blocks.  The format of this file is the same
              as the one generated by the badblocks(8) program.  Note that the
              block  numbers  are  based  on  the blocksize of the filesystem.
              Hence, badblocks(8) must be given the blocksize of the  filesys&#8208;
              tem in order to obtain correct results.  As a result, it is much
              simpler and safer to use the -c option to e2fsck, since it  will
              assure  that  the correct parameters are passed to the badblocks
              program.

       -L filename
              Set the bad blocks list to be the list of  blocks  specified  by
              filename.  (This option is the same as the -l option, except the
              bad blocks list is cleared before the blocks listed in the  file
              are added to the bad blocks list.)

       -n     Open  the  filesystem read-only, and assume an answer of `no' to
              all questions.  Allows  e2fsck  to  be  used  non-interactively.
              This  option  may not be specified at the same time as the -p or
              -y options.

       -p     Automatically repair ("preen") the  file  system.   This  option
              will  cause  e2fsck to automatically fix any filesystem problems
              that can be safely fixed without human intervention.  If  e2fsck
              discovers  a  problem which may require the system administrator
              to take  additional  corrective  action,  e2fsck  will  print  a
              description  of the problem and then exit with the value 4 logi&#8208;
              cally or'ed into the exit code.  (See the  EXIT  CODE  section.)
              This  option  is normally used by the system's boot scripts.  It
              may not be specified at the same time as the -n or -y options.

       -r     This option does nothing at all; it is provided only  for  back&#8208;
              wards compatibility.

       -t     Print  timing  statistics  for  e2fsck.   If this option is used
              twice, additional timing statistics are printed  on  a  pass  by
              pass basis.

       -v     Verbose mode.

       -V     Print version information and exit.

       -y     Assume  an answer of `yes' to all questions; allows e2fsck to be
              used non-interactively.  This option may not be specified at the
              same time as the -n or -p options.

EXIT CODE
       The  exit  code  returned  by e2fsck is the sum of the following condi&#8208;
       tions:
            0    - No errors
            1    - File system errors corrected
            2    - File system errors corrected, system should
                   be rebooted
            4    - File system errors left uncorrected
            8    - Operational error
            16   - Usage or syntax error
            32   - E2fsck canceled by user request
            128  - Shared library error

SIGNALS
       The following signals have the following effect when sent to e2fsck.

       SIGUSR1
              This signal causes e2fsck to start displaying a  completion  bar
              or  emitting  progress  information.   (See discussion of the -C
              option.)

       SIGUSR2
              This signal causes e2fsck to stop displaying a completion bar or
              emitting progress information.

REPORTING BUGS
       Almost  any  piece of software will have bugs.  If you manage to find a
       filesystem which causes e2fsck to crash, or which e2fsck is  unable  to
       repair, please report it to the author.

       Please  include  as  much  information  as possible in your bug report.
       Ideally, include a complete transcript of the e2fsck run, so I can  see
       exactly  what  error  messages  are displayed.  (Make sure the messages
       printed by e2fsck are in English; if your system has been configured so
       that  e2fsck's  messages  have  been  translated into another language,
       please set the the LC_ALL environment variable to C so that  the  tran&#8208;
       script  of  e2fsck's  output  will  be  useful  to  me.)  If you have a
       writable filesystem where the transcript can be stored,  the  script(1)
       program is a handy way to save the output of e2fsck to a file.

       It  is  also  useful  to send the output of dumpe2fs(8).  If a specific
       inode or inodes seems to be giving  e2fsck  trouble,  try  running  the
       debugfs(8)  command  and send the output of the stat(1u) command run on
       the relevant inode(s).  If the inode is a directory, the  debugfs  dump
       command  will allow you to extract the contents of the directory inode,
       which can sent to me after being first run  through  uuencode(1).   The
       most useful data you can send to help reproduce the bug is a compressed
       raw image dump of the filesystem, generated using e2image(8).  See  the
       e2image(8) man page for more details.

       Always include the full version string which e2fsck displays when it is
       run, so I know which version you are running.

AUTHOR
       This version of e2fsck was written by Theodore Ts'o <tytso@mit.edu>.

SEE ALSO
       e2fsck.conf(5),  badblocks(8),  dumpe2fs(8),  debugfs(8),   e2image(8),
       mke2fs(8), tune2fs(8)



E2fsprogs version 1.41.14        December 2010                       E2FSCK(8)
```With emphasis on > However, even if it is  safe  to  do so,  the  results  printed by e2fsck are not valid if the filesystem is
       mounted.
So the next question is, "If fragmentation isn't the issue, then why do I see improved read times after formatting and restoring data from back ups?" I never had such problems with NTFS while running Windows 7, which I do very often on one of my machines.

EXT4 is great, but I see nothing wrong with NTFS and would happily run ubuntu on NTFS if it were possible.

---

### Post by PhillyPhil on 2011-08-15
> **uRock said:**
> Did ya run it from a LiveCD or some other image?
No (I don't have a working optical drive), but I'm sure you and/or someone else will volunteer results.


> With emphasis on 
So the next question is, "If fragmentation isn't the issue, then why do I see improved read times after formatting and restoring data from back ups?" I never had such problems with NTFS while running Windows 7, which I do very often on one of my machines.
Please tell me you don't believe ext fragments at anywhere NEAR the levels of ntfs?
Not even the most strident Windows fan or Linux hater who knows how files are allocated (not even steve balmer), will support that.

The only possible stance for an ntfs supporter when comparing fragmentation with ext is "it doesn't really matter" (which is only an opinion, of course).

> EXT4 is great, but I see nothing wrong with NTFS and would happily run ubuntu on NTFS if it were possible.

I don't think anyone has actually said ntfs is bad, per se.  It does have to be regularly defragmented though, unlike ext.

---

### Post by szymon_g on 2011-08-15
hm... 
it has shadow copy, so you can easily create snapshots. no linux filesystem has that /yes, i know- you can do snapshots of lvm/
also, ntfsv4 is a really good stuff /it got implemented in freebsd9 btw/

---

### Post by Grenage on 2011-08-15
Wouldn't moving all files to a trash drive (and then back again)  effectively kill any fragmentation?  I've never bothered it with it, as I've not noticed any slowdown on my builds; admittedly none of my machines have passed 60% drive capacity.

---

### Post by alexan on 2011-08-15
> **szymon_g said:**
> hm... 
it has shadow copy, so you can easily create snapshots. no linux filesystem has that /yes, i know- you can do snapshots of lvm/
also, ntfsv4 is a really good stuff /it got implemented in freebsd9 btw/

that's becouse have snapshot is a lesser priority feel by linux's community of user/developer.
After roughly 5~6 year of linux it never happen to me complain for lack of this feature

---

### Post by forrestcupp on 2011-08-15
It's kind of like asking why doesn't Windows use the Linux kernel. They're in competition, and NTFS is their offering, which is much better than FAT, like they used to use.

One other possible reason is that no version of Windows has ever been able to detect an ext partition. That could cause problems, and it's a pretty huge thing to transition. When they moved from FAT to NTFS, it was a huge undertaking. The benefits of NTFS over FAT were obvious, but people on work systems don't want to go through another transition like that for the minimal benefits they would get from Ext.

---

### Post by nerdopolis on 2011-08-15
> **szymon_g said:**
> hm... 
it has shadow copy, so you can easily create snapshots. no linux filesystem has that /yes, i know- you can do snapshots of lvm/
also, ntfsv4 is a really good stuff /it got implemented in freebsd9 btw/

Doesn't BTRFS have snapshot ability?

---

### Post by szymon_g on 2011-08-15
> **nerdopolis said:**
> Doesn't BTRFS have snapshot ability?

btrfs is like linux on desktop- it's never ending story. so far, it doesn't even have a fsck tool, so- its rather a toy than something useful.

---

