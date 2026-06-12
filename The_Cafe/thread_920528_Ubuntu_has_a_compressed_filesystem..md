---
title: "Ubuntu has a compressed filesystem."
date: 2008-09-15
forum: The Cafe
---

### Post by Masoris on 2008-09-15
I always wondered that why ubuntu doesn't have any compressed filesysetem. When I use Windows, I used compressed function of NTFS to save my disk space. Actually I could save much of disk space when I compress file such as text files and incomplete torrent files. But after change my main O/S to Ubuntu, I can't do that.

Today, I found one; fusecompress. [http://developer.berlios.de/projects/fusecompress/](http://developer.berlios.de/projects/fusecompress/)
That makes any filesystem to compressed filesystem. And it has many options to change compress ratio and performance. It has better compressed ratio than NTFS's one.

So I tried to find fusecompress deb package for Ubuntu. But I could find nothing. Instead of I found a needs-packaging bug report: [https://bugs.launchpad.net/ubuntu/+bug/108874](https://bugs.launchpad.net/ubuntu/+bug/108874)

To use fusecompress, I have to install manually from source code. After compiling, I could run fusecompress, and make and compress my ext3 filesystem.

It's very nice and works perfectly nevertheless it is still beta state! :)

---

### Post by miggols99 on 2008-09-15
This would be nice. Especially for people with small HDDs.

---

### Post by steeleyuk on 2008-09-15
Hows the performance?

Compressing everything would probably make reading and writing slow enough but to have to use Fuse would make it even slower. Or am I wrong?

---

### Post by macvr on 2008-09-15
i too used to keep my drive compressed in XP


what about this?>
[http://e2compr.sourceforge.net/]("http://e2compr.sourceforge.net/")
or [http://sourceforge.net/services/project_services.php?project_id=222108]("http://sourceforge.net/services/project_services.php?project_id=222108")

has anyone tried them?

also how's the performance with fuse?

---

### Post by Masoris on 2008-09-16
> **Masoris said:**
> It's very nice and works perfectly nevertheless it is still beta state! :)

Today I test again the compressed filesystem. small files works perfectly, but large file has critical problem.
It takes few times more disk space than original file. :( (Bug: [http://developer.berlios.de/bugs/?func=detailbug&bug_id=14467&group_id=5384](http://developer.berlios.de/bugs/?func=detailbug&bug_id=14467&group_id=5384))
I should find another compressed filesystem.

---

### Post by irrdev on 2008-09-16
I don't believe this should be necessary for 2 reasons:
**1)** Linux's package management system saves hundreds of megabytes by ensuring  only one version of any one library is installed at a time. On Windows, dozens of the same dlls can be scattered over different program folders, wasting lots of hard-drive space. 

**2) ** Today's new computers come with at least a 160gb hard drive, while most have 250gb drives. This is more than ample for most users; if you need more room, a 200gb usb external hard drive can be bought for around $80-$120.

---

### Post by macvr on 2008-09-16
> **irrdev said:**
> 

**2) ** Today's new computers come with at least a 160gb hard drive, while most have 250gb drives. This is more than ample for most users; if you need more room, a 200gb usb external hard drive can be bought for around $80-$120.

well .... y spend $80-$120 now
if u could fit a bit more in the present drive , could postpone a new drive!:lolflag:
guess a few of us want to squeeze the pennies:lolflag:

---

### Post by Masoris on 2008-09-16
> **steeleyuk said:**
> Hows the performance?

Compressing everything would probably make reading and writing slow enough but to have to use Fuse would make it even slower. Or am I wrong?

When I test, I mounted fusecompress with bz2 compression method. The read and write performance was:
Read without compression: 12.9MB/s
Read with bz2 compression: 7.5MB/s
Write with bz2 compression: 2.6MB/s

And text file's compression ratio was about 1:2 (200kB file become 100kB after compression).

---

### Post by Archmage on 2008-09-16
> **Masoris said:**
> I could save much of disk space when I compress file such as text files and incomplete torrent files. But after change my main O/S to Ubuntu, I can't do that.

Just a small comment on this: For incomplete torrents you should use "spare"-files. (Even under Windows.) They will only write the part of the files that they recived already.

I have to confess, that I'm strictly against compressing the files online. Especily with torrents that changed each second your CPU needs to compress the file a thousend times each second, resulting in high CPU useage and slowing down the download process as well (esspecily for big files).

This way you need to buy a higher CPU and use more electricy. Resulting that you pay in one year ten times the ammount that you are saving for not buying a larger harddrive.

Spare-files on the other hand work flawless in this case.

---

### Post by jespdj on 2008-09-16
> **Masoris said:**
> When I test, I mounted fusecompress with bz2 compression method. The read and write performance was:
Read without compression: 12.9MB/s
Read with bz2 compression: 7.5MB/s
Write with bz2 compression: 2.6MB/s

And text file's compression ratio was about 1:2 (200kB file become 100kB after compression).
And how is that compared to a normal, non-compressed ext3 filesystem on the same computer and harddisk? What are the specs of your computer?

---

### Post by macvr on 2008-09-16
> **Archmage said:**
> Just a small comment on this: For incomplete torrents you should use "spare"-files. (Even under Windows.) They will only write the part of the files that they recived already.


Spare-files on the other hand work flawless in this case.

hei, i'm a noob... so ...what exactly do u mean by spare-files?

---

### Post by oedipuss on 2008-09-16
It's a typo, he means sparse files : 
[http://en.wikipedia.org/wiki/Sparse_file](http://en.wikipedia.org/wiki/Sparse_file)

---

### Post by Masoris on 2008-09-17
I searched stable read/write compressed filesystem all day, but I could find nothing :sad:
The conclusion is linux doesn't have any stable and writeable compressed filesystem, if you want this, use NTFS on Windows, or ZFS on Solaris !!!

---

### Post by macvr on 2008-09-17
hei, i have a bit of out of topic question...
i have a 160GB western digital drive.... i want to split it[ntfs+linux partition] using partition editor

which is the best file system for video files?[with power crash min problems]
xfs/jfs/ext3

should i backup the files first?

---

### Post by egwest on 2008-09-17
> **irrdev said:**
> I don't believe this should be necessary for 2 reasons:
**1)** Linux's package management system saves hundreds of megabytes by ensuring  only one version of any one library is installed at a time. On Windows, dozens of the same dlls can be scattered over different program folders, wasting lots of hard-drive space. 

**2) ** Today's new computers come with at least a 160gb hard drive, while most have 250gb drives. This is more than ample for most users; if you need more room, a 200gb usb external hard drive can be bought for around $80-$120.

I just bought a 750gb usb external harddrive for $119 plus it had a $50 rebate on it! So if you look around a little instead of grabbing the first one you see, you can get some good deals on them.

---

### Post by hessiess on 2008-09-17
> **macvr said:**
> hei, i have a bit of out of topic question...
i have a 160GB western digital drive.... i want to split it[ntfs+linux partition] using partition editor

which is the best file system for video files?[with power crash min problems]
xfs/jfs/ext3

should i backup the files first?

I don't know which file system would be best, but you should always back up when changing the partition table, try starting a new thred.

---

### Post by irrdev on 2008-09-18
> **egwest said:**
> I just bought a 750gb usb external harddrive for $119 plus it had a $50 rebate on it! So if you look around a little instead of grabbing the first one you see, you can get some good deals on them.

WOW! :eek: That is the best deal I have seen for quite a while, and I am a frequenter of Best Buy. Can you get this deal online, or from a large retail store?

---

### Post by egwest on 2008-09-18
> **irrdev said:**
> WOW! :eek: That is the best deal I have seen for quite a while, and I am a frequenter of Best Buy. Can you get this deal online, or from a large retail store?

I got it online about 4 months ago, don't know if the $50 rebate is still in effect, but it was from New Egg:
(looks like it has dropped a few dollars since I bought it!!)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822148329&nm_mc=OTC-B1zrat3&cm_mmc=OTC-B1zrat3-_-Hard+Drives+-+External-_-Seagate-_-22148329](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148329&nm_mc=OTC-B1zrat3&cm_mmc=OTC-B1zrat3-_-Hard+Drives+-+External-_-Seagate-_-22148329)

The rebate was not listed there when I ordered it, it was inside the box and was a nice surprise when I got found it.

It was sent to me as a Master Card Debit/gift Card

---

### Post by morticae on 2008-11-25
> **irrdev said:**
> I don't believe this should be necessary for 2 reasons:
**1)** Linux's package management system saves hundreds of megabytes by ensuring  only one version of any one library is installed at a time. On Windows, dozens of the same dlls can be scattered over different program folders, wasting lots of hard-drive space. 

**2) ** Today's new computers come with at least a 160gb hard drive, while most have 250gb drives. This is more than ample for most users; if you need more room, a 200gb usb external hard drive can be bought for around $80-$120.

I think that's a pretty sweeping generalization (remember Bill Gate's famous quote to the same effect?).
I'm currently setting up an Rsync server to perform automated backups of all of our company's computers.  I have a 4.5 terabyte raid array for the purpose, but space is still at a premium.  My current solution is to just create and mount a compressed file within the drive, but I think a compressed filesystem would be more elegant and probably perform much better.

---

### Post by init1 on 2008-11-25
> **irrdev said:**
>  
**2) ** Today's new computers come with at least a 160gb hard drive, while most have 250gb drives. This is more than ample for most users; if you need more room, a 200gb usb external hard drive can be bought for around $80-$120.
Well, I'm neither using a new computer nor am I most users :D

---

### Post by insane_alien on 2008-11-25
don't see why the size of harddrives on the market is of any concern really. 

if you value space over speed then compression is for you.

you can even buy the massive drives on the cheap and still compress them :)

---

### Post by rogerdpack on 2013-01-08
Since google thinks this thread is "still relevant" thought I'd pitch in that you "should" be able to use btrfs with ubuntu, and be able to turn its compression feature on.
GL!

---

### Post by oldos2er on 2013-01-08
Old thread is old. Closed.

---

