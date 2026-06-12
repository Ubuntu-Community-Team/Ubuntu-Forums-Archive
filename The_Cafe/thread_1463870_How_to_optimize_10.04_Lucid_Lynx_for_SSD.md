---
title: "How to optimize 10.04 Lucid Lynx for SSD"
date: 2010-04-27
forum: The Cafe
---

### Post by systemarpi on 2010-04-27
Hello, I would like to know if somebody know for a official tweaks needed for ubuntu to take the most possible advantage of SSD and take care of write/erase cicles.

I have search the web and found some interesting links I share here:

[http://itezer.com/blog/ubuntu-linux/125-Four-Tweaks-for-Using-Linux-with-SSD.html](http://itezer.com/blog/ubuntu-linux/125-Four-Tweaks-for-Using-Linux-with-SSD.html)

[http://blog.loxal.net/2009/04/tuning-ext4-for-performance-with.html](http://blog.loxal.net/2009/04/tuning-ext4-for-performance-with.html)

[http://bryan.larsen.st/2009/3/23/using-a-vertex-ssd-with-ubuntu-jaunty](http://bryan.larsen.st/2009/3/23/using-a-vertex-ssd-with-ubuntu-jaunty)

[http://samiux.wordpress.com/2009/06/09/howto-ubuntu-9-04-desktop-on-solid-state-disk-ssd/](http://samiux.wordpress.com/2009/06/09/howto-ubuntu-9-04-desktop-on-solid-state-disk-ssd/)

[http://megabytemorsels.blogspot.com/2009/05/using-tmpfs-for-tmp-with-ssd-in-ubuntu.html](http://megabytemorsels.blogspot.com/2009/05/using-tmpfs-for-tmp-with-ssd-in-ubuntu.html)

[http://forums.fedoraforum.org/showthread.php?t=215109](http://forums.fedoraforum.org/showthread.php?t=215109)

It will be nice if we can start talking about what should work and what is just useless.

---

### Post by robbel on 2010-04-30
There's TRIM support missing in 10.04... follow [https://bugs.launchpad.net/bugs/571476](https://bugs.launchpad.net/bugs/571476) for a report...

---

### Post by nhasian on 2010-04-30
i'm not worried about TRIM.  just upgrading the kernel to 2.6.33 or newer will enable trim.  what's MORE important is to properly align the SSD drive.  I just installed ubuntu 10.04 on my corsair P128 today and I dont think its properly aligned.  

```
sudo fdisk -l
```

gives the output:

> Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cb7c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1567    12586896   83  Linux
/dev/sda2            1568       15566   112446967+  83  Linux


shouldn't the start be something like 1024 or 2048 instead of 1?  its definitely not divisible by 512.

I noticed gparted had the option NOT to round to cylinders when creating the EXT4 partition, but it gave me some kind of error when i tried to create the first partition like that.

---

### Post by systemarpi on 2010-05-01
Just a fact I have checked with some test.

First, to newcomers, make sure you have 2.6.33.x Kernel, otherwise forget about TRIM.

Now, when you upgrade to 2.6.33 and run your tests, notice that if you modify your fstab file with the commit=x option, you will have to wait that x seconds before the SSD auto-trim the sector, at least thats what is happening with my ST Ultra Drive, if you test too early you could think that Trim is not working.

---

### Post by dcstar on 2010-05-01
And how does this thread comply with:
[I]
All your general support **questions** for Ubuntu, Kubuntu, Edubuntu and Xubuntu.[/I]?

Do not post things like this in the General Support forum, find a more appropriate place.

---

### Post by systemarpi on 2010-05-01
> **dcstar said:**
> And how does this thread comply with:
[I]
All your general support **questions** for Ubuntu, Kubuntu, Edubuntu and Xubuntu.[/I]?

Do not post things like this in the General Support forum, find a more appropriate place.

I think because it stars with this:
"**I would like to know** if somebody **know** for a official tweaks needed for ubuntu to take the most possible advantage of SSD"

But nobody reply to my question, so people started to look for answers themselves, if you dont like the post, you can simply report it, so it can be deleted ASAP, I just dont care :)

---

### Post by mattlach on 2010-05-02
I don't see how alignment would help an SSD, because the partition space is virtual.  The drive itself decides where to place the data across the drive (in the name of load leveling)

I could be wrong though.

If you want to try it, it would seem you could just use gparted to move/resize your partitions to align them to 4k block sizes (with a a few blocks gap in between them) but I'm willing to wager the difference will be marginal at best.

I've been wrong before though, so I am open to being surprised if anyone gives it a try :p

---

### Post by systemarpi on 2010-05-02
> **mattlach said:**
> I don't see how alignment would help an SSD, because the partition space is virtual.

I agree with this one, partition is just a reserved amount of space, thats why partitions can be resized, aligning partitions to a exact size given a determined block size, could improve performance but in my opinion that improvement would be in the 0.X% factor, so, its a bit useless

---

### Post by solitaire on 2010-05-07
> **mattlach said:**
> I don't see how alignment would help an SSD, because the partition space is virtual.  The drive itself decides where to place the data across the drive (in the name of load leveling)

Unfortunately SSD's have a interface on the device which converts the flash chips in to Cylinder / Sector that any BIOS and OS can understand. So all file systems are still limited to sector alignment issues.

It's only the VERY expensive SSD's (talking $10,k drives here!) that don't have that interface and can use alternate filesystems that don't rely on cylinder/sector limits...

---

### Post by dcstar on 2010-05-07
> **systemarpi said:**
> I think because it stars with this:
"**I would like to know** if somebody **know** for a official tweaks needed for ubuntu to take the most possible advantage of SSD"

But nobody reply to my question, so people started to look for answers themselves, if you dont like the post, you can simply report it, so it can be deleted ASAP, I just dont care :)

The Ubuntu forums has a specific place for HOWTOs (it's called Tutorials and Tips), if people are too lazy to post things where they are supposed to go then I guess we just end up with the forum for General Support questions being filled with things that aren't supposed to be there, and those with genuine questions have to compete for attention.

---

### Post by systemarpi on 2010-05-07
:p

---

### Post by moep on 2010-05-14
> **nhasian said:**
> i'm not worried about TRIM.  just upgrading the kernel to 2.6.33 or newer will enable trim.  what's MORE important is to properly align the SSD drive.  I just installed ubuntu 10.04 on my corsair P128 today and I dont think its properly aligned.  

```
sudo fdisk -l
```

gives the output:

shouldn't the start be something like 1024 or 2048 instead of 1?  its definitely not divisible by 512.

I noticed gparted had the option NOT to round to cylinders when creating the EXT4 partition, but it gave me some kind of error when i tried to create the first partition like that.

The 10.04 installer already aligns partitions correctly. 
Try fdisk -lu (the u will display sectors instead of cylinders) and you’ll find that partition 1 starts at 2048.

---

### Post by nhasian on 2010-05-14
> **moep said:**
> The 10.04 installer already aligns partitions correctly. 
Try fdisk -lu (the u will display sectors instead of cylinders) and you’ll find that partition 1 starts at 2048.

yes i noticed that but gparted would not allow me to create the partitions with the 'round to cylinders' unchecked unless i left the first megabyte of the hard disk free.  This important piece of information should be documented somewhere :idea:

---

### Post by cariboo on 2010-05-14
This really isn't really a support question. Moved to the Cafe.

If you feel a post is in the wrong place, please report it, instead of commenting in the thread.

---

### Post by Johnsie on 2010-05-14
I've had an eeepc with an SSD for nearly 2 years running ubuntu and not had any problems. Decent SSD's are not as fast wearing as some people make them out to be.

Oh... I guess that's not relevant to the thread lol.

---

### Post by tahina on 2010-05-19
> **cariboo907 said:**
> This really isn't really a support question. Moved to the Cafe.

If you feel a post is in the wrong place, please report it, instead of commenting in the thread.

Support question or not, the question in the title ("How to optimize 10.04 Lucid Lynx for SSD"?) is still unanswered, though, unless "get kernel .33" is the complete answer.

If there's anything else one should consider, anyone with insight is welcome to share.

---

### Post by cariboo on 2010-05-19
I don't think that's a question that can really be answered, the question should be **What do I need to do to install Lucid on an ssd.**

---

### Post by nhasian on 2010-05-19
> **cariboo907 said:**
> **What do I need to do to install Lucid on an ssd.**

well to my knowledge two things need to be done, when using gparted untick the box labeled 'round to cylinders' and leave 1 megabyte free at the beginning of the disk or creating the partition will fail. Also for ata-trim you do need the Linux 2.6.33 higher kernel.  as for optimizing lucid for SSDs there are tons of other tweaks that can be done from moving the swap file to a regular HD to moving the /tmp and firefox cache etc.

---

### Post by Shining Arcanine on 2010-05-19
> **nhasian said:**
> i'm not worried about TRIM.  just upgrading the kernel to 2.6.33 or newer will enable trim.  what's MORE important is to properly align the SSD drive.  I just installed ubuntu 10.04 on my corsair P128 today and I dont think its properly aligned.  

```
sudo fdisk -l
```

gives the output:



shouldn't the start be something like 1024 or 2048 instead of 1?  its definitely not divisible by 512.

I noticed gparted had the option NOT to round to cylinders when creating the EXT4 partition, but it gave me some kind of error when i tried to create the first partition like that.

While I run Gentoo Linux, here is what I have on my laptop:

```
$ sudo fdisk -lu

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x93516c21

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         128       65664       32768+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2           65665     4259969     2097152+  82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sda3         4259970   125045423    60392727   83  Linux
```

You need to pass -u as a flag to fdisk, otherwise it will show cylinders instead of sectors. On old hard drives, cylinders were the way to go, but SSDs have a geometry that is not based on conventional cylinders.

By the way, my laptop uses a SSD and it is properly optimized. The warnings about cylinder boundaries are because of that.

Edit: In hindsight, it looks like only my boot partition is properly optimized. My swap partition is off by 1 sector while my root partition is off by 2 sectors. :oops:

Time to repartition my disk. :/

> **cariboo907 said:**
> I don't think that's a question that can really be answered, the question should be **What do I need to do to install Lucid on an ssd.**

Installing Lucid Lynx on a SSD is no different than installing it on an advanced format hard drive. It will work, but if you install it without aligning its partitions to 4KB boundaries, disk I/O performance will suffer.

---

### Post by tahina on 2010-05-19
I thought the main problem was about TRIM support and whether there is anything else to consider. I may be mistaken.

[COLOR="Red"][edit][/COLOR] 
> **Shining Arcanine said:**
> 
Installing Lucid Lynx on a SSD is no different than installing it on an advanced format hard drive. It will work, but if you install it without aligning its partitions to 4KB boundaries, disk I/O performance will suffer.

Thanks. Must look into that.
[COLOR="Red"][/edit][/COLOR]

I've yet to investigate the best way to go about getting the trim support, ie. getting a kernel of at least version 2.6.33. Now, [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) has lots of kernels, but installing directly from a .deb file instead of from a repository leads to not getting automatic updates.

There is a ppa on launchpad, [https://launchpad.net/~kernel-ppa](https://launchpad.net/~kernel-ppa) but I need to look into that more before I understand what that's about.

TRIM support might be coming to the backports repository. Does anyone know if there are plans for that?

---

### Post by cariboo on 2010-05-19
<offtopic>

> Installing Lucid Lynx on a SSD is no different than installing it on an advanced format hard drive. It will work, but if you install it without aligning its partitions to 4KB boundaries, disk I/O performance will suffer.

I do believe that has changed, I just recently installed WD Green 1Tb drive in my server, I just partitioned it as normal as an experiment, and checked the transfer rates

```
sudo hdparm -tT /dev/sdf
[sudo] password for me: 

/dev/sdf:
 Timing cached reads:   2464 MB in  2.00 seconds = 1232.21 MB/sec
 Timing buffered disk reads:  326 MB in  3.00 seconds = 108.62 MB/sec
```

Does that mean if I align it to 4k boundries my transfer rate will be even higher?

</offtopic>

---

### Post by Shining Arcanine on 2010-05-19
> **tahina said:**
> I thought the main problem was about TRIM support and whether there is anything else to consider. I may be mistaken.

[COLOR="Red"][edit][/COLOR] 


Thanks. Must look into that.
[COLOR="Red"][/edit][/COLOR]

I've yet to investigate the best way to go about getting the trim support, ie. getting a kernel of at least version 2.6.33. Now, [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) has lots of kernels, but installing directly from a .deb file instead of from a repository leads to not getting automatic updates.

There is a ppa on launchpad, [https://launchpad.net/~kernel-ppa](https://launchpad.net/~kernel-ppa) but I need to look into that more before I understand what that's about.

TRIM support might be coming to the backports repository. Does anyone know if there are plans for that?

It turned out that I made a mistake. After I realized my mistake on how I aligned my own drive's partitions, I did some quick google searches to verify whether or not my misaligned attempt at proper alignment from several months ago was targetting the correct erase block size and it turned out that it was not. You need to align partitions on SSDs to 512KB boundaries.

You can get good performance on SSDs by aligning partitions to 4KB boundaries, because 4KB is the size of an SSD page (smallest unit you can write on a SSD), but optimal performance is obtained by aligning them to 512KB boundaries, because 512KB is the size of an erase block (smallest unit you can erase on an SSD) and 512KB aligned partitions are by definition 4KB aligned partitions.

> **cariboo907 said:**
> <offtopic>



I do believe that has changed, I just recently installed WD Green 1Tb drive in my server, I just partitioned it as normal as an experiment, and checked the transfer rates

```
sudo hdparm -tT /dev/sdf
[sudo] password for me: 

/dev/sdf:
 Timing cached reads:   2464 MB in  2.00 seconds = 1232.21 MB/sec
 Timing buffered disk reads:  326 MB in  3.00 seconds = 108.62 MB/sec
```

Does that mean if I align it to 4k boundries my transfer rate will be even higher?

</offtopic>

Kernel caching is skewing the results in cached reads. The buffered disk reads are more accurate, but those are sequential reads, which do not reflect real world performance. You need to do random reads via something like IOMeter to get real world throughput rates. I guarentee you that your hard drive will not exceed 2MBps.

---

### Post by cariboo on 2010-05-19
More anecdotal info, when I first got the drive, I transferred a directory containing about 35Gb of data, mc was showing transfer rates ranging from 70MB/sec to 90MB/sec, that's the best speed I've seen transferring data between two SATA drives.

---

### Post by tahina on 2010-05-20
I came across a post from more than a year ago written by Ted Ts'o about aligning filesystems:

[http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/](http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/)

From the article and especially the comments, I gathered two things: 

1) Intel is said to have claimed that this is not an issue with their 2:nd generation ssd:s 

2) Formatting a disk with no partitions, but with the filesystem directly on the whole disk avoids any need for alignment.

Since #1 is hear-say of marketing speech (ie. not necessarily absolutely reliable) and since I only have a 40 GB ssd, I think I'll go with #2 for the sake of simplicity. I thinks it's just a matter of *mkfs.ext4 /dev/sda* in my case, but I'll do some more reading first...

---

### Post by Fanless_Puppy_Fan on 2010-05-24
> **tahina said:**
> 
2) Formatting a disk with no partitions, but with the filesystem directly on the whole disk avoids any need for alignment.

Since #1 is hear-say of marketing speech (ie. not necessarily absolutely reliable) and since I only have a 40 GB ssd, I think I'll go with #2 for the sake of simplicity. I thinks it's just a matter of *mkfs.ext4 /dev/sda* in my case, but I'll do some more reading first...Did you do your reading?

---

### Post by 98cwitr on 2010-05-24
> **systemarpi said:**
> Just a fact I have checked with some test.

First, to newcomers, make sure you have 2.6.33.x Kernel, otherwise forget about TRIM.

Now, when you upgrade to 2.6.33 and run your tests, notice that if you modify your fstab file with the commit=x option, you will have to wait that x seconds before the SSD auto-trim the sector, at least thats what is happening with my ST Ultra Drive, if you test too early you could think that Trim is not working.

there's manual trim with hdparm :)

---

### Post by tahina on 2010-05-26
> **Fanless_Puppy_Fan said:**
> Did you do your reading?

I was about to look into that, but first I went to look at how the sectors were laid out on my ssd. I did that the easy GUI way, by installing gparted, clicking on a partition and selecting "Information" in the "Partition" menu.

During the installation of lucid on the ssd, I chose manual partitioning and went for a 4.1 GB root and the rest for home and disregarded the warning of having no swap partition, since I'm thinking that the 4 GB of ram I have should be enough and hence no swap should be needed.

Now that I looked at the partitions with gparted, there's a 1 MB unallocated space at the beginning, wich I didn't put there. It's ranging from sector 0 to sector 2048 and I think it's there to serve this alignment purpose. 

The next one, the /-partition starts at 2048 and is a number of sectors divisible by 8 (8 times 512 bytes is 4 K, right?), so I'm thinking my drive is aligned...

Edit: And as was stated a week ago in post #12, by the insightful moep:
> The 10.04 installer already aligns partitions correctly.
Try fdisk -lu (the u will display sectors instead of cylinders) and you&#8217;ll find that partition 1 starts at 2048.

---

### Post by tahina on 2010-05-27
Oh, one more thing. I'm assuming the OS will do all the TRIMing I need, now that I have installed a .33 kernel. I don't need to enable it or anything, right? Correct me if I'm wrong.

---

### Post by zdude on 2010-05-27
"Oh, one more thing. I'm assuming the OS will do all the TRIMing I need, now that I have installed a .33 kernel. I don't need to enable it or anything, right? Correct me if I'm wrong."

You need to add the option "discard" to the mount point in fstab.

---

### Post by 98cwitr on 2010-05-27
^^^that's if you want to discard your cached internet files...which I dont and have enough ram to deal with it. Anyway, I am highly concerned about trim...my drive is getting slower by the day at a rate of 3MB per day...at this rate, when 10.10 comes out with the new kernel, my drive will be less than my old 500GB drive :(

---

### Post by 98cwitr on 2010-05-28
> **robbel said:**
> There's TRIM support missing in 10.04... follow [https://bugs.launchpad.net/bugs/571476](https://bugs.launchpad.net/bugs/571476) for a report...

added my .02 to the bug report...it would be nice if we could just get a kernel update...2.6.33 and 34 are out in stable releases, but when I installed 2.6.34 it totally blew out my graphics ;(

---

### Post by Jordanwb on 2010-05-28
I ordered a SSD today and I've found today's MM image to be useless (well I expected that...). So I'd like to know if this is the correct requirements to optimize 10.04 for SSD's:

[LIST=1]
[*]Install a .33 (or greater I suppose) kernel
[*]Add the "discard" mount option (I know this wasn't mentionned ITT but I read it elsewhere)
[*]Aligning partitions to?
[/LIST]

This is my "fdisk -lu" output:

```
root@JORDAN-CD3CDA3B:/home/jordanwb/Desktop# fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00099557

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   125831167    62914560    7  HPFS/NTFS
/dev/sda2       125837145   146801969    10482412+  83  Linux
/dev/sda3       146801970   624880304   239039167+  83  Linux
/dev/sda4       624880305   625137344      128520   83  Linux
```

Assuming /dev/sda is my SSD, are the partitions aligned? If not what tool would align them correctly?

> **cariboo907 said:**
> More anecdotal info, when I first got the drive, I transferred a directory containing about 35Gb of data, mc was showing transfer rates ranging from 70MB/sec to 90MB/sec, that's the best speed I've seen transferring data between two SATA drives.

Cool story bro.

---

### Post by libssd on 2010-05-28
By coincidence, I installed an OCZ Vertex SSD today on an Acer AA1. Good tips on netbook optimization available here: [http://blog.bodhizazen.net/linux/netbook-optimization/](http://blog.bodhizazen.net/linux/netbook-optimization/)

PS: Except for shock resistance and lower power draw, a fast SSD is probably not worth the effort on a netbook, as the Atom processor and SATA I bus can't take advantage of the speed of the SSD. I'm seeing 10-20% speed improvement over the 160gb Toshiba HDD that was originally in my Acer.

---

### Post by Jordanwb on 2010-05-28
I added the kernel ppa mentioned earlier in this thread. I installed linux-image-2.6.34-4-generic and linux-headers-2.6.34-4 but I can't install linux-headers-2.6.34-4-generic but it's not installable, linux-maverick-headers-2.6.34-4 doesn't exist.

---

### Post by Shining Arcanine on 2010-05-28
> **Jordanwb said:**
> I ordered a SSD today and I've found today's MM image to be useless (well I expected that...). So I'd like to know if this is the correct requirements to optimize 10.04 for SSD's:

[LIST=1]
[*]Install a .33 (or greater I suppose) kernel
[*]Add the "discard" mount option (I know this wasn't mentionned ITT but I read it elsewhere)
[*]Aligning partitions to?
[/LIST]

This is my "fdisk -lu" output:

```
root@JORDAN-CD3CDA3B:/home/jordanwb/Desktop# fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00099557

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   125831167    62914560    7  HPFS/NTFS
/dev/sda2       125837145   146801969    10482412+  83  Linux
/dev/sda3       146801970   624880304   239039167+  83  Linux
/dev/sda4       624880305   625137344      128520   83  Linux
```

Assuming /dev/sda is my SSD, are the partitions aligned? If not what tool would align them correctly?



Cool story bro.

1. They are not aligned
2. There is no automatic tool for partition alignment. You can align them manually with fdisk.
3. Here is a thread from the Gentoo forums that I made which explains how to align them yourself manually:

[http://forums.gentoo.org/viewtopic-t-828737.html](http://forums.gentoo.org/viewtopic-t-828737.html)

4. Here is how my partitions are setup on Gentoo Linux:

```
$ sudo fdisk -lu

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x93516c21

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1024       66559       32768   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2           66560     4260863     2097152   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sda3         4260864   125045423    60392280   83  Linux
```

5. Here is a bug report I filed in the Gentoo Linux bug tracker regarding an issue with fdisk that makes it difficult to align partitions properly:

[http://bugs.gentoo.org/show_bug.cgi?id=320655](http://bugs.gentoo.org/show_bug.cgi?id=320655)

Because of it, you cannot tell fdisk, say +2G, after specifying the starting sector for the swap file, because the ending sector will be off by 1. You need to either calculate it yourself to specify it manually, or specify, to follow the current example, +2G, then see where the partition ends, delete the partition and recreate the partition with the old ending minus 1. Otherwise, it throws off the alignment for the next partition.

6. While your root partition is fine, it does not need to start at sector 2048. Starting at sector 1024 is fine.

---

### Post by Jordanwb on 2010-05-28
So I'd want each partition to start on a block that is a multiple of 512 and the block count to be a multiple of 512.

When I use fdisk to partition a drive I use "fdisk /dev/sd?" then press n to add a partition, it asks me where I want the partition to start. I have a feeling 1024 isn't the right answer.

---

### Post by Shining Arcanine on 2010-05-29
> **Jordanwb said:**
> So I'd want each partition to start on a block that is a multiple of 512 and the block count to be a multiple of 512.

When I use fdisk to partition a drive I use "fdisk /dev/sd?" then press n to add a partition, it asks me where I want the partition to start. I have a feeling 1024 isn't the right answer.

[http://en.wikipedia.org/wiki/Cylinder-head-sector#Blocks](http://en.wikipedia.org/wiki/Cylinder-head-sector#Blocks)

The blocks involved here are not multiples of 512. The block involved here are multiples of 1024. While all multiples of 1024 are also multiples of 512, the converse is not true, which renders the idea of using multiples of 512 wrong. This assumes the units we mean are sectors, which is because a sector in traditional hard drives is 512 bytes, an erase block is 512KB and we need to align our partitions to 1024 sector boundaries to align them properly to erase blocks.

By the way, 1024 is not the right answer unless you press u before pressing n. Then it becomes the right answer because you switch from cylinders to sectors and 1024 sectors is the equivalent of an erase block. If it were possible to start partitions at the 0th sector, then it would be best to do that, but that would conflict with the MBR, boot loader and partition table.

---

### Post by stmiller on 2010-05-29
Yes - you need to add the mount option 'discard'. Simply running 2.6.33 or later does not give you trim. It is OFF by default, as most experimental/new things are when they first arrive.

kernel 2.6.33 and later
ext4 only
SSD with trim support only


Add mount option 'discard' to your /etc/fstab entry.

Ex:

```
/dev/sda1 / ext4 defaults,noatime,discard 0 1
```
:popcorn:

---

### Post by Jordanwb on 2010-05-29
Okay so I'd want the partition to start on a multiple of 1024, and its size to be a multiple of 1024. Is this 1024 bytes?

Does grub support having /boot as ext4?

[quote="frostschutz"]The alignment must also be respected by all layers you put on the drive, i.e. not only partitions, but raid (stripe size, payload offset?), lvm (payload offset?), filesystems (block size?), etc.[/quote]

Then there's this. How would one align file systems?

---

### Post by andrewabc on 2010-05-29
> **libssd said:**
> By coincidence, I installed an OCZ Vertex SSD today on an Acer AA1. Good tips on netbook optimization available here: [http://blog.bodhizazen.net/linux/netbook-optimization/](http://blog.bodhizazen.net/linux/netbook-optimization/)

PS: Except for shock resistance and lower power draw, a fast SSD is probably not worth the effort on a netbook, as the Atom processor and SATA I bus can't take advantage of the speed of the SSD. I'm seeing 10-20% speed improvement over the 160gb Toshiba HDD that was originally in my Acer.

Are you serious!?!? :(
Make sure your partition is aligned properly. If not then that is the problem.

Please post your benchmark at [System->Admin->Disk Utility->Benchmark results](http://ubuntuforums.org/showthread.php?t=1468995) thread. I think other netbook users have gotten SSD at full speed.

I would seriously expect more than 10-20% speed improvement over 160gb 5400 rpm drive. Even if SATA1 limited.

SATAI speed limit = 143mb/s
SATAII speed limiy  = 286mb/s

Benchmarks others are posting from netbooks with HDD only give around 60mb/s.

Here's my 160gb hdd in eeebox (same as netbooks)
[[IMG]http://img442.imageshack.us/img442/6176/screenshot160gbharddisk.th.png[/img]](http://img442.imageshack.us/i/screenshot160gbharddisk.png/)
It gets 47.8mb/s average. You're SSD should be getting triple that amount even if limited to SATA1.

Also was this vertex1 or vertex2?
I have original vertex 60gb. Check out my linked thread for all the benchmarks.

---

### Post by Shining Arcanine on 2010-05-29
> **Jordanwb said:**
> Okay so I'd want the partition to start on a multiple of 1024, and its size to be a multiple of 1024. Is this 1024 bytes?

Does grub support having /boot as ext4?



Then there's this. How would one align file systems?

That is 1024 sectors, where each sector is 512 bytes.

GRUB supports /boot as ext4. It also supports /boot as btrfs, although I do not recommend attempting that at this time.

I am not sure if there is anything special you can do with the file systems. I only worry about whether or not the partitions are aligned and I have not heard about anything with regard to file system alignment.

> **andrewabc said:**
> Are you serious!?!? :(
Make sure your partition is aligned properly. If not then that is the problem.

Please post your benchmark at [System->Admin->Disk Utility->Benchmark results](http://ubuntuforums.org/showthread.php?t=1468995) thread. I think other netbook users have gotten SSD at full speed.

I would seriously expect more than 10-20% speed improvement over 160gb 5400 rpm drive. Even if SATA1 limited.

SATAI speed limit = 143mb/s
SATAII speed limiy  = 286mb/s

Benchmarks others are posting from netbooks with HDD only give around 60mb/s.

Here's my 160gb hdd in eeebox (same as netbooks)
[[IMG]http://img442.imageshack.us/img442/6176/screenshot160gbharddisk.th.png[/img]](http://img442.imageshack.us/i/screenshot160gbharddisk.png/)
It gets 47.8mb/s average. You're SSD should be getting triple that amount even if limited to SATA1.

Also was this vertex1 or vertex2?
I have original vertex 60gb. Check out my linked thread for all the benchmarks.

ATA TRIM might not be enabled on his system.

By the way, if he has a single core system, he might a performance boost if he compiled his kernel to use the noop i/o scheduler:

[http://www.alphatek.info/2009/02/02/ssd-performance-vs-linux-kernel-io-scheduler-in-fedora-10/](http://www.alphatek.info/2009/02/02/ssd-performance-vs-linux-kernel-io-scheduler-in-fedora-10/)

Multicore systems see a performance drop with the noop i/o scheduler on SSDs, but single core systems see an increase:

[http://www.alphatek.info/2009/02/02/io-scheduler-and-ssd-part-2/](http://www.alphatek.info/2009/02/02/io-scheduler-and-ssd-part-2/)

---

### Post by andrewabc on 2010-05-30
> **Shining Arcanine said:**
> That is 1024 sectors, where each sector is 512 bytes.

GRUB supports /boot as ext4. It also supports /boot as btrfs, although I do not recommend attempting that at this time.

I am not sure if there is anything special you can do with the file systems. I only worry about whether or not the partitions are aligned and I have not heard about anything with regard to file system alignment.



ATA TRIM might not be enabled on his system.


I don't have TRIM because I am on Karmic 9.10, and havn't updated my firmware to a TRIM supported version.
I've had SSD since October, and my read speeds are still >200mb/s. I'm sure my write speeds have gotten slower, but the read speeds are most important advantage of SSD. TRIM should not affect read speeds that much. So he should be seeing triple increase in performance, not 10-20%. Something is definitely not setup correctly.

---

### Post by libssd on 2010-05-31
I haven't aligned the SSD, in part because the information I have found suggests that the performance improvements are marginal, but more because the procedure seems a little daunting. If you can point me to a good "how to" I would appreciate it. The best sources I have found so far are:

[http://bryan.larsen.st/2009/3/23/using-a-vertex-ssd-with-ubuntu-jaunty](http://bryan.larsen.st/2009/3/23/using-a-vertex-ssd-with-ubuntu-jaunty)
[http://articles.techrepublic.com.com/5100-10878_11-6149142.html](http://articles.techrepublic.com.com/5100-10878_11-6149142.html)

I have an external optical drive, as well as Ubuntu on 9.10 on an 8 gb SDHC card, so I can be running from it, and do the formatting/alignment on the SSD. And restorable system backups made with remastersys for disaster recovery.

Here are read test results on the HDD, using sudo hdparm -t /dev/sda:

  60.40 MB/sec
  60.09 MB/sec
  60.44 MB/sec

SSD:

 Timing buffered disk reads:  236 MB in  3.02 seconds =  81.37 MB/sec
 Timing buffered disk reads:  242 MB in  3.02 seconds =  82.14 MB/sec
 Timing buffered disk reads:  242 MB in  3.01 seconds =  82.21 MB/sec

---

### Post by Shining Arcanine on 2010-05-31
> **andrewabc said:**
> I don't have TRIM because I am on Karmic 9.10, and havn't updated my firmware to a TRIM supported version.
I've had SSD since October, and my read speeds are still >200mb/s. I'm sure my write speeds have gotten slower, but the read speeds are most important advantage of SSD. TRIM should not affect read speeds that much. So he should be seeing triple increase in performance, not 10-20%. Something is definitely not setup correctly.

It depends on the SSD. Some degrade more gracefully than others without TRIM. Intel's drives are the best examples of this. Jmicron based drives are the worst examples of this.

> **libssd said:**
> I haven't aligned the SSD, in part because the information I have found suggests that the performance improvements are marginal, but more because the procedure seems a little daunting. If you can point me to a good "how to" I would appreciate it. The best sources I have found so far are:

[http://bryan.larsen.st/2009/3/23/using-a-vertex-ssd-with-ubuntu-jaunty](http://bryan.larsen.st/2009/3/23/using-a-vertex-ssd-with-ubuntu-jaunty)
[http://articles.techrepublic.com.com/5100-10878_11-6149142.html](http://articles.techrepublic.com.com/5100-10878_11-6149142.html)

I have an external optical drive, as well as Ubuntu on 9.10 on an 8 gb SDHC card, so I can be running from it, and do the formatting/alignment on the SSD. And restorable system backups made with remastersys for disaster recovery.

Here are read test results on the HDD, using sudo hdparm -t /dev/sda:

  60.40 MB/sec
  60.09 MB/sec
  60.44 MB/sec

SSD:

 Timing buffered disk reads:  236 MB in  3.02 seconds =  81.37 MB/sec
 Timing buffered disk reads:  242 MB in  3.02 seconds =  82.14 MB/sec
 Timing buffered disk reads:  242 MB in  3.01 seconds =  82.21 MB/sec

It is a mistake to call the performance difference marginal, especially when measuring disk performance in sequential tests. The performance difference is almost entirely restricted to the realm of random I/O and depends upon how gracefully your SSD degrades. You can literally triple performance with some drives (sandforce based) if your drives are properly aligned, although when the same drives are improperly aligned, their performance is still competitive with other properly aligned drives. With Jmicron drives, you can literally increase performance by a factor of a thousand, although the performance is still abysmal, so I tend not to use them as an example of what SSDs can do when properly aligned.

Intel drives on the other hand only improve by about 5 to 10% while Indilinx based drives improve a bit more than that, although Intel drives are by far better, with or without TRIM.

---

### Post by andrewabc on 2010-05-31
> **libssd said:**
> I haven't aligned the SSD, in part because the information I have found suggests that the performance improvements are marginal, but more because the procedure seems a little daunting. If you can point me to a good "how to" I would appreciate it. The best sources I have found so far are:

[http://bryan.larsen.st/2009/3/23/using-a-vertex-ssd-with-ubuntu-jaunty](http://bryan.larsen.st/2009/3/23/using-a-vertex-ssd-with-ubuntu-jaunty)
[http://articles.techrepublic.com.com/5100-10878_11-6149142.html](http://articles.techrepublic.com.com/5100-10878_11-6149142.html)

I have an external optical drive, as well as Ubuntu on 9.10 on an 8 gb SDHC card, so I can be running from it, and do the formatting/alignment on the SSD. And restorable system backups made with remastersys for disaster recovery.

Here are read test results on the HDD, using sudo hdparm -t /dev/sda:

  60.40 MB/sec
  60.09 MB/sec
  60.44 MB/sec

SSD:

 Timing buffered disk reads:  236 MB in  3.02 seconds =  81.37 MB/sec
 Timing buffered disk reads:  242 MB in  3.02 seconds =  82.14 MB/sec
 Timing buffered disk reads:  242 MB in  3.01 seconds =  82.21 MB/sec

Can you possibly benchmark using [System->Admin->Disk Utility->Benchmark results](http://ubuntuforums.org/showthread.php?t=1468995)?

I agree that properly partitioning is a nightmare. I can't seem to find the thread I used to partition my ssd back in October. Looks like they removed/hid that thread.
Having to use command line to properly partition sucks. And still no confirmation if they fixed it for 10.04 or 10.10 in default installer (or gparted).

EDIT:
back in October I did
> sudo hdparm -t /dev/sdb

/dev/sdb:
 Timing buffered disk reads:  500 MB in  3.00 seconds = 166.46 MB/sec

$ sudo hdparm -t --direct /dev/sdb

/dev/sdb:
 Timing O_DIRECT disk reads:  594 MB in  3.01 seconds = 197.56 MB/sec
So maybe your benchmark is correct (no other slowdowns) as it is 1/2 of what my sataII gives.

But you definitely need to make sure your ssd is aligned properly, or else your writing speeds will be crippled (and wear down SSD twice as fast).

[Linux - Tips, tweaks and alignment ](http://www.ocztechnologyforum.com/forum/showthread.php?t=54379) is what I used to partition 60gb vertex1 back in October with a bit of help from ubuntuforum users.

Old article/review: [HDD vs SSD on a Netbook &#8211; Acer Aspire One D250](http://igadgetlife.com/2009/09/29/hdd-vs-ssd-on-a-netbook-%E2%80%93-acer-aspire-one-d250/) - Note that the SSD is slower than the one you have.
You should definitely be seeing 2x improvement over HDD on netbook.

---

### Post by Shining Arcanine on 2010-05-31
> **andrewabc said:**
> Can you possibly benchmark using [System->Admin->Disk Utility->Benchmark results](http://ubuntuforums.org/showthread.php?t=1468995)?

I agree that properly partitioning is a nightmare. I can't seem to find the thread I used to partition my ssd back in October. Looks like they removed/hid that thread.
Having to use command line to properly partition sucks. And still no confirmation if they fixed it for 10.04 or 10.10 in default installer (or gparted).

EDIT:
back in October I did

So maybe your benchmark is correct (no other slowdowns) as it is 1/2 of what my sataII gives.

But you definitely need to make sure your ssd is aligned properly, or else your writing speeds will be crippled (and wear down SSD twice as fast).

[Linux - Tips, tweaks and alignment ](http://www.ocztechnologyforum.com/forum/showthread.php?t=54379) is what I used to partition 60gb vertex1 back in October with a bit of help from ubuntuforum users.

Old article/review: [HDD vs SSD on a Netbook – Acer Aspire One D250](http://igadgetlife.com/2009/09/29/hdd-vs-ssd-on-a-netbook-%E2%80%93-acer-aspire-one-d250/) - Note that the SSD is slower than the one you have.
You should definitely be seeing 2x improvement over HDD on netbook.

Random performance is what suffers most when SSDs are not aligned. Sequential performance is relatively unaffected.

---

### Post by ShadowDragon on 2010-05-31
I'm wondering... I'm seeing quite some posts of people who are searching for a "howto <verb> a SSD" while there are quite some decent articles which go quite in-depth about the subjects. Nevertheless you do need to read quite a lot to understand what you are doing and to do it right. For the past years that wasn't such a big problem because the enthusiasts (the only people mad enough to pay for those things :p) wanted to know everything that was possible to know about SSDs. I, myself have spent a year following and reading the SSD evolution before I actually bought one.

But times seems to have changed. SSDs have become a bit more mainstream and new SSD owners hear that they can tweak the SSD. But not all of them are enthusiasts, they are just looking for a "quick-fix" they can apply without the burden of understanding every detail.

That makes me wonder: are there people who are interested in a series of HowTo's that explain, step by step, following the guidelines of the "Tutorials & Tips" subforums, how you align / secure erase / unfrost / ... your SSD? Because if there is a small group, I can volunteer to write some, next month, in the T&T section since there are practically no SSD's threads there...


I just saw that "alpharesearch" started with writing some stuff down in [Ubuntu GNU/Linux 10.04 migration from HDD to SSD](http://ubuntuforums.org/showthread.php?t=1491622). So if you guys think it's useful, I will see if it's possible to combine forces.

---

### Post by libssd on 2010-05-31
> **andrewabc said:**
> Can you possibly benchmark using [System->Admin->Disk Utility->Benchmark results](http://ubuntuforums.org/showthread.php?t=1468995)?

I agree that properly partitioning is a nightmare. I can't seem to find the thread I used to partition my ssd back in October. Looks like they removed/hid that thread.
Having to use command line to properly partition sucks. And still no confirmation if they fixed it for 10.04 or 10.10 in default installer (or gparted).

EDIT:
back in October I did

So maybe your benchmark is correct (no other slowdowns) as it is 1/2 of what my sataII gives.

But you definitely need to make sure your ssd is aligned properly, or else your writing speeds will be crippled (and wear down SSD twice as fast).

[Linux - Tips, tweaks and alignment ](http://www.ocztechnologyforum.com/forum/showthread.php?t=54379) is what I used to partition 60gb vertex1 back in October with a bit of help from ubuntuforum users.

Old article/review: [HDD vs SSD on a Netbook – Acer Aspire One D250](http://igadgetlife.com/2009/09/29/hdd-vs-ssd-on-a-netbook-%E2%80%93-acer-aspire-one-d250/) - Note that the SSD is slower than the one you have.
You should definitely be seeing 2x improvement over HDD on netbook.

sudo hdparm -t --direct /dev/sda

 Timing O_DIRECT disk reads:  372 MB in  3.01 seconds = 123.72 MB/sec
 Timing O_DIRECT disk reads:  370 MB in  3.01 seconds = 122.78 MB/sec
 Timing O_DIRECT disk reads:  368 MB in  3.01 seconds = 122.20 MB/sec

I'm a  little confused about how to use Palimpsest to generate benchmarks, as all choices except unmount are grayed out --  perhaps because I'm on 9.10 Karmic?

---

### Post by andrewabc on 2010-05-31
> **libssd said:**
> sudo hdparm -t --direct /dev/sda

 Timing O_DIRECT disk reads:  372 MB in  3.01 seconds = 123.72 MB/sec
 Timing O_DIRECT disk reads:  370 MB in  3.01 seconds = 122.78 MB/sec
 Timing O_DIRECT disk reads:  368 MB in  3.01 seconds = 122.20 MB/sec

I'm a  little confused about how to use Palimpsest to generate benchmarks, as all choices except unmount are grayed out --  perhaps because I'm on 9.10 Karmic?

I have no idea how they work either, I just typed in what someone told me to.

I guess since you are on 9.10 (same as me!), you can't easily run the benchmark I asked (it only showed up in 10.04).

You can if you create 10.04 liveusb (or livecd), and run the test. That is what I did for all my devices to get benchmarks.
Run liveusb/cd, run test, take screenshot of benchmark window, and upload to the thread I linked (or this thread, or both). Then reboot back into your 9.10.

You may want to test 10.04 on livecd/usb to quickly see what works/doesn't work. See if others have the same problem, and if not create bugs so they hopefully get fixed in time for 10.04.1 in July (or 10.10). Should only take 15 minutes.

To see if your partition is aligned properly this thread might give some suggestions (I linked to a thread that links to this already).
[Partition alignment for OCZ Vertex in Linux](http://www.ocztechnologyforum.com/forum/showthread.php?p=373226#post373226)

Go straight to **Verify result** section to see where your partition starts. Don't do the other stuff as you'll wipe your drive (ubuntu install).

---

### Post by Jordanwb on 2010-05-31
> **Shining Arcanine said:**
> That is 1024 sectors, where each sector is 512 bytes.

Okay I think I'm starting to understand, I'm going to try and align a standard hard drive as if it is a SSD.

```
root@JORDAN-CD3CDA3B:/home/jordanwb# fdisk -lu /dev/sdg

Disk /dev/sdg: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc01f9e34

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1            1024   312450047   156224512   83  Linux
/dev/sdg2       312450048   312581119       65536   83  Linux
```

Each partition starts on a multiple of 1024 and each partition's length is a multiple of 1024.

---

### Post by libssd on 2010-06-01
OK, I ran 10.4 from a USB, and then ran Disk Utility to generate a benchmark (screenshot attached).

This leads to two more questions:

1. Vertex SSD is running firmware 1.4; 1.5 is available, but I'm having a devil of a time figuring out how to install it on a netbook with no spare SATA port. Any ideas? The OCZ support site hasn't been a great deal of help so far. I have opened a support request with OCZ.

2. If 140 mb/sec according to the Disk Utility benchmark, is it worth the effort of aligning? I don't mind the work; at worst, I can always reinstall Ubuntu 9.04 from a backup, and re-upgrade to 9.10.

---

### Post by andrewabc on 2010-06-01
> **libssd said:**
> OK, I ran 10.4 from a USB, and then ran Disk Utility to generate a benchmark (screenshot attached).

This leads to two more questions:

1. Vertex SSD is running firmware 1.4; 1.5 is available, but I'm having a devil of a time figuring out how to install it on a netbook with no spare SATA port. Any ideas? The OCZ support site hasn't been a great deal of help so far. I have opened a support request with OCZ.

2. If 140 mb/sec according to the Disk Utility benchmark, is it worth the effort of aligning? I don't mind the work; at worst, I can always reinstall Ubuntu 9.04 from a backup, and re-upgrade to 9.10.

Argh, firmware updating. It sucks.

1. The ocz support site sucks. You have to get your info at the forum. Make a thread there after you've read everything and still have questions.
[Vertex, Agility, Turbo, Solid V2, Summit, Colossus and Z-Drive with Microsoft OS.](http://www.ocztechnologyforum.com/forum/forumdisplay.php?186-Vertex-Agility-Turbo-Solid-V2-Summit-Colossus-and-Z-Drive-with-Microsoft-OS.) - Has most information you need (upgrading firmware doesn't matter if you use windows or linux, other than creating bootable usb).
[Vertex, Agility, Turbo, Solid V2, Summit, Colossus on Linux and Apple OSX](http://www.ocztechnologyforum.com/forum/forumdisplay.php?237-Vertex-Agility-Turbo-Solid-V2-Summit-Colossus-on-Linux-and-Apple-OSX) - linux forum.


Specific thread to get your new firmare+instructions:
[This thread has the 1.5 FW update for Agility and Vertex drives ](http://www.ocztechnologyforum.com/forum/showthread.php?67815-This-thread-has-the-1.5-FW-update-for-Agility-and-Vertex-drives)

As for you using a netbook, it may not be possible to upgrade firmware on that. Need a IDE sata connection. This is the reason I am still on 1.3 firmware (on my 4 year old desktop), because I don't have access to IDE sata and have been too lazy to take to computer shop to do it.

2. You're 140mb/s is sata 1 limit, which is good speed (you're netbook HDD would have gotten 1/2 that in this test).
Yes very worth it to align. It is absolutely one of the most important things you should make sure to do. You won't see any difference in the read speed benchmark. But it will affect your sequential write, and random 4k write (read?).
I can't find reviews at the moment that compare aligned, vs non aligned, but I remember there is a difference. And if you have no problem wiping your SSD clean then I would do it.

---

### Post by 98cwitr on 2010-06-01
[http://wiki.archlinux.org/index.php/Maximizing_performance](http://wiki.archlinux.org/index.php/Maximizing_performance)

---

### Post by 98cwitr on 2010-06-01
added this line to fstab

```
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
```

if I do a *sudo df* I see the tmp files in tmpfs

> 
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                  1030128     10328   1019800   2% /tmp


but I dont see a process to monitor it in System Monitor. Can someone tell me where I can find this process or ensure that it's loaded into RAM?

---

### Post by libssd on 2010-06-01
> **andrewabc said:**
> Argh, firmware updating. It sucks.

1. The ocz support site sucks. You have to get your info at the forum. Make a thread there after you've read everything and still have questions.
[Vertex, Agility, Turbo, Solid V2, Summit, Colossus and Z-Drive with Microsoft OS.](http://www.ocztechnologyforum.com/forum/forumdisplay.php?186-Vertex-Agility-Turbo-Solid-V2-Summit-Colossus-and-Z-Drive-with-Microsoft-OS.) - Has most information you need (upgrading firmware doesn't matter if you use windows or linux, other than creating bootable usb).
[Vertex, Agility, Turbo, Solid V2, Summit, Colossus on Linux and Apple OSX](http://www.ocztechnologyforum.com/forum/forumdisplay.php?237-Vertex-Agility-Turbo-Solid-V2-Summit-Colossus-on-Linux-and-Apple-OSX) - linux forum.


Specific thread to get your new firmare+instructions:
[This thread has the 1.5 FW update for Agility and Vertex drives ](http://www.ocztechnologyforum.com/forum/showthread.php?67815-This-thread-has-the-1.5-FW-update-for-Agility-and-Vertex-drives)

As for you using a netbook, it may not be possible to upgrade firmware on that. Need a IDE sata connection. This is the reason I am still on 1.3 firmware (on my 4 year old desktop), because I don't have access to IDE sata and have been too lazy to take to computer shop to do it.

2. You're 140mb/s is sata 1 limit, which is good speed (you're netbook HDD would have gotten 1/2 that in this test).
Yes very worth it to align. It is absolutely one of the most important things you should make sure to do. You won't see any difference in the read speed benchmark. But it will affect your sequential write, and random 4k write (read?).
I can't find reviews at the moment that compare aligned, vs non aligned, but I remember there is a difference. And if you have no problem wiping your SSD clean then I would do it.
Your comments about the OCZ site make me feel much better -- I thought I was just being dense. On the other hand, Eric Ryder, of OCZ has been very helpful; if only to confirm what I had already sussed out. 

Fortunately, I have contacts where I used to work, and can get my hands on a Dell to flash the firmware.

I had been assuming that if SATA I was limiting throughput, alignment would provide little, if any, improvement, but you are suggesting otherwise, so I'll look into that after the firmware upgrade (break one thing at a time).

---

### Post by andrewabc on 2010-06-01
> **libssd said:**
> Your comments about the OCZ site make me feel much better -- I thought I was just being dense. On the other hand, Eric Ryder, of OCZ has been very helpful; if only to confirm what I had already sussed out. 

Fortunately, I have contacts where I used to work, and can get my hands on a Dell to flash the firmware.

I had been assuming that if SATA I was limiting throughput, alignment would provide little, if any, improvement, but you are suggesting otherwise, so I'll look into that after the firmware upgrade (break one thing at a time).

As for alignment benchmarks, I finally found one of the articles I was looking for.

[OCZ&#8217;s Vertex Limited Edition Review & SSD State of the Union](http://www.anandtech.com/show/2944/10) - anand states that indilinx drives get minor improvement (sadly doesn't show it).

While googling also found this nice article that explains it nicely why alignment is very important.
[Aligning an SSD on Linux](http://www.nuclex.org/blog/personal/80-aligning-an-ssd-on-linux)

Basically your sectors have to align with your SSD write erase amount.
On ocz vertex ssd erase size is 512kb. So you want each sector to be 512kb.
From the [ocz alignment forum post](http://www.ocztechnologyforum.com/forum/showthread.php?p=373226#post373226)
> On the other hand, since write operations to an SSD
always affect a whole erase block, it makes sense to
align to the erase block size, which is 512KB for OCZ Vertex.
Note that a 512KB aligned drive is also 64KB aligned,
because 512KB is a multiple of 64KB.
In the following, I will therefore assume that you want
a 512KB alignment; other possible alignment sizes
are discussed later.

It is possible that if you knew you would be constantly writing lots of large files (for a specific purpose), you could increase the sector size (but make sure to keep in multiples of 512 (or 64 etc)), which could 'improve' write speed of larger files. But smaller files would suffer (os/web browsing type stuff). So go with default 512kb.

EDIT:
[another old alignment ocz forum thread](http://www.ocztechnologyforum.com/forum/showthread.php?t=57599) - with some info on proper alignment.
> The goal is to not start a partition in the middle of a block or a page. That way, you don't split any boundaries. If you split a page (4k) section, then 2 writes are necessary to write the page instead of 1, doubling the work. It will happen repeatively every 8th page, reducing overall performance and I/O commands. Blocks have a similar performance hit but not to the same degree as pages. It's easy to align to both.
So if misaligned, you can end up writing twice as much as needed, which would decrease write speed. As a previous poster mentioned, it is the smaller files (4k random write) that suffer the most.

So in summary, even if you align properly, it is unlikely you will notice a performance increase. Benchmark wise there should be small gains. And to make your ssd last longer it will mean less writes.

---

### Post by libssd on 2010-06-01
I learned a lot about SSD technology from Anand's long piece, *[The SSD Anthology]("http://www.anandtech.com/show/2738")*.

Since most of my activity with the netbook is on the web, and I am using RAM for tmp space and have made other tuning changes to minimize unnecessary writing to the SSD, I don't think that aligning the drive is going to be worth the effort.

---

### Post by andrewabc on 2010-06-01
> **libssd said:**
> I learned a lot about SSD technology from Anand's long piece, *[The SSD Anthology]("http://www.anandtech.com/show/2738")*.

Since most of my activity with the netbook is on the web, and I am using RAM for tmp space and have made other tuning changes to minimize unnecessary writing to the SSD, I don't think that aligning the drive is going to be worth the effort.

Well, next time you decide to format ubuntu, might as well align the partitions. Or maybe they are aligned, I dunno if you checked. When I was doing it in October, it wasn't supported by default by jaunty/karmic (and I still have no idea about lucid/maverick).

To make firefox faster (maybe less writes, only when you sync to HDD) you could try [Howto; Firefox profile in RAM for increased speed and stability](http://ubuntuforums.org/showthread.php?t=1120475)

Oh, and make sure you turn down your swappiness so your swap doesn't get used unless absolutely necessary.
[Swap Faq](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)

Upgrading ram to 2gb in the future should help as you can have ram full of more data. Maybe if they fix preload software for 10.10 it will be useful (load most used data into ram at startup).

---

### Post by libssd on 2010-06-01
I've already done all those tweaks, except for FF cache, which is unnecessary since I use Chrome 99% of the time.

Reading back through this thread, and elsewhere, am I correct that it should be possible to non-destructively align an ext4 filesystem using gparted? IF so, that approach might be worth the effort. If it goes wrong, I can always restore from backup.

---

### Post by 98cwitr on 2010-06-03
> **98cwitr said:**
> added this line to fstab

```
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
```

if I do a *sudo df* I see the tmp files in tmpfs



but I dont see a process to monitor it in System Monitor. Can someone tell me where I can find this process or ensure that it's loaded into RAM?

anyone?

---

### Post by stmiller on 2010-06-03
OCZ gives you a boot CD as an iso download.  Pretty easy but yeah you need to switch the SATA mode from AHCI to IDE to write the firmware.

This is much better than some companies who require you to make a freedos boot CD on your own in order to load the firmware...

---

### Post by libssd on 2010-06-08
> **stmiller said:**
> OCZ gives you a boot CD as an iso download.  Pretty easy but yeah you need to switch the SATA mode from AHCI to IDE to write the firmware.

This is much better than some companies who require you to make a freedos boot CD on your own in order to load the firmware...
Except that you need a machine with a drive controller that permits switching from SATA to IDE during the boot sequence, which is not possible on my Aspire One. Eventually I'll get around to cadging time on a Dell, and flash the SSD.

---

### Post by 98cwitr on 2010-06-08
my SSD finally leveled off to around a 250MBps average...I could settle with that I guess :?

---

### Post by wconstantine on 2010-06-10
How do I upgrade to the .33 kernel? I ran a system update this morning and now I got 2.6.32-22-generic-pae.

I really don't want my new SSD to decline in performance.

A bit bad of Canonical not to include trim by default in this day and age? 

Also, I spent like 1½ hours reading how to align my partitions when I suddenly stumbled upon that the Ubuntu installer does this automagically in 10.04. Awesome. :)

However, reading about Trim made me reformat my ssd and reinstall Ubuntu. I had Backtrack 4 on the SSD and I bet it's better running it from the USB Pendrive instead (since I find it unlikely that BT4 devs find it prio to arrange Trim support in the near future).

---

### Post by 98cwitr on 2010-06-10
> **wconstantine said:**
> How do I upgrade to the .33 kernel? I ran a system update this morning and now I got 2.6.32-22-generic-pae.

I really don't want my new SSD to decline in performance.

A bit bad of Canonical not to include trim by default in this day and age? 

Also, I spent like 1½ hours reading how to align my partitions when I suddenly stumbled upon that the Ubuntu installer does this automagically in 10.04. Awesome. :)

However, reading about Trim made me reformat my ssd and reinstall Ubuntu. I had Backtrack 4 on the SSD and I bet it's better running it from the USB Pendrive instead (since I find it unlikely that BT4 devs find it prio to arrange Trim support in the near future).

[https://help.ubuntu.com/community/Kernel/Upgrade](https://help.ubuntu.com/community/Kernel/Upgrade)

---

### Post by wconstantine on 2010-06-10
> **98cwitr said:**
> [https://help.ubuntu.com/community/Kernel/Upgrade](https://help.ubuntu.com/community/Kernel/Upgrade)

I'm afraid that I can't find anything fresher than .32 there. I've enabled all repos I could find for Lucid and reloaded. Still no .33. I maybe have to download a complete new kernel from kernel.org?

Will a patch suffice or do I need a full version?

---

### Post by nhasian on 2010-06-10
to install the linux 2.6.34 kernel, follow my post [here]("http://ubuntuforums.org/showpost.php?p=9348970&postcount=8")

---

### Post by 98cwitr on 2010-06-10
> **wconstantine said:**
> I'm afraid that I can't find anything fresher than .32 there. I've enabled all repos I could find for Lucid and reloaded. Still no .33. I maybe have to download a complete new kernel from kernel.org?

Will a patch suffice or do I need a full version?

woops...sorry. Try this. You will then need to modify the /etc/fstab to add the discard option and add the tmpfs /tmp mount command since it's not included.

[http://www.ramoonus.nl/2010/05/19/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/](http://www.ramoonus.nl/2010/05/19/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/)

---

### Post by wconstantine on 2010-06-10
> **nhasian said:**
> to install the linux 2.6.34 kernel, follow my post [here]("http://ubuntuforums.org/showpost.php?p=9348970&postcount=8")

Man, that was easy. Cheers. I've moved /tmp to RAM and added discard for my root partition in Linux.

I'm getting some pretty impressive benchmarks.

[IMG]http://pici.se/pictures/ICgcKFwNV.png[/IMG]

I've also read that turning off EXT4 journaling will improve SSD performance? Anyone know this to be true? Is journaling not needed for a SSD disk?

---

### Post by ShadowDragon on 2010-06-10
> **wconstantine said:**
> I've also read that turning off EXT4 journaling will improve SSD performance? Anyone know this to be true? Is journaling not needed for a SSD disk?

Disabling journaling isn't a SSD-specific performance improver. It will boots almost anything, because it's mainly a file-system tweak.

But SSDs don't provide anything additional to the convectional HDD which would make journaling unnecessary. So if you didn't disable it on your HDD, why would you on SSD? (BTW: current gen SSDs aren't as vulnerable to the additional writes as it used to be, so that too isn't a real solid argument in this case.)

Of course this explanation is the really short version. The pro's and the cons are already written out multiple times, so I'm not going to repeat that here ;)

(Sorry, can't provide any links, it's too long ago to find any articles back... Just try a search-engine, that's the same way I would look for it ;) )

---

### Post by Jordanwb on 2010-06-10
> **wconstantine said:**
> I'm getting some pretty impressive benchmarks.

What program did you use for that?

---

### Post by wconstantine on 2010-06-10
> **Jordanwb said:**
> What program did you use for that?

Disk Utility by Red Hat. Go to System -> Administration -> Disk Utility. If you're using Ubuntu that is.

---

### Post by andrewabc on 2010-06-10
> **wconstantine said:**
> Disk Utility by Red Hat. Go to System -> Administration -> Disk Utility. If you're using Ubuntu that is.

Only started in Ubuntu 10.04

---

### Post by Jordanwb on 2010-06-11
> **andrewabc said:**
> Only started in Ubuntu 10.04

I believe it was in 9.10. I don't find it trustworthy. It keeps saying my external hard drive has bad sectors. I've done a full check on both checks and they're fine.

But anyways.

---

### Post by andrewabc on 2010-06-11
> **Jordanwb said:**
> I believe it was in 9.10. I don't find it trustworthy. It keeps saying my external hard drive has bad sectors. I've done a full check on both checks and they're fine.

But anyways.

I'm on 9.10
Yes 'Disk Utility' is in it, but it does not have benchmark program.

Disk Utility in 9.10 is really bad compared to 10.04 version for basic info on hard drives. I'm not exactly sure what the point of it is in 9.10 :P

---

### Post by libssd on 2010-06-14
I've been laid up with a broken foot recently, so tuning Ubuntu/SSD has become a way to pass the time. Following my original post, I have upgraded to Ubuntu 10.04, and have done all the recommended things to optimize an SSD. Just for the heck of it, I completely erased the Vertex 32gb SSD using shred, and re-installed 10.04. 

As the first program after boot, I ran Disk Utility multiple times. I saw *no significant difference* in performance in Ubuntu 9.04 (no alignment) and 10.04 (partition aligned by default). Average read rates were 139.8 MB/s +- 0.01 ms. Average access times were around 0.27 ms, +-0.02 ms. Changes to the elevator parameter may have had a very small impact, with noop being perhaps .02 ms faster than cfq and .01 ms faster than deadline, but these differences are so small that I don't consider them significant.

---

### Post by moly82 on 2010-06-14
could someone kindly summarize all the optimizations I should do on my lucid lynx installed on a SSD?

I saw the many links but really wouldn't know which one I should do and which ones I do not need at all..

thanks anyway

bye!

---

### Post by Shining Arcanine on 2010-06-14
> **libssd said:**
> I've been laid up with a broken foot recently, so tuning Ubuntu/SSD has become a way to pass the time. Following my original post, I have upgraded to Ubuntu 10.04, and have done all the recommended things to optimize an SSD. Just for the heck of it, I completely erased the Vertex 32gb SSD using shred, and re-installed 10.04. 

As the first program after boot, I ran Disk Utility multiple times. I saw *no significant difference* in performance in Ubuntu 9.04 (no alignment) and 10.04 (partition aligned by default). Average read rates were 139.8 MB/s +- 0.01 ms. Average access times were around 0.27 ms, +-0.02 ms. Changes to the elevator parameter may have had a very small impact, with noop being perhaps .02 ms faster than cfq and .01 ms faster than deadline, but these differences are so small that I don't consider them significant.

You should not be seeing a difference when you are testing sequential performance. Sequential performance has never been an issue for SSDs or any kind of storage technology and it is not what modern operating systems typically do. What you want is to test random 4KB I/O performance, which is more difficult to test. You could try running IOMeter, but I am not sure if the Linux version of it works with recent kernels.

---

### Post by libssd on 2010-06-14
> **moly82 said:**
> could someone kindly summarize all the optimizations I should do on my lucid lynx installed on a SSD?

I saw the many links but really wouldn't know which one I should do and which ones I do not need at all..
There is a lot of information out there, some of it conflicting, but here are my installation tweaking notes (which are based on a lot of sources written by people far more knowledgeable than me). :p  

In all candor, these changes, collectively, do very little for performance, but may slightly reduce the number of writes to the SSD. I am using the ext4 filesystem. These changes are for a netbook with 1GB of RAM; they are not appropriate for a server. 

:-({|=  **WARNING:** Apply these tweaks at your own risk, and make sure you have a restorable backup (such as can be created by **[Remastersys]("http://geekconnection.org/remastersys/")**). 

[SIZE="4"]**SSD Optimization/Filesystem Tuning**[/SIZE]

**Note:** commands are in ***bold italics***

1. ***sudo gedit /etc/fstab***

Mount volumes using the noatime option. By default Linux will write the last accessed time attribute to files. This has performance overhead, and can theoretically reduce the life of the SSD by causing a lot of writes. The noatime mount option turns this off.

```
UUID=31b8c0a8-db49-4835-b7f0-2c1f4392ea92 /   ext4    **noatime**,errors=remount-ro 0    1
```

Mount /tmp /var/log and /var/tmp in RAM.  Add these lines to the end of fstab to mount /tmp (temporary files) as tmpfs (temporary file system):

```
   tmpfs /tmp tmpfs noexec,defaults,noatime 0 0
   tmpfs /var/tmp tmpfs noexec,defaults,noatime 0 0
```

Save, then:  ***sudo mount -a***

Reboot for the changes to take effect. Running df, you should see a new line with /tmp and /var/tmp mounted on tmpfs.

```
$ ***df***
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             30489032   3396212  25544048  12% /
none                    501464       292    501172   1% /dev
none                    508416      1500    506916   1% /dev/shm
none                    508416       100    508316   1% /var/run
none                    508416         0    508416   0% /var/lock
none                    508416         0    508416   0% /lib/init/rw
```

2. ***sudo gedit /etc/sysctl.conf***

Minimize swappiness. Ref: [http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=15549](http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=15549)
```
vm.swappiness = 10
vm.vfs_cache_pressure = 50
vm.dirty_writeback_centisecs = 20000
vm.dirty_ratio = 90
vm.dirty_background_ratio = 1
```

Many people swear that aligning a SSD is essential. Alignment is a lot of trouble, fraught with risk, and in my (limited) experience, unneeded, at least with an SSD that has a good controller like the OCZ Vertex. Other drives may respond differently. On an Acer AA1 D150 with 1.6gHz Atom processor, Ubuntu 10.04 boots in 20 seconds, shuts down in 5 seconds.

**References:**

[http://itezer.com/blog/ubuntu-linux/125-Four-Tweaks-for-Using-Linux-with-SSD.html](http://itezer.com/blog/ubuntu-linux/125-Four-Tweaks-for-Using-Linux-with-SSD.html)
[http://blog.bodhizazen.net/linux/netbook-optimization/](http://blog.bodhizazen.net/linux/netbook-optimization/)
[http://samiux.wordpress.com/2009/06/09/howto-ubuntu-9-04-desktop-on-solid-state-disk-ssd/](http://samiux.wordpress.com/2009/06/09/howto-ubuntu-9-04-desktop-on-solid-state-disk-ssd/)
[http://www.linux-mag.com/id/7599/2/](http://www.linux-mag.com/id/7599/2/)

---

### Post by andrewabc on 2010-06-14
> **moly82 said:**
> could someone kindly summarize all the optimizations I should do on my lucid lynx installed on a SSD?

I saw the many links but really wouldn't know which one I should do and which ones I do not need at all..

thanks anyway

bye!

We need to know what model of SSD you have and what firmware version it has.

---

### Post by Shining Arcanine on 2010-06-14
> **libssd said:**
> There is a lot of information out there, some of it conflicting, but here are my installation tweaking notes (which are based on a lot of sources written by people far more knowledgeable than me). :p  

In all candor, these changes, collectively, do very little for performance, but may slightly reduce the number of writes to the SSD. I am using the ext4 filesystem. These changes are for a netbook with 1GB of RAM; they are not appropriate for a server. 

:-({|=  **WARNING:** Apply these tweaks at your own risk, and make sure you have a restorable backup (such as can be created by **[Remastersys]("http://geekconnection.org/remastersys/")**). 

[SIZE="4"]**SSD Optimization/Filesystem Tuning**[/SIZE]

**Note:** commands are in ***bold italics***

1. ***sudo gedit /etc/fstab***

Mount volumes using the noatime option. By default Linux will write the last accessed time attribute to files. This has performance overhead, and can theoretically reduce the life of the SSD by causing a lot of writes. The noatime mount option turns this off.

```
UUID=31b8c0a8-db49-4835-b7f0-2c1f4392ea92 /   ext4    **noatime**,errors=remount-ro 0    1
```

Mount /tmp /var/log and /var/tmp in RAM.  Add these lines to the end of fstab to mount /tmp (temporary files) as tmpfs (temporary file system):

```
   tmpfs /tmp tmpfs noexec,defaults,noatime 0 0
   tmpfs /var/tmp tmpfs noexec,defaults,noatime 0 0
```

Save, then:  ***sudo mount -a***

Reboot for the changes to take effect. Running df, you should see a new line with /tmp and /var/tmp mounted on tmpfs.

```
$ ***df***
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             30489032   3396212  25544048  12% /
none                    501464       292    501172   1% /dev
none                    508416      1500    506916   1% /dev/shm
none                    508416       100    508316   1% /var/run
none                    508416         0    508416   0% /var/lock
none                    508416         0    508416   0% /lib/init/rw
```

2. ***sudo gedit /etc/sysctl.conf***

Minimize swappiness. Ref: [http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=15549](http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=15549)
```
vm.swappiness = 10
vm.vfs_cache_pressure = 50
vm.dirty_writeback_centisecs = 20000
vm.dirty_ratio = 90
vm.dirty_background_ratio = 1
```

Many people swear that aligning a SSD is essential. Alignment is a lot of trouble, fraught with risk, and in my (limited) experience, unneeded, at least with an SSD that has a good controller like the OCZ Vertex. Other drives may respond differently. On an Acer AA1 D150 with 1.6gHz Atom processor, Ubuntu 10.04 boots in 20 seconds, shuts down in 5 seconds.

**References:**

[http://itezer.com/blog/ubuntu-linux/125-Four-Tweaks-for-Using-Linux-with-SSD.html](http://itezer.com/blog/ubuntu-linux/125-Four-Tweaks-for-Using-Linux-with-SSD.html)
[http://blog.bodhizazen.net/linux/netbook-optimization/](http://blog.bodhizazen.net/linux/netbook-optimization/)
[http://samiux.wordpress.com/2009/06/09/howto-ubuntu-9-04-desktop-on-solid-state-disk-ssd/](http://samiux.wordpress.com/2009/06/09/howto-ubuntu-9-04-desktop-on-solid-state-disk-ssd/)
[http://www.linux-mag.com/id/7599/2/](http://www.linux-mag.com/id/7599/2/)
A few observations:

[LIST]
[*]Mounting stuff with noatime is a good idea.
[*]Mounting a tmpfs to /var/tmp might not be a good idea because some distributions put stuff there that is not supposed to be deleted on a regular basis. In particular, deleting /var/tmp/alsaconf.cards should require that alsaconfig is run to regenerate it, which likely does not happen automatically. Not all distributions use ALSA and while I do not know what Ubuntu uses, it could use ALSA, which would make mounting /var/tmp as a tmpfs directory a problem unless it puts the alsaconf.cards file somewhere else.
[*]You do not need to reboot to add tmpfs directories to your system. For example, you can run [COLOR="Green"]mount -t tmpfs tmpfs /tmp[/COLOR] to mount a tmpfs at /tmp. Running [COLOR="Green"]rm -rf /tmp[/COLOR] before to mounting a tmpfs might be a good idea to clear out anything under the mount point.
[*]So far, I have not been able to find a reason to use vm.swappiness = 10 over vm.swappiness = 0 on SSDs. It probably would be best to use vm.swappiness = 0. As for the other things you suggest putting into /etc/sysctl.conf, I am not sure if they are a good idea. I have not seen any benchmarks justifying their use and it is not clear exactly what they do in place of the default values. The default values were picked by the kernel developers themselves and have been extensively tested. I am not sure what value changing them could provide, especially when the single change of vm.swappiness = 0 will stop all unnecessary swap activity. This also has nothing to do with ssd/filesystem tuning and a little something to do with SSD longevity; the two are not the same thing.
[*]If you are not willing to align your SSDs, you might as well just not bother to do anything special with them.
[/LIST]

---

### Post by Husein Poonawala on 2010-06-14
This is interesting. Let me take a look and see what I can come up with.
 
Husein Poonawala

---

### Post by Jordanwb on 2010-06-14
> **libssd said:**
> Alignment is a lot of trouble, fraught with risk, and in my (limited) experience, unneeded, at least with an SSD that has a good controller like the OCZ Vertex.

Aligning is easy with gparted. I don't know about the version in lucid but the one is meerkat can align just fine if you disable "Round to cylinders".

---

### Post by moly82 on 2010-06-15
> **libssd said:**
> There is a lot of information out there, some of it conflicting, but here are my installation tweaking notes (which are based on a lot of sources written by people far more knowledgeable than me). :p  

In all candor, these changes, collectively, do very little for performance, but may slightly reduce the number of writes to the SSD. I am using the ext4 filesystem. These changes are for a netbook with 1GB of RAM; they are not appropriate for a server. 

:-({|=  **WARNING:** Apply these tweaks at your own risk, and make sure you have a restorable backup (such as can be created by **[Remastersys]("http://geekconnection.org/remastersys/")**). 

[SIZE="4"]**SSD Optimization/Filesystem Tuning**[/SIZE] 
...
...
[CUT]


> **andrewabc said:**
> We need to know what model of SSD you have and what firmware version it has.

thanks a lot libssd and andrewabc for your answers.

Actually more than optimize the install to get faster reading/writings I am interested in reducing the SSD writings to hopefully increase the SSD life, I should have specified that in my post, sorry. 
I am really not so interested in improving performances, ubuntu is already quite fast here, but what worries me are the writings as I have alread had to get rid of my (expensive) Runcore SSD 64 GB recently because (I guess) it has almost died (I forgot how many times I installed linux, osx etc on it, how many gigs of stuff I copied, pictures, music, movies etc :( )

that said, I'm on a eeePC 901 running (now) with the default SSDs (both by Asus, 4 gb the first one, soldered, faster, while the second has 16gb and it is removable and much slower, I resintalled it after throwing away the runcore ssd mentioned above).  

I don't know the firmwares, if you are still interested in knowing them where can I look, in the bios?

finally, just to let you know how I did install lucid lynx (which is simply great actually, I think I got to the final OS at last, even better than Snow Leopard, at least it is way way more stable than the hacked osx I tried :) ): 

- first (fast) SSD, 1 partition only (about 3.8gb) where I installed / 
- second (slower) SSD, two partitions, 1 for the swap (about 800mb) and one for the /home (about 15gb)

I will try your suggestions in the meantime LIBSSD, thanks again! (do I need also to install kernel 2.6.34? I am on 2.6.32.something now)

bye all!

---

### Post by moly82 on 2010-06-15
> **nhasian said:**
> to install the linux 2.6.34 kernel, follow my post [here]("http://ubuntuforums.org/showpost.php?p=9348970&postcount=8")


installing kernel 2.6.34 this way, will it be later updated automatically (when new kernels will be released officially for lucid) using SW update or apt-get dist-upgrade from terminal?

thanks! :)

---

### Post by libssd on 2010-06-15
Aligning with gparted isn't feasible on a netbook with 1024x600 resolution, as it requires a minimum of 1024x768. Once you have done it a few times, fdisk really isn't too bad -- as long as you are confident that you have a restorable backup. I'm working on an erase/partition/align/re-install doc; sort of the "idiot's" guide to alignment.

Thank you very much for comments, Shining Arcanine. Opinions are all over the place on /etc/syctl.conf values. Some advocate vm.swappiness = 0, some 1, and some 10, but all agree that the default value is too high for an SSD and a decent amount of RAM (e.g., 1GB). There is a similar range of opinions for vm.dirty_writeback_centisecs. I chose the values I did because I have only 1 gb of RAM, and I have defined 256MB as swap space; I was  concerned about running out of memory, and thought these values would result in less memory usage -- but I could be completely misunderstanding what these parameters do! :p

---

### Post by libssd on 2010-06-15
Can anybody enlighten me about head and sector calculations? I think I understand why the cylinder size should equal the erase block size, but does it matter how the heads and sectors are defined? All these values work:

512K:
  -S 8 -H 128
  -S 16 -H 64
  -S 32 -H 32

Is there any practical benefit to choosing one over another?

---

### Post by moly82 on 2010-06-16
> **Shining Arcanine said:**
> A few observations:

[*]... Running [COLOR="Green"]rm -rf /tmp[/COLOR] before to mounting a tmpfs might be a good idea to clear out anything under the mount point...

this completely ****ed up my install.. thanks a lot.. :mad:

error at boot: gconf-sanity-check-2 exited with status 256

someone else had the exact same error after playing with the /tmp folder so..

[http://ubuntuforums.org/showpost.php?p=9125449&postcount=18](http://ubuntuforums.org/showpost.php?p=9125449&postcount=18)

already tried with no success all the suggestions in that thread so I will have to reinstall..
 
regards

---

### Post by libssd on 2010-06-16
I'm working on a "foolproof" (HAH!) guide to aligning an SSD, and have two questions:

1. Assuming an erase block size of 512kb, most people recommend creating a cylinder size of 1024, from the product of Heads times Sectors. A commonly recommended value is 32 H 32 S. Why? Are there any benefits/liabilities to other ratios, such as (at the extreme) 2x512 or 512x2?

2. Unless trim is supported, the commonest recommendation I have found to refresh a badly fragmented SSD is to completely erase the SSD to restore all memory cells to their original condition. Will sudo shred -n1 have the same effect as doing an ATA security erase using hdparm? [This procedure]("https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase") for using hdparm is considerably more daunting than using shred.

---

### Post by steveneddy on 2010-06-16
> **systemarpi said:**
> take care of write/erase **cicles**.



Only if we can discuss 

**icycle**'s

also.

Oh wait - did you mean to type cycles?

My bad.

---

### Post by andrewabc on 2010-06-16
> **libssd said:**
> I'm working on a "foolproof" (HAH!) guide to aligning an SSD, and have two questions:

1. Assuming an erase block size of 512kb, most people recommend creating a cylinder size of 1024, from the product of Heads times Sectors. A commonly recommended value is 32 H 32 S. Why? Are there any benefits/liabilities to other ratios, such as (at the extreme) 2x512 or 512x2?


Hmm, I think if erase block is 512kb, then cylinder(sector?) size should be same.
At least for vertex Indilinx ssd.

Damn, I just read a review the other day where they compare different sizes and which perform better. I think it was a RAID0 review of vertex1. And I think the conclusion was to use erase size of 512kb.

---

### Post by libssd on 2010-06-16
The Vertex block size is 512kb. But, my question was, assuming a cylinder size that aligns with the erase block size, does it matter what combination of heads/sectors is used to generate that cylinder size? 32x32=1024, but so does 1x1024 or 512x2. Why choose 32x32 over other combinations, other than the fact that these are nice, easy to remember numbers?

---

### Post by Shining Arcanine on 2010-06-16
There are 11 different choices you can make. I doubt it makes a difference. Once everything is on the disk, the figures you set will likely be meaningless, just as long as everything is aligned correctly.

---

### Post by syngiun on 2010-06-17
I have an Intel X-25M G2 with the latest firmware. I installed Lucid, tweaked quite a bit, and booted on average in 10-13 secs (bootchart). Then I discovered that 2.6.32 doesn't support trim. GRRRR  Off to Fedora i go...

is there yet a safe and update friendly way to upgrade to a later kernel? 

Call me lazy or chicken or whatever you like, I don't care. I just don't like going thru hours of repeated tweaking and customizing every time I have to re-install. I tend to do everything manually cuz i don't trust auto installer scripts.

---

### Post by libssd on 2010-06-17
> **Shining Arcanine said:**
> There are 11 different choices you can make. I doubt it makes a difference. Once everything is on the disk, the figures you set will likely be meaningless, just as long as everything is aligned correctly.
This is what I suspected; 32x32 is easy to remember, so I'm sticking with it.

---

### Post by libssd on 2010-06-17
> **syngiun said:**
> I have an Intel X-25M G2 with the latest firmware. I installed Lucid, tweaked quite a bit, and booted on average in 10-13 secs (bootchart). Then I discovered that 2.6.32 doesn't support trim. GRRRR  Off to Fedora i go...

is there yet a safe and update friendly way to upgrade to a later kernel? 

Call me lazy or chicken or whatever you like, I don't care. I just don't like going thru hours of repeated tweaking and customizing every time I have to re-install. I tend to do everything manually cuz i don't trust auto installer scripts.
Like aligning partitions, changing the kernel is one of those things that seems terrifying until you have done it.

Short and sweet: [Switch to a newer kernel in Ubuntu 10.04]("http://usablesoftware.wordpress.com/2010/05/26/switch-to-a-newer-kernel-in-ubuntu-10-04/")

Of course, make sure you have a restore disk or USB available. :p

I ran a later kernel (which fixed a couple of minor hardware compatibility problems) with 9.04 for about 6 months, and the only problem I had was that Remastersys would not work properly with it; Unfortunately, the problem with Remastersys was not revealed until I tried to restore from backup! If I booted under the standard kernel for 9.04 (hold down Shift key before grub starts to access the boot menu), Remastersys worked just fine.

---

### Post by jromma on 2010-06-21
Sorry for the noobish question, but how exactly do you enable trim in kernels 2.6.33 and later? I'm running kernel 2.6.35 now with an intel SSD, and I haven't done anything to improve performance with my SSD except put the discard option in my fstab file. So far my read performance is great (242 Mb/s average), but from what I understand TRIM only really helps write speeds. TRIM isn't automatically turned on, right? Thanks

---

### Post by nhasian on 2010-06-21
if your already running kernel 2.6.35 and have added the discard option to /etc/fstab then trim is already enabled.  optionally you can mount /tmp to ram or i just bind it to my secondary HDD drive.

> **jromma said:**
> Sorry for the noobish question, but how exactly do you enable trim in kernels 2.6.33 and later? I'm running kernel 2.6.35 now with an intel SSD, and I haven't done anything to improve performance with my SSD except put the discard option in my fstab file. So far my read performance is great (242 Mb/s average), but from what I understand TRIM only really helps write speeds. TRIM isn't automatically turned on, right? Thanks

---

### Post by andrewabc on 2010-06-21
Assuming TRIM is set up properly, in order to 'activate' (run) it, you need to delete a file (empty recycle bin/trash).
At least that is what I remember hearing a while ago.

---

### Post by mr_raider on 2010-06-27
2.6.34 won't allow my my bcmwl and fglrx modules to build. any solutions?

---

### Post by Elysius on 2010-07-03
Where do I add the noatime and discard option? The example fstab files are different than mine. This is how mine looks like. :confused:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e404377d-1d35-41d1-bcfd-760371b8247a /               ext4    errors=remount-ro 0       1

# mounting tmpfs
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

```

---

### Post by Shining Arcanine on 2010-07-03
> **Elysius said:**
> Where do I add the noatime and discard option? The example fstab files are different than mine. This is how mine looks like. :confused:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e404377d-1d35-41d1-bcfd-760371b8247a /               ext4    errors=remount-ro 0       1

# mounting tmpfs
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

```

Replace errors=remount-ro with errors=remount-ro,noatime,discard

---

### Post by Bakmeel on 2010-07-09
Did I understand correctly that TRIM is only supported on ext4?

I decided to install my system on Ext2, because Ext3 and Ext4 have journalling which would imply additional write cycles. In fact, according to [http://en.wikipedia.org/wiki/Ext2](http://en.wikipedia.org/wiki/Ext2) Ext2 is the filesystem of choice for SSD, SD and Flash USB.

Did I just upgrade my kernel for no good reason?

---

### Post by Paqman on 2010-07-09
> **Bakmeel said:**
> In fact, according to [http://en.wikipedia.org/wiki/Ext2](http://en.wikipedia.org/wiki/Ext2) Ext2 is the filesystem of choice for SSD, SD and Flash USB.


SD and Flash definitely, and probably early/cheap SSDs too. For a recent SSD with decent wear levelling then write cycles isn't really worth worrying about IMO. I'd rather have the significant extra performance of Ext4 than a small improvement in lifespan.

---

### Post by Jordanwb on 2010-07-09
> **Bakmeel said:**
> Did I understand correctly that TRIM is only supported on ext4?
Yes

> **Bakmeel said:**
> I decided to install my system on Ext2, because Ext3 and Ext4 have journalling which would imply additional write cycles.
You can create an ext4 filesystem without a journal, I don't know how though.


> **Bakmeel said:**
> Did I just upgrade my kernel for no good reason?
Yeah

---

### Post by Bakmeel on 2010-07-10
> **Jordanwb said:**
> Yeah

Bugger. :x

---

### Post by wiresquire on 2010-07-14
Just thought I would add a little workaround that was frustrating me no end. I'd also seen a couple of posts that mentioned similar symptoms.

**The disclaimer**
* As always, YMMV ;)
* Don't mess with partition tables without having backups!!

**The problem**
I had been trying to set up the SSD with -H 32 -S 32 using fdisk, as mentioned in several guides/threads to align partitions. What happened is that setting did not 'stick'. It constantly reverted back to 255 heads and 63 sectors/track. This happened when I used the Ubuntu 10.04 live CD, or when I was using sysrescuecd 1.5.8.

I was setting up four primary partitions.

**The investigation**
After messing around a little bit, it turned out that it was *only when adding the 4th primary partition* that it reverted to 255/63. After a little experimenting, it turned out that *it only reverted back to 255/63 when you used up nearly all the disk*. Eg, setting the 4th partition to the end of the disk caused it to revert. My last sector is now set ~68K sectors from the end of the disk; and the 32/32 holds. Note that your disk may be different, Just set the last sector on the last partition to be 1 sector less than a multiple of 2048 so as to align with the erase block size. Save the change and try listing from the terminal using fdisk -ucl. It should still show "32 heads, 32 sectors/track". If it doesn't try again with the partition a little smaller. When it does 'stick' reboot and check it again. 

I didn't spend any time on 'minimising; 68K sectors is only ~39KB. Don't even really understand what caused it. Maybe it's a bug in fdisk. Maybe it's my machine. Don't really care as it seems I have worked around it.

**The summary**
When the 4th (or last) partition was set somewhat before the end of the disk, the 32 heads and 32 sectors setting is permanent. When it went to the last sector, this caused the heads to be reset to 255 and the sectors/track to be 63.

hth
ws

PS: You may also 'lose' your setting of 32 heads and 32 sectors/track if you dual boot and run certain of the 'repair' options in windows. That is probably a topic for another day...

---

### Post by Bakmeel on 2010-08-16
> **libssd said:**
> Mount /tmp /var/log and /var/tmp in RAM.  Add these lines to the end of fstab to mount /tmp (temporary files) as tmpfs (temporary file system):

```
   tmpfs /tmp tmpfs noexec,defaults,noatime 0 0
   tmpfs /var/tmp tmpfs noexec,defaults,noatime 0 0
```Save, then:  ***sudo mount -a***

Reboot for the changes to take effect. Running df, you should see a new line with /tmp and /var/tmp mounted on tmpfs.


I have succeeded in getting the temp files to RAM and I am considering to put the logfiles there too. However, I am aware that when I reboot these files are lost and that is not desirable.

I have made a crontab to back up the logfiles every day at midnight:

```
sudo crontab -l -u root

# m h  dom mon dow   command
  0 0   *   *   *    cp -r /var/log/* /var/log_local/
```But that doesn't solve the issue of restoring some of the logfiles when I reboot the system, and some services like apache won't come back online.

Has anyone tried to restore the logfiles to the ramdisk at reboot using:

```
# m h  dom mon dow   command
@reboot cp -r /var/log_local/* /var/log/
```Any alternatives to restore the logs at reboot?

---

### Post by Bakmeel on 2010-08-19
Apparently nobody has tried it, so I did :-)

And it works! 
Now, each night the logfiles will be copied from the memory to the SSD.
Upon reboot, the logfiles are restored and all services resume operation as normal.

Now I just need a small script to make an additional backup when I shut down

---

### Post by schmickey on 2010-09-12
I will be receiving my new Intel X25M G2 80GB SSD in a couple of days.  It supposedly already has the latest firmware installed.

A comprehensive guide for Lucid installation and tweaks would be awesome -- either here or in another section of the Forum.  If this has already been done, could someone advise me where in the Forum it is located?  I've just read this entire thread and have come away somewhat confused.

Should I just wait for Meerkat?  (Newer kernel, perhaps better support for SSDs overall)?

I have just enough Linux knowledge to be dangerous, not enough to be truly competent -- so a detailed instructional guide would be something many of us would love to have in order to extend the life and increase the performance of our SSDs.  I realize there will always be conflicting opinions about settings (tweaks) but I would think that by now some experience would shed some light on what works and what doesn't.

Thanks!

---

### Post by Jordanwb on 2010-09-12
Use gparted to create the partitions, when creating them untick the "round to cylinders" box. You can install a 2.6.35 kernel in lucid if you wish via the [kernel ppa]("https://launchpad.net/~kernel-ppa/+archive/ppa"). In /etc/fstab, add the "discard" flag for all partitions on your SSD. That's all there is to it.

---

### Post by schmickey on 2010-09-13
> **Jordanwb said:**
> Use gparted to create the partitions, when creating them untick the "round to cylinders" box. You can install a 2.6.35 kernel in lucid if you wish via the [kernel ppa]("https://launchpad.net/~kernel-ppa/+archive/ppa"). In /etc/fstab, add the "discard" flag for all partitions on your SSD. That's all there is to it.

Thanks!  What about swappiness?  Would you recommend setting that to "0" (I have 4GB RAM)?  And the ramdrive/temp files tweak?  Would that cut down on a lot of writes?

---

### Post by Jordanwb on 2010-09-13
Don't put a swap partition on an SSD. You can put /tmp on a tmpfs file so:

```
tmpfs /tmp tmpfs rw 0 0
```

You can also set firefox to use /tmp as it's temporary storage but I don't know how.

---

### Post by schmickey on 2010-09-13
Thanks.  There is another thread in the Hardware & Laptops section that I will be posting my SSD experience in... [Here]("http://ubuntuforums.org/showthread.php?t=1558489")

If I can find some good Linux disk benchmarking software, I'll post results, both for the original platter HDD and the SSD.

EDIT: My laptop (a new model)-(HM55 Chipset) runs hot and drains battery fast with Lucid and no matter what I do the SSD performance seems much slower. I'm going to wait for Maverick (10.10) or Natty (11.04) since there should be (might be?) many changes to accommodate this chipset and help with SSD setup & maintenance (newer kernel, etc.) and power management.

Hopefully, by then, there will be a comprehensive guide for SSD owners somewhere in the hardware and laptops section. I will contribute to it myself as I have time.  Or, even better, maybe no special tweaks will be needed for SSDs or HM55 chipsets in upcoming releases. Thanks.

---

### Post by amgalitz on 2010-10-22
Wishing to keep with the 'kiss' principle, I've just left my ssd as one large partition which I believe removes the issue of alignment. I've left the /home and /swap partitions on a moderately fast harddisk (WD Black)

I've used the noatime and discard in fstab for when the 10.04 kernel gets backported.

fstab entry:
```

UUID=e3e294b8-40cd-4c4c-969e-135b7530db9d / ext4 noatime,discard,errors=remount-ro 0 1
```

To speed up wine / crossover programs loading, I copied the ~/cxoffice and ~/.cxoffice folder to a folder on the ssd which has the ownerships and permissions matching my home folder. I left, but renamed the original versions ~/cxoffice-b and ~/.cxoffice-b and created empty folders to serve as mount points: ~/cxoffice and ~/.cxoffice.

to mount these at boot, added to fstab:
```
/ssd/cxoffice /home/myusername/cxoffice none defaults,noatime,bind 0 0
/ssd/.cxoffice /home/myusername/.cxoffice none defaults,noatime,bind 0 0

```

without a reboot I did 
```
sudo mount -a
```

Now my wine / crossover linux program startup quite fast and I hear no disk activity.

I plan to move some of the frequently changing data files for wine programs that are not already in my ~/documents folders from the folders ~/.cxoffice to ones in my ~/ directory. Usually though I'm working on folders already in my ~/ hardisk folders even when using a wine based program. 

I think this trick could work well to speed up user space programs that load many files from /home without overly wearing the ssd.


I still need to run evernote and msoffice for my profession.

I'm using a Corsair CSSD-V32GB2 connected through a HighPoint Rocket620a dual SATAIII (but the ssd is only SATAII) on a gigabyte GIGABYTE GA-MA785GM-US2H, AMD Phenom II x3 720
Read times are 199.5 (min), 246.9 (max), 223.9 MB/s per the ub 10.04 disk utility read benchmark. 2.6.32-25 generic kernel.

Ubuntu loads scary fast now. I've another ssd coming for my wife's machine since she heavily uses msoffice.

Hope this helps.

a

---

### Post by 116North on 2010-10-25
For a pretty good blog post on aligning the partitions for a new install, see: [http://thunk.org/tytso/blog/2009/02/20/aligning-ACfilesystems-to-an-ssds-erase-block-size/](http://thunk.org/tytso/blog/2009/02/20/aligning-ACfilesystems-to-an-ssds-erase-block-size/)

---

### Post by andrewabc on 2010-10-26
> **116North said:**
> For a pretty good blog post on aligning the partitions for a new install, see: [http://thunk.org/tytso/blog/2009/02/20/aligning-ACfilesystems-to-an-ssds-erase-block-size/](http://thunk.org/tytso/blog/2009/02/20/aligning-ACfilesystems-to-an-ssds-erase-block-size/)

You got link wrong.

So I went and found al relevant ssd links in his blog up to that post.
They were written in early 2009.

[http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/](http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/)
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
[http://thunk.org/tytso/blog/2009/02/22/should-filesystems-be-optimized-for-ssds/](http://thunk.org/tytso/blog/2009/02/22/should-filesystems-be-optimized-for-ssds/)

---

### Post by MrSnowmiss on 2010-12-02
Very interesting to read all this.

Today I received an OCZ Vertex II 60GB SSD to install my (K)ubuntu on. Seems I have to do some more reading before I put it in my pc and start installing ;)

---

