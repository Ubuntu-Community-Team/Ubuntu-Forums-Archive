---
title: "Best filesystem for NAS/Samba?"
date: 2008-05-11
forum: Server Platforms
---

### Post by mixersoft on 2008-05-11
I'm setting up an 8.04 server right now, with 1 partition dedicated as a NAS/Samba share for my data, photos, music, etc. For the most part (95% of the time) the data will only be accessed from XP clients. 

What's the current wisdom on the best filesystem to use in this case? Ext3, NTFS, XFS, etc?

(note: the only thread I found on this topic was in 2006, and the author was saying NTFS was still experimental.)

---

### Post by LeoSolaris on 2008-05-11
The use of NTFS in Linux is smoother now. I am still building my home server at the moment, so anything other than letting you know that there is no longer any issues with NTFS and Linux would not be coming from experience.

You would be just fine setting it as an NTFS partition. We have updated the drives since 06. The new ntfs-3g driver has read/write support, and very minimal, if any data corruption issues. It's always a possibility, but it's a pretty remote possibility, now.

I hope that little bit of intel helps out!
Leo

---

### Post by mdr on 2008-05-12
I personally use XFS for all my server data drives.  A bit of a personal preference really.  I often have large data files (GB+) and it seems faster.  XFS was known to be awkward with Ubuntu if you used it on your root partition.

I would not use NFTS with a linux server.  Sticking with ext3 should be fine unless you intend to be running highly tuned large corporate databases etc.

---

### Post by songshu on 2008-05-12
NTFS would be a NO NO i'd say, 

other then that i have been tweaking and testing file systems like crazy when i was setting up my first file servers trying to squeze out that last bit of performance....

nowadays i got lazy and i just go for the default because it gives less problems in the end because it is better tested and nobody will notice any difference in performance anyway..

---

### Post by HermanAB on 2008-05-12
You got to look at what the file system has to do.  NTFS is robust, but extremely slow and inefficient.  It wastes about 12 to 25% of the disk drive. So it is OK if the system is not busy and you have lots of disk space.

Ext3 is faster than NTFS, but is also very inefficient and wastes about 7.5% of the disk drive.  Ext3 is also good for an encrypted file system.

JFS is fast and efficient and wastes only 0.2% of the disk space, while XFS only wastes 0.1%.  These two are however not robust enough for use as encrypted file systems.

My favourite is JFS, simply because XFS had a stupid bug some time ago.

---

### Post by koenn on 2008-05-12
> **LeoSolaris said:**
> The use of NTFS in Linux is smoother now
You would be just fine setting it as an NTFS partition. 
But what on earth would be the point in using NTFS ? The file server runs Linux, and even if all clients are WinXP, they'll be accessing files via samba (or whatever) so all they'll ever see is smb, regardless of what filesystem the NAS/fileserver is using. 
The support for ntfs under Linux is a workaround to provide some level of interoperability with a closed source filesystem developed specifically for Windows NT. What would be the benefit in choosing that over any of the tried and tested native Linux filesystems ?

---

### Post by Cytomax on 2008-05-12
what is the default file system in 8.04?
Eddie

---

### Post by lespaul_rentals on 2008-05-12
I would recommend either reiserFS or JFS.

---

### Post by articpenguin on 2008-05-12
uhh i would avoid reiserfs. Its a dead filesystem and hans reiser is in jail for the next 25 years. So i would recommened ext3 or jfs.

---

### Post by songshu on 2008-05-12
> **articpenguin said:**
> uhh i would avoid reiserfs. Its a dead filesystem and hans reiser is in jail for the next 25 years. So i would recommened ext3 or jfs.

lol ;)

i have used reiserfs happily for many years on slackware and found it to work very well, i don't think that the "chroot" of Reiser himself will make it less good all of a sudden.

---

### Post by mixersoft on 2008-05-13
> **koenn said:**
> But what on earth would be the point in using NTFS ? The file server runs Linux, and even if all clients are WinXP, they'll be accessing files via samba (or whatever) so all they'll ever see is smb, regardless of what filesystem the NAS/fileserver is using. 
?

I suppose this is the crux of the matter. It sounds like ntfs does not have any inherent advantages for samba, unless I want to mount the partition on an XP machine at some future time. But that seems unlikely.

I'm leaning to either JFS or XFS

---

