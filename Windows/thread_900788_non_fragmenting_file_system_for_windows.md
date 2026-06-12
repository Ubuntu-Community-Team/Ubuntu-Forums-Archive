---
title: "non fragmenting file system for windows?"
date: 2008-08-25
forum: Windows
---

### Post by zamadatix on 2008-08-25
is htere any non fragmenting file system that can be made to run with windows properly?

---

### Post by ddarsow on 2008-08-25
no

---

### Post by Gregmond on 2008-08-25
I have no idea what a non fragmenting file system is.

If you want to use something that Windows and Linux can read then there are few options.
Linux can view most File systems, although you may need to install things like ntfs3g.
Windows is very limited in what file systems it can read.

Not sure what you are trying to do here, so it is hard to give a better answer.

---

### Post by kansasnoob on 2008-08-25
> **ddarsow said:**
> no

+1

Win scatters crap all over a drive, quite often unmovable crap!

---

### Post by tamoneya on 2008-08-25
ive never seen one myself that windows can actually be installed on (that appears to be what you want).  The only thing I have seen that comes close is using ext3 + fs-drivers which you could store data on it but you wouldnt be able to boot windows from it (i think.  I have never heard of it being done).

---

### Post by speedkreature on 2008-08-25
To my knowledge, no real-world file system is capable of being free of fragmentation...that's just the result of not being able to predict the size of any given file at any given point in time.  There are some file systems that are less prone to fragmentation (Ext3&4 aren't bad, ZFS is quite good, XFS is decent in the right environment).

You're going to be hard pressed to get any non-Micrsoft file system working on the OS volume/partition (depending on your setup).  There is an Ext2/Ext3 driver for Windows which works pretty well, but it cannot fix errors on the drive (from what I've observed so far) so you'll need to boot into Linux to do that.

The problem here is a combination of thigs: 1) Closed-source proprietary framework, and 2) End User License Agreement (which prevents people from reverse-engineering the OS legally).

Microsoft pretty much wants end users to use the OS as-is, more than anything, because it's difficult to support software that isn't yours or isn't how you distributed it when source code isn't readily available.

This is why I choose open source :-)  

I hope this explanation has been informative and helpful.

---

### Post by jpeddicord on 2008-08-25
Moved to Windows Discussions.

---

### Post by damis648 on 2008-08-25
Microsoft and their closed-mindedness prevent us from using any filesystem other  than NTFS and FAT32. (Assuming XP)

---

### Post by cmat on 2008-08-25
I could only dream of such a thing. On Ubuntu my partition is a year old and is still under 2% fragmentation. My NTFS partition was 45% fragmented in 2 months. Not to mention I spend much more time on Ubuntu and I'm only on Windows when I do work.

---

### Post by scottuss on 2008-08-25
It's FAT32 or NTFS only due to the way it is coded. NTFS is much better than FAT32 (in terms of fragmentation resistance among other things)

There was supposed to be a new filesystem for Vista which got canned, dunno if it will be in the next version...

---

### Post by Devport on 2008-08-26
I use ext3 as a shared data storage between Windows And Linux and it works fine without any problems since months ( ext3 performance is much better than ntfs ). I even played team fortress 2 over the weekend on that partition using steam ( > 6 GB heavy FPS ).

[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

Yet if fragmentation is your only concern - as people said - all fs fragment to some degree. So you can either use a fs that fragments less like ext3 or you stick with ntfs / vfat and use a defragmenter ( which will not work on linux fs ) :

[http://ultradefrag.sourceforge.net/](http://ultradefrag.sourceforge.net/)

---

### Post by Seti on 2008-08-26
> **scottuss said:**
> There was supposed to be a new filesystem for Vista which got canned, dunno if it will be in the next version...

AFAIK it was going to be called WinFS, I think it should be out around the same time as Duke Nukem Forever,:rolleyes:

---

### Post by rockface on 2008-08-26
> **Seti said:**
> AFAIK it was going to be called WinFS, I think it should be out around the same time as Duke Nukem Forever,:rolleyes:

I know Microsoft developers made a big noise about the new technologies planned for Vista, of which WinFS was but one. It never materialised  and it is considered nothing more than vaporware. I don't think WinFS was ever suppose to be a revolutionary new filesystem, reading from a blog some time ago, it sat on top of and required NTFS to function.

Maybe a Google search will provide more accurate information.

---

