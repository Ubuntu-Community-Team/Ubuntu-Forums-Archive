---
title: "What is the recommended partitioning scheme for a file server"
date: 2009-09-11
forum: Server Platforms
---

### Post by Udayakiran on 2009-09-11
Hi,
A brief history:
I'm an amateur Linux user and have done about 10-15 installations of various distros. I have also used LVM and a bit of Linux RAID with openSUSE. I'm in love with kubuntu (thx to the openSUSE KDE interface) and was using it as the primary desktop OS. I've also set up Ubuntu Server about thrice and used one installation for 3 months as a file server.

The actual subject:
Now i want to set up a file server that'll also serve for downloads. It'll be a headless machine. It'll run on Ubuntu Server x86 version.
The system specs are:
AMD Athlon 64 X2 5000+ (2.6 GHz)
Asus Mobo (MZN-MX SE plus).
1 TB Seagate HDD.
DVD writer.

I would like to have some future expandibility, though not in the near future. I'd like some help on the recommended partitioning scheme. I am a bit hesitant to use my own intelligence as i want this to last for some time.

Thx in advance.:P
-Udayakiran

---

### Post by hessiess on 2009-09-11
20~ gig: OS.
rest:    file storage partition.

I also recommend you add a second HDD for backups.

---

### Post by Udayakiran on 2009-09-11
> **hessiess said:**
> 20~ gig: OS.
rest:    file storage partition.

I also recommend you add a second HDD for backups.
Thx for the quick reply. Another couple of questions.

Which file system should i use for the storage partition? I'll primarily be storing movies, game dvd backups, music collection, etc.

And i was wondering whether breaking it down to smaller partitions might reduce fragmentation and help keep up performance.

---

### Post by Claus7 on 2009-09-11
Hello,

as far as the file of the storage partition is concerned I would suggest you ext4, since is stable now, and according to users faster than ext3. Avoid at all costs using fat32. If you do so, have in mind that you won't be able to store a file more than 4GB.

Regards!

---

### Post by hessiess on 2009-09-11
> **Udayakiran said:**
> And i was wondering whether breaking it down to smaller partitions might reduce fragmentation and help keep up performance.

The larger the partition is, the less its going to fragment as the lack of a large enough contiguous block of storage is going to be less of a problem. Linux file systems are designed not to fragment, whereas the windows file systems(NTFS, FAT) just dump data in the first available spot, regardless of if its actually big enough.

Eather EXT3 or 4 would be aright, however I would personally use EXT3 as its older and thus is better tested.

---

### Post by grantemsley on 2009-09-11
I typically use about 20-40GB for /, a few gigs for swap, and mount the rest as /storage

Dividing it up has its pros and cons.  It might help with performance (not sure), and if the filesystem gets messed up you'd only have problems with that one partition.

However, it becomes an issue when you have all your files nicely sorted, and one of the partitions gets full.  You start having to move files around to manually load balance the partitions.

I'd use ext3 for the filesystem - it's the oldest, all the bugs are worked out, and there are well tested recovery tools for it if needed.

One tip I have for you if you might add more drives later but aren't going to use raid or LVM to span between them (because then one drive takes out data on both), and are sharing them via samba.

Setup your directories like this:

/storage/disc1/Movies
/storage/disc1/Games
(later on, with your second disc)
/storage/disc2/Software
/storage/disc2/Photos

Then make a directory /storage/shares
In /storage/shares, put symbolic links to Movies, Games, Software, Photos.  Make sure samba is set to follow symlinks.

The reason for doing this is because you can move folders between the drives when they start to get full, and just have to update the symlinks.  Everyone else sees it as one big share and doesn't have to change anything when you move them around.

---

### Post by Udayakiran on 2009-09-11
Thanks guys. I'm not going to use any windows partitions, esp FAT32. After some thinking, i've decided on this system:
   
   root partition: 20 GB, ext3.
  swap: 3 GB.
   rest on LVM,
   partition for important files: 100 GB, ext3 (with mirroring in the future if needed).
   storage: rest of the space, ext4 (might shrink it if the important file partition becomes full).
   
   Is it good enough?
   
   > **Claus7 said:**
> Hello,
   
  as far as the file of the storage partition is concerned I would suggest you ext4, since is stable now, and according to users faster than ext3. Avoid at all costs using fat32. If you do so, have in mind that you won't be able to store a file more than 4GB.
   
   Regards!
   
   Yea, i've read about the nice performance boost of ext4 and that makes it quite tempting. But i was a bit worried about the file system corruption problem. Has it been fixed?
   
   > **hessiess said:**
> The larger the partition is, the less its going to fragment as the lack of a large enough contiguous block of storage is going to be less of a problem. Linux file systems are designed not to fragment, whereas the windows file systems(NTFS, FAT) just dump data in the first available spot, regardless of if its actually big enough.

Eather EXT3 or 4 would be aright, however I would personally use EXT3 as its older and thus is better tested.

Ok, but i'm not going to use redundancy. So, as grantemsley said, if the file system gets corrupted, it'll be just that partition and i'd be losing less data.  But what you said makes sense. I guess i'll just go with one big partition.

> **grantemsley said:**
> I typically use about 20-40GB for /, a few gigs for swap, and mount the rest as /storage

Dividing it up has its pros and cons.  It might help with performance (not sure), and if the filesystem gets messed up you'd only have problems with that one partition.

However, it becomes an issue when you have all your files nicely sorted, and one of the partitions gets full.  You start having to move files around to manually load balance the partitions.

I'd use ext3 for the filesystem - it's the oldest, all the bugs are worked out, and there are well tested recovery tools for it if needed.

One tip I have for you if you might add more drives later but aren't going to use raid or LVM to span between them (because then one drive takes out data on both), and are sharing them via samba.

Setup your directories like this:

/storage/disc1/Movies
/storage/disc1/Games
(later on, with your second disc)
/storage/disc2/Software
/storage/disc2/Photos

Then make a directory /storage/shares
In /storage/shares, put symbolic links to Movies, Games, Software, Photos.  Make sure samba is set to follow symlinks.

The reason for doing this is because you can move folders between the drives when they start to get full, and just have to update the symlinks.  Everyone else sees it as one big share and doesn't have to change anything when you move them around.

Using symlinks is a great idea. I've never tried it. I'll look it up.

I am planning on using LVM exclusively, because i found it a lot more flexible and easier to use and modify. Last i used RAID, a mirror gave me a lot of head ache when i tried to shrink it.  LVM, on the other hand shrank without a protest. Performance isn't an issue either. I'm just worried about stability and compatibility. Using windows dynamic disks has left me with a bad taste.

I use GParted Live for partitioning. Does it support LVMs fully?

Last question, whats your opinion on XFS? from what i've read, its performance is competing with ext4. And it is a much older file system, suggesting more stability. Also i heard it is good at handling large files.

---

