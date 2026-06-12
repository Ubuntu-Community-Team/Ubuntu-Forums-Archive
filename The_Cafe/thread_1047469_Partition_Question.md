---
title: "Partition Question"
date: 2009-01-22
forum: The Cafe
---

### Post by andras artois on 2009-01-22
Am I right in thinking you can have 2 or more partitions running off 1 harddrive at once?

So one partition has the OS running from it and the other partition has just got all the user's music etc on it.

Thanks.

---

### Post by gn2 on 2009-01-22
Yes that's perfectly possible, desireable even.

---

### Post by azmo35 on 2009-01-22
Hi,mate are you asking about /root and /home? Because i have 1 hd 3 partitions, 2 running 2 Os xp/ubuntu,i'm not sure if i understand your question.

---

### Post by andras artois on 2009-01-22
Is more beneficial than having two seperate harddrives doing the same thing?


> **azmo35 said:**
> Hi,mate are you asking about /root and /home? Because i have 1 hd 3 partitions, 2 running 2 Os xp/ubuntu,i'm not sure if i understand your question.

Having 1 partition running all the main OS stuff and then another partition with music, video's that sort of thing.

Thank youuuuu.

---

### Post by jbrown96 on 2009-01-22
You can have up to 4 primary partitions. If you need more than that, you can use one primary partition as an extend partition, which can then be divided up further.

About putting your data files on a separate partition; it's actually highly recommended. It makes re-installing Ubuntu much easier. Usually people create a separate /home partition, but you could also create something separate. Just choose manual partitioning when installing and create at least three partitions: 1 for swap (2x size of your ram to be safe), 1 for / which I generally make around 10GB (you don't really need a whole lot of space. I've done it with 6GB and had no problems. The third should be mounted as /home. Just remember if you re-install that when you set the mount point for you /home parition that you don't format it.

---

### Post by andras artois on 2009-01-22
What I was planning was having three partitions. The biggest being for music, video and other documents, the next biggest biggest being for windows (CAD, Video editing programs etc) and the smallest being Ubuntu.

---

### Post by Bölvaður on 2009-01-22
that would be 4 partitions:

/data   (your personal data and films and music... stuff)
/       (ubuntu)
swap    (swap partition for pagign, should be the smallest one, shouldn't need more than 512 to 1024 mb for it)
windy   (windy)

---

### Post by Slug71 on 2009-01-22
You should setup like mine. I have a 120Gb HDD.

Windows Vista on 40GB
Shared FAT32 on 45GB(Music, Pics, Video etc..)
/(root) on 15Gb
Swap 2GB
/home on 15GB

You can create the FAT32 partition with the Ubuntu installer/partitioner.
Everything on that drive can be shared by Windows and Ubuntu since Linux can read and write to FAT32 and so can Windows of course. 

Another good reason for this is that it keeps all your files safe just in case you need to reinstall any OS.

---

### Post by andras artois on 2009-01-22
> **Bölvaður said:**
> that would be 4 partitions:

/data   (your personal data and films and music... stuff)
/       (ubuntu)
swap    (swap partition for pagign, should be the smallest one, shouldn't need more than 512 to 1024 mb for it)
windy   (windy)

That sounds like what I want.

And partitions instead of multiple harddrives would be better right?

Thanks for the answers so far!

---

### Post by deanjm1963 on 2009-01-22
I have a large hard drive and have many partitions e.g.

root, home, stuff (music, pics, etc), video, downloads and archives

the most important thing to remember is that you need to give yourself permissions to be able to write to those extra partitions.

example

if I have made a partition called "stuff" I would give myself permission to own and write to it by

sudo chown -R dean:dean /stuff
sudo chmod -R 755 /stuff

and just repeat the procedure for any extra partitions you make, but NOT for home or root as the system has already set permissions for those, and changing permissions on your root partition can lead to disaster.

hope this helps

---

### Post by CarpKing on 2009-01-22
> **Slug71 said:**
> You should setup like mine. I have a 120Gb HDD.

Windows Vista on 40GB
Shared FAT32 on 45GB(Music, Pics, Video etc..)
/(root) on 15Gb
Swap 2GB
/home on 15GB

You can create the FAT32 partition with the Ubuntu installer/partitioner.
Everything on that drive can be shared by Windows and Ubuntu since Linux can read and write to FAT32 and so can Windows of course. 

The possible downside of that is that FAT32 can't have files bigger than 4 gigs.  I have a partition for windows, a partition for /, a swap partition, and the rest is /home, which is ext3.  Then I install [this](http://www.fs-driver.org/) in Windows to give it read/write support for ext3 partitions.

---

### Post by Grant A. on 2009-01-22
Personally, I would recommend two hard drives. Mainly because the recovery disks Toshiba gives out directly attack ext3 partitions, even if an NTFS partition with nothing on it is available.

[quote="CarpKing"]
The possible downside of that is that FAT32 can't have files bigger than 4 gigs. I have a partition for windows, a partition for /, a swap partition, and the rest is /home, which is ext3. Then I install this in Windows to give it read/write support for ext3 partitions.
[/quote]

Not just that, but FAT32 doesn't have journaling so if the power goes out, all of your data could be lost. I wouldn't recommend the ext3 driver, either, as it doesn't work with ext3's journaling support and if you have a power surge, you can lose all of your data. NTFS is the best type of partition for Windows-Linux interoperability.

Here's my setup for a reference:

```

HDD 0 (320gb){
sda1:[NTFS]Windows Vista: 285GB
sda2:[NTFS]Windows Vista factory default (provided by HP): 2GB
}

HDD 1 (1TB) {
sdb1:[EXTENDED]
-----------------------
sdb5:[EXT3]Xubuntu / (root): 92GB
sdb6:[EXT3]Xubuntu /home: 92GB
sdb7:[LINUX_SWAP] Linux Swap: 2.5GB
-----------------------
sdb2:[XFS]User Files (Music, Videos, Pictures, Codes): 721GB
}

```

---

### Post by theromanone on 2009-01-23
-why would you need a "swap" partition as that seems like it would just be wasting space?

-what does ram have to do with anything, doesnt the computer use full ram no matter o.s. you boot into anyway?

---

