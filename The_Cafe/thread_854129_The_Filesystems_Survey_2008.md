---
title: "The Filesystems Survey 2008"
date: 2008-07-09
forum: The Cafe
---

### Post by samjh on 2008-07-09
There has been a few threads about which filesystem people use here.  Most are quite old, and not in poll form.

So here it is: which filesystem do you use for your Linux installation?  By this, I mean what is the filesystem you MOST PREFER for a general-purpose home Linux installation.  Only filesystems supported by Ubuntu are listed.

An outline of reasons for your choice would be good too.  It may help users who are trying to decide.

(This is a poll.)

[EDIT: My choices]

My current installation uses JFS.  It is very efficient in CPU and memory usage, has good recovery rates from crashes, and has active Linux support from IBM's Linux Technology Centre.

The alternative I recommend is ext3.  It is the default filesystem for many Linux distributions and the most widely-supported Linux filesystem in existance.

---

### Post by hessiess on 2008-07-09
ext3

---

### Post by HansKisaragi on 2008-07-09
Ext3 på alle diskene mine.

---

### Post by diwas on 2008-07-09
ext3

---

### Post by FuturePilot on 2008-07-09
I like Ext3. I can't wait for Ext4 :D

---

### Post by atomkarinca on 2008-07-09
I used ext2 and ext3, couldn't tell any difference. Currently I'm using ext2 and very happy with it.

---

### Post by artir on 2008-07-09
ext3

---

### Post by beniwtv on 2008-07-09
Using XFS both on my server and my laptop. Love it so far. And it's _fast_.

---

### Post by ibutho on 2008-07-09
For my desktops, its reiserfs and for servers ext3.

---

### Post by Dr Small on 2008-07-09
ext3

---

### Post by ice60 on 2008-07-09
i've never bothered reading much about FS. i have had problems with ext3 once, so i'll go for ReiserFS as it's never given me any problems, eventhough i've no idea why i had inode errors with ext3 lol. 

Reiser is having a bit of a bad time atm, he probably shouldn't have killed is wife :|

EDIT. you should put that solaris FS up there, is it called ZFS???

---

### Post by diwas on 2008-07-09
Guys, 1 thing. Which one is latest and good?? Coz i remember while using windows (last year) i argued wid my frens that FAT32 is latest over NTFS. Hehe.
So i wud like to know, which one's good and latest.

---

### Post by cardinals_fan on 2008-07-09
ZFS.  OpenSolaris is awesome.

On Linux, Ext3.

---

### Post by Jammy4041 on 2008-07-09
Ext3- it's the default and I don't really care about it- and I shouldn't have to. As long as it works I'm happy.

TBH, I hadn't even heard of XFS, JFS and Reiser FS, but when EXT4 comes out, it would be interesting to see how that works. I think Fedora supports it so it must be coming out soon.

---

### Post by Jim! on 2008-07-09
Ext 3.....Its a shame about the whole Reiser incident :( But murdering your wife just isn't cool. I'm sure most of you have probably seen this by now but hell: [http://www.flickr.com/photos/ronocdh/2651155110/sizes/o/](http://www.flickr.com/photos/ronocdh/2651155110/sizes/o/) (ReiserFS 'Kills your wife')

---

### Post by kerry_s on 2008-07-09
i prefer jfs on mine, but sometimes i'll use ext2.

---

### Post by billgoldberg on 2008-07-09
Reiser FS here, just to be different.

---

### Post by billgoldberg on 2008-07-09
> **cardinals_fan said:**
> ZFS.  OpenSolaris is awesome.

On Linux, Ext3.

I've heared that zfs might come to linux.

But I also heared it hyped up quit a bit and isn't actually very useful on the desktop.

---

### Post by cardinals_fan on 2008-07-09
> **billgoldberg said:**
> 
But I also heared it hyped up quit a bit and isn't actually very useful on the desktop.
Is it the ultimate salvation for all *nix users that will provide the flawless and perfect file system?  No.  Is it a cool file system to mess about with?  Absolutely.

---

### Post by Chame_Wizard on 2008-07-09
Ext3 FTW :guitar:

---

### Post by LaRoza on 2008-07-09
FAT32

What is the point of just posting what you use. That is the purpose of the poll.

---

### Post by Canis familiaris on 2008-07-09
Mine:
/ ReiserFS         ..for speed presumably
/home ext3         ..for reliability

---

### Post by Canis familiaris on 2008-07-09
> **LaRoza said:**
> FAT32


Are you joking?

---

### Post by sujoy on 2008-07-09
ext3 ... never used anything else.

---

### Post by bobbocanfly on 2008-07-09
Ext3. Never had a problem with it and never found a reason to switch.

---

### Post by chucky chuckaluck on 2008-07-09
> **LaRoza said:**
> FAT32

What is the point of just posting what you use. That is the purpose of the poll.

some of us despise polls.

the first time i had arch installed, i used xfs. this time, i'm using reiserfs. with xfs, everything seemed more or less the same speed. with reiser, pacman is way fast and so is my boot, but it takes longer for cplay to open up my music folders.

---

### Post by kpatz on 2008-07-09
Most of my partitions are ext3, but the data partition on my MythTV box is JFS because it's more efficient for large files (esp. deleting).

---

### Post by ryaxnb on 2008-07-09
I would PREFER ext4, looks very promising.:popcorn: but sadly lacking in availablity so far (I would use it if it were easy to get to, despite beta-ness.) I use ext2. (Compatibility reasons) Oh and I like FAT32 for real... so darn simple. UMSDOS FTW!  :D

---

### Post by LaRoza on 2008-07-09
> **Anurag_panda said:**
> Are you joking?

Off course, I already voted for what I use.

---

### Post by dracule on 2008-07-09
are the speed differenced THAT much better?

also i think sabayon linux has ext4 by default.

---

### Post by articpenguin on 2008-07-10
All the filesystems have there special ways

XFS and JFS are the best with large file with XFS being slightly better

Reiserfs is best for tons of small files <4KB

ext3 well i dont know what its best at maybe nothing

In the end I think JFS is the best all around filesystem.


JFS XFS Reiserfs use B+ trees which help a lot in directorys with tons of files. Ext3 uses some simple Htree which is just a simplified version of a Btree since the ext3 devs feel a B+ tree compromises a filesystem if the tree corrupts.

---

### Post by YaroMan86 on 2008-07-25
I use reiserfs for my main partition, ext3 for my home partition.

---

### Post by ARhere on 2008-07-25
> **samjh said:**
> So here it is: which filesystem do you use for your Linux installation?  By this, I mean what is the filesystem you MOST PREFER for a general-purpose home Linux installation.  Only filesystems supported by Ubuntu are listed.

Should have put FAT on your list.  It is supported and there are a lot of installation configurations that use FAT as the main file system.  (*USB key is one example*)

-AR

---

