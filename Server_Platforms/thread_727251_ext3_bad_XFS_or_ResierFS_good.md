---
title: "ext3 bad? XFS or ResierFS good?"
date: 2008-03-17
forum: Server Platforms
---

### Post by Technoviking on 2008-03-17
We are planning to switch a digital collection we run on CnntentDM from Windows 2003 using NTFS to Ubuntu Server 8.04 (when it is final). The collection is hundreds of thousands of graphic files. Would it make sense to using XFS or ResierFS over ext3?
=========================================
[from vendor, assumed we were going to use RedHat Enterprise and not Ubuntu]
I saw your recent request to do a Linux evaluation of CONTENTdm and wanted to get in touch with you to discuss a potential issue. Linux (specifically Red Hat Enterprise Linux) has a fundamental file system limitation that can compromise the functionality of CONTENTdm collections. I know that you all have a LOT of data and some very large collections, so this limitation will almost certainly be encountered during your Linux evaluation if you are planning to use Red Hat Enterprise. The problem is easy to work around if an alternate file system is used, but Red Hat explicitly does not support any file systems other than these non-scalable ext2/ext3 volumes. Nearly all other Linux distributions support file systems that do not have this problem (e.g. XFS, ReiserFS).
 
Are you planning to deploy CONTENTdm on Red Hat Enterprise Linux? If you'd like to discuss this in more detail, let me know a good time to reach you and the best number to use.
=========================================

Thanks,
Mike

---

### Post by netlogic on 2008-03-17
Isn't Han Resier in jail? Since, I haven't heard who took over his project, I will stick with ext3 until ext4 comes out.

---

### Post by HermanAB on 2008-03-17
JFS is likely the best for what you want to do.  XFS won't be bad either.  Ext3 wastes a lot of disk space, so I don't like it.  I only use Ext3 when I need to encrypt a drive.

---

### Post by kerry_s on 2008-03-17
i prefer jfs myself. i tried all of them and jfs just rocks, recovery after failure is incredible, there's almost no pause to check the fs.
i forgot> jfs & elevator=deadline <for fast systems> jfs & elevator=noop or as <for older slower systems, i use noop on mine.

---

### Post by articpenguin on 2008-03-17
if you have hundereds of thousands i would diffently avoid ext3.

1. Fixed amount of inodes usually have around 800k inodes on a 15GB drive.

2. Will NOT scale well with lots of files in a directorys.


I would recommend JFS, because

1. It uses dynamic inodes.
2.It uses a b+ tree to help with REALLY big directorys.

---

### Post by piousp on 2008-03-17
Maybe you already read this, but here is it just in case:

[JFS]("http://en.wikipedia.org/wiki/JFS_%28file_system%29")

[XFS]("http://en.wikipedia.org/wiki/XFS")

[ext3]("http://en.wikipedia.org/wiki/EXT3")

[NTFS]("http://en.wikipedia.org/wiki/Ntfs")

Good luck!

---

### Post by jayson.rowe on 2008-03-17
Not too much to add, but wanted to chime in once more for JFS - I've had great luck using it as the file system for the drive that holds my VMWare machines on my VMWare host server.

Very fast, and great with dealing w/ large files. 

Also research your scheduler options (noop/deadline/as/cfq) - I like the default (cfq) on a desktop system, but I use noop for virtual machines (let the host handle that, not the virt.) and deadline for my VMWare host.

---

### Post by DDuong on 2008-03-17
I say XFS or JFS.

---

### Post by syxbit on 2008-03-18
JFS for right now
but BTRFS as soon as it's stable (Oracle's answer to ZFS)

---

### Post by jrusso2 on 2008-03-18
I agree with JFS.  At least until something better comes out.  Its too bad development is ending on our best file system.

EXT 3 has too many issues to use for servers.

I am hoping we can get something like ZFS someday.

---

### Post by jrusso2 on 2008-03-18
> **netlogic said:**
> Isn't Han Resier in jail? Since, I haven't heard who took over his project, I will stick with ext3 until ext4 comes out.

From what I have read Namesys Han's Reisers company has continued development of Reiser FS

---

### Post by articpenguin on 2008-03-18
> **jrusso2 said:**
> I agree with JFS.  At least until something better comes out.  Its too bad development is ending on our best file system.

EXT 3 has too many issues to use for servers.

I am hoping we can get something like ZFS someday.

Development did not end on JFS. Its just maintained part time.

---

### Post by articpenguin on 2008-03-18
> **syxbit said:**
> JFS for right now
but BTRFS as soon as it's stable (Oracle's answer to ZFS)

BTRFS wont be stable until at least 2010.


I think we wont get a new filesystem to early next year when ext4 is ready.

---

### Post by wieman01 on 2008-03-18
Also 'ext3' is subject to fragementation similar to FAT32/NTFS when it stores a multitude of smaller files. So I heard it is not suitable for file servers and in particular email services. I would avoid it.

---

### Post by articpenguin on 2008-03-18
> **wieman01 said:**
> Also 'ext3' is subject to fragementation similar to FAT32/NTFS when it stores a multitude of smaller files. So I heard it is not suitable for file servers and in particular email services. I would avoid it.

I wouldnt think ntfs would be affected by this if the file was under say 600 bytes since ntfs stores the file in its inode or whatever microsoft calls it on windows.

---

### Post by Technoviking on 2008-03-18
Thanks for all the advice, we are going to use JFS for our data partition.

---

### Post by piousp on 2008-03-18
Just one quick questions,
¿what FS is better for my daily use? By daily use I mean, programming, and anime (mostly :lolflag: ).

---

### Post by wieman01 on 2008-03-18
> **piousp said:**
> Just one quick questions,
¿what FS is better for my daily use? By daily use I mean, programming, and anime (mostly :lolflag: ).
Use 'ext3' as most other Linux users do. It saves you a lot of trouble should anything go wrong.

---

### Post by justin whitaker on 2008-03-18
Don't know if you guys have seen this, but there is a nice overview of file systems over on Ars Technica.

[http://arstechnica.com/articles/paedia/past-present-future-file-systems.ars](http://arstechnica.com/articles/paedia/past-present-future-file-systems.ars)

---

### Post by piousp on 2008-03-18
I was thinking if there was a better option for me. I already use, and i've using ext3 since 6.06 and i'm happy with it. I was just wonderig... Thanks anyway

---

### Post by wieman01 on 2008-03-18
> **piousp said:**
> I was thinking if there was a better option for me. I already use, and i've using ext3 since 6.06 and i'm happy with it. I was just wonderig... Thanks anyway
If it works for you, I would not change it.'ext4' could be an option sometime next year, but up to now I would just stick with it.

---

### Post by piousp on 2008-03-18
yep, no problems so far. Mmm, maybe i can try a different one with heron, since i'm ready for a clean install. What do you think? Or is not even worth the try?

---

### Post by wieman01 on 2008-03-18
> **piousp said:**
> yep, no problems so far. Mmm, maybe i can try a different one with heron, since i'm ready for a clean install. What do you think? Or is not even worth the try?
I really don't know although I heard good stuff concerning XFS. But come to a conclusion yourself and do a bit of homework and reading. I cannot advise here as I have little experience with other file systems. I could not think of any benefits if you ask me.

---

### Post by piousp on 2008-03-18
Well, since i posted the links for the differents FK wiki, i was reading 'em indeed. Let me try something as xfs vs. ext3 and i'll let you know the results ;)

---

### Post by wieman01 on 2008-03-18
> **piousp said:**
> Well, since i posted the links for the differents FK wiki, i was reading 'em indeed. Let me try something as xfs vs. ext3 and i'll let you know the results ;)
Thank you. Look forward to it. :)

---

### Post by piousp on 2008-03-18
So far, no good answer. It seems that for "daily use" there wont be any noticeable difference. I did read somewhere that xfs dont need fcsk.
Lets keep reading...

---

### Post by jimcooncat on 2008-03-18
I've been happy with ReiserFS for many years. Ext3 has been a dog compared to ReiserFS on my systems. I've switched everything over.

The technology was developed and very stable before Hans Reiser's current troubles. It was the default filesystem back when I was running Gentoo, and was the default for SuSe for a while. Namesys is currently supporting it, but really, there's not much they have to do, it just works.

Only trick to using it is to use the "notail" option on any partition that boots. That is, if you have a separate /boot partition, use the notail option on it. If you don't have a separate /boot partition, then use the notail option on your / partition.

Now Reiser4 is a totally different beast, don't confuse the two. It's very different  (strange, futuristic?) from other filesystems, and I've no idea how it works in production. If you're interested in it, best to talk to someone who has used it.

Don't let politics keep you from using good free technology.

Update 4/29/08: John Dong (jdong) has enlightened me regarding the waning support of ReiserFS. The website of the developing company, Namesys, has now gone offline. OpenSUSE did have good reasons to stop using it as the default filesystem, and I wished I'd run across their reasoning earlier (link below). I'm reevaluating, and will probably start using Ext3 instead.

[http://blog.linuxoss.com/2006/09/27/suse-102-ditching-reiserfs-as-it-default-fs/](http://blog.linuxoss.com/2006/09/27/suse-102-ditching-reiserfs-as-it-default-fs/)

---

### Post by piousp on 2008-03-18
I read in wiki that reiser4 breaks the kernel's codding standards.

---

### Post by articpenguin on 2008-03-18
i find JFS a little faster than ext3.

JFS is excellent with large files. It deletes a 2GB file in 1 sec. Ext3 takes 6 secs to delete 2GB file.


Also JFS fragments less than ext3 since it is extent based.

---

### Post by smileypaul on 2008-03-19
Ive been using Reiser on a production storage server for about 4-5 months. No real problems.. although i dnot really expect any, since the box just recieves files daily.

For some reason its slipped my mind if its Reiser4 .. ill have to look :(

I had to abandon ext3 because of the 2tb limit..

---

### Post by Medieval_Creations on 2008-03-19
> **articpenguin said:**
> i find JFS a little faster than ext3.

After coming across this thread, it spawned the urge to tinker.  :)
I haven't done any serious benchmarking, but just in my experience with everyday use JFS does seem to perform better than my previous ext3 setup.

---

### Post by gaspard.leon on 2008-03-19
I prefer JFS, except for one issue: windows compatibility...

Since I dual-boot so I can play the odd windows game that's not well supported in wine, it's nice to be able to read my linux partitions under windows... there is an IFS for ext2/3 but I have not found a free software solution to read JFS partitions under windows...

ext3 is good for ultimate support, cause it's so widely used, lot of utilities and stuff for it, however it has some serious limitations, and it's annoyingly slow to delete files...

I was considering either jfs or xfs cause I like having good performance and high limits... however after using jfs on gutsy, i installed hardy to an ext3 partition cause then when I dual boot to windows I can quickly look at my files...

will have to see if xfs has anything like an IFS (Installable File System [driver]) for windows...

Anyway overall, I like the idea of JFS.. little CPU overhead, no limitations I can see hitting anytime soon...

Obviously something like ZFS would be nice, but it's not really well supported and license means it can't be installed in the kernel, so performance will suck.

my 2 cents

---

