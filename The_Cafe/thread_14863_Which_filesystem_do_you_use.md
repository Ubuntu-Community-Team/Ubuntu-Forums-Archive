---
title: "Which filesystem do you use"
date: 2005-02-10
forum: The Cafe
---

### Post by lao_V on 2005-02-10
And what do you mainly use it for?

---

### Post by Viro on 2005-02-10
On my Linux boxes, I use ext3. I've used ReiserFS before, until once when there was a power failure and it *corrupted* my ReiserFS partition and I couldn't boot anymore. Sorta defeats the purpose of a journaling FS in my opinion, but I've been told the Reiser has improved since then.

Still, ext3 is much safer and I've got machines with ext3 that have been running for years without any problems. ext3 = tried and tested.

---

### Post by allans on 2005-02-10
I heard that Ubuntu would sometimes check ext3 filesystems anyway, so I went with ResierFS, wether this is true or not I'm not sure but it took my long enough to get Ubuntu playing happily with Windows so I went with that route.

---

### Post by Kakalto on 2005-02-10
I use ext3, as it's the default, tried and tested, and also, now I've installed ubuntu with ext3, I can't really be bothered trying ReiserFS out, and I don't really expect much difference in speed.

---

### Post by kassetra on 2005-02-10
I have a combination system, still.

I use ext2 for my root & boot partitions, because in an emergency, if all I have is a floppy available...

I use reiserfs for everything else.

---

### Post by Dylanby on 2005-02-10
I use a combo of reiserfs & ext3.

---

### Post by Randabis on 2005-02-10
ext3 across the board.

I use it for everything.

---

### Post by jdong on 2005-02-10
I heavily use reiserfs and reiser4. I find that:

1. ALL (that's **ALL**) filesystems can be reproducibly corrupted by abrupt shutdowns, etc.

2. Reiserfs is fast.

---

### Post by Rule on 2005-02-10
I chose Reiserfs but I don't even know the differance between ext3 and Reiserfs hahaha

---

### Post by jdong on 2005-02-10
[QUOTE=Rule]I chose Reiserfs but I don't even know the differance between ext3 and Reiserfs hahaha[/QUOTE]

Speed. Reiserfs is speed... Reiser4 is insane, too!

---

### Post by mark on 2005-02-10
The current (I think it's 3.6) version of ReiserFS for everything - /, /boot, /home and /usr.  It "feels" faster to me than ext3 (I have no objective proof of this) and, after a couple of power outages, it's checked itself at boot and come right up with no loss or corruption (that I know of <g>).

ANY filesystem can be trashed, if you work at it hard enough...

---

### Post by jdong on 2005-02-10
I will say that reiserfs is faster than ext3 for average file I/O purposes.

Example: I just reinstalled my Hoary RAID5 system, and it took about 5 minutes shorter (of 10 minutes total) to install Ubuntu! That's a pretty significant improvement over XFS! And guess what -- XFS is even faster than ext3! LOL.

---

### Post by ozar on 2005-02-10
ext3 does all I need it to do!   \\:D/

---

### Post by Rotarychainsaw on 2005-02-10
How would I go about switching to reiserfs eh?

---

### Post by Rule on 2005-02-10
can I use  Reiser4? or would it just be better to stay with reiserfs?

---

### Post by CowPie on 2005-02-11
[QUOTE=lao_V]And what do you mainly use it for?[/QUOTE]
 Reiserfs, it seems fastest.

Also, to use it in windows:

[http://yareg.akucom.de/](http://yareg.akucom.de/)
[http://p-nand-q.com/download/rfstool/download.html](http://p-nand-q.com/download/rfstool/download.html)

---

### Post by KiwiNZ on 2005-02-11
ext3 when I have Linux installed[img]http://www.ubuntuforums.org/images/smilies/icon_sad.gif[/img]

---

### Post by lao_V on 2005-02-14
I installed Ubuntu 4.10 on my laptop (Pentium 1GHz Celeron, 256DDR RAM, 10GB HD) over the weekend with reiserFS as the filesystem and it seems to working much quicker then my desktop PC (AMD 2GHz, 512DDR RAM, 120GB) which also has Ubuntu with ext3 FS.

---

### Post by topcop on 2005-02-15
not only is reiserfs faster, but it also takes a lot less space on the harddrive if you have a lot of small files. I find on a 4GB full partition i save about 300MB by using reiserfs instead of EXT2/3.

---

### Post by lao_V on 2005-02-15
[QUOTE=lao_V]I installed Ubuntu 4.10 on my laptop (Pentium 1GHz Celeron, 256DDR RAM, 10GB HD) over the weekend with reiserFS as the filesystem and it seems to working much quicker then my desktop PC (AMD 2GHz, 512DDR RAM, 120GB) which also has Ubuntu with ext3 FS.[/QUOTE]
 There was one thing I noticed when installing Ubuntu with reiserfs. Everytime I boot up, it says failed to load the 'hotplug' module.

Is this something that reiserfs cannot handle?

---

### Post by Quest-Master on 2005-02-15
ext3..  haven't bothered to look at the others. :P

---

### Post by jdong on 2005-02-15
[QUOTE=Rule]can I use  Reiser4? or would it just be better to stay with reiserfs?[/QUOTE]

Reiser4 rocks. Unfortunately, it's not so easy to find reiser4 support these days....

I'm considering maintaining my own kernel line, Ubuntu kernel + reiser4 support.

---

### Post by Xian on 2005-02-15
Reiser FS

---

### Post by DJ_Max on 2005-02-15
ext2, never bothered, or even cared to look at others. It servers it's purposes.

---

### Post by jdong on 2005-02-15
Man, ext2 is quite old and aged now. You might wanna move up to ext3!

---

### Post by DJ_Max on 2005-02-15
[QUOTE=jdong]Man, ext2 is quite old and aged now. You might wanna move up to ext3![/QUOTE]
 Yeah, I really should, when I build my new PC, I'll probably use Reiser FS, seems to be the "new hotness".

---

### Post by topcop on 2005-02-17
my filesystem!
[IMG]http://www.las-vegas-gallery.com/items/26.jpg[/IMG]  :p

---

### Post by Rule on 2005-02-17
[IMG]http://www3.telus.net/ra11le/crap/kerry.jpg[/IMG] 

i'd love to double click her mouse :grin:

---

### Post by KiwiNZ on 2005-02-17
I am slightly confused by this post ?  Can you enlighten me ?

---

### Post by G.I.Josh on 2005-02-17
ext3 for root, XFC for everything else.  No clue why realy, but it works well. :)

---

### Post by Rule on 2005-02-17
[QUOTE=KiwiNZ]I am slightly confused by this post ?  Can you enlighten me ?[/QUOTE]

ummm...how to say...you got a GF or a wife?? :wink:

---

### Post by DJ_Max on 2005-02-17
[QUOTE=topcop]my filesystem!
[IMG]http://web.meganet.net/dickwhitney/BigBird.jpg[/IMG]  :p[/QUOTE]
hrrmm, never heard of that one, nor is it on the list. Is it any good. \\:D/

---

### Post by TravisNewman on 2005-02-17
at the moment I have ext3 for /boot, ext3 for ubuntu, reiser4 for gentoo, ntfs for windows, sun's own format for solaris, and freebsd's own partition format for freebsd. I haven't added all the OS's I'm going to (doing this all over again to write that howto) but I'll probably try out other filesystems for the others, just to see how they perform. I've only ever used reiser3 and ext3 extensively.

---

### Post by DJ_Max on 2005-02-17
[QUOTE=panickedthumb]at the moment I have ext3 for /boot, ext3 for ubuntu, reiser4 for gentoo, ntfs for windows, sun's own format for solaris, and freebsd's own partition format for freebsd. I haven't added all the OS's I'm going to (doing this all over again to write that howto) but I'll probably try out other filesystems for the others, just to see how they perform. I've only ever used reiser3 and ext3 extensively.[/QUOTE]
On that note, i forgot to mention I use [HFS+](http://www.kernelthread.com/mac/osx/arch_fs.html) for OS X. 8)

---

### Post by Lovechild on 2005-02-17
I'm full on Ext3, I found that ReiserFS has poor latency and a tendency to act up every once in a while. I was never fond of XFS or JFS, they never worked quite right for me.

---

### Post by ThePainter on 2005-02-19
Hi,
I havent even heard of some of those in the list.
I dual boot so its NTFS,FATS32 and EXT 3 cos they are the only ones I could make with Partition Magic back in XP.
If some one ever makes a driver for my scanner and an .avi editor that works in linux then it will be EXT 3 all the way  \\:D/

---

### Post by telmo on 2005-02-19
I use ReiserFS for /boot; XFS for filesystem; NTFS for Windows and Fat32 for a shared partition.

---

### Post by reid on 2005-02-21
Reiser
Reiser
Reiser

I like the journaisiling.

---

### Post by morethannoise on 2005-02-21
[FONT=Comic Sans MS]Being extremely new to Linux, I chose the supposed "slower but safer" ext3. Perhaps I'll try the others after getting my feet wet with this one[/FONT].

---

### Post by mimek on 2005-03-29
I've completly moved to reiser4. 
It's great and it's the future.
I hope that there will be reiser4 plugins soon (I'm waiting for that, allowing to compress files "on the fly")

---

### Post by HungSquirrel on 2005-03-29
Reiser3.6.  I'd use Reiser4, but I don't know how to get it done in Ubuntu.  I imagine it'd take a custom kernel to read the filesystems, but what about creating the filesystems?  No clue where to start.  However, when I tried it with Yoper, it was INSANELY fast.

---

### Post by jdong on 2005-03-29
I just had a reiser4 partition die on me -- don't use it.

Actually, ext3 with data=journal is blazingly fast.

---

### Post by jhands on 2005-03-29
what does journaling mean?? :?:  :?:  :cry:

---

### Post by arctic on 2005-03-29
journaling: &#8594; [http://olstrans.sourceforge.net/release/OLS2000-ext3/OLS2000-ext3.html](http://olstrans.sourceforge.net/release/OLS2000-ext3/OLS2000-ext3.html)

i use ext3, as reiserfs still has some flaws like problems with securely locking files on the root system.

---

### Post by bored2k on 2005-03-29
ReiserFS over here .

---

### Post by DJ_Max on 2005-03-29
I now use ext3, since I did a fresh install with Hoary.

---

### Post by wmcbrine on 2005-03-30
[QUOTE=allans]I heard that Ubuntu would sometimes check ext3 filesystems anyway,[/QUOTE]
It's good to have an occasional check, just to be safe. But I do think the default value is set too low (it was at 30 on my new Ubuntu Hoary installation). Anyway, you can check the current value with dumpe2fs, and change it with tune2fs -- set it to 0 to turn it off. (I set mine to 200.)

---

### Post by hard_i on 2005-03-30
did a fresh install of array-7 about a week ago , and choosed Reiserfs instead of ext3 this time.
Searching for files is noticeable faster .. haven't noticed anything else ..yet  ;)

---

### Post by TjaBBe on 2005-03-30
I allways used ReiserFS on Gentoo, but with Ubuntu I have completely moved to ext3. Can't really tell the supposed speed-difference to be honest.

---

### Post by steffen on 2005-03-30
[QUOTE=jdong]Actually, ext3 with data=journal is blazingly fast.[/QUOTE]

Is it safe to add data=journal to my ext3 line in fstab?

Do I need journal=update?

My 'man mount' gives me (on data=journal): >  To use modes other than ordered on  the  root file system, pass the mode to the kernel as boot parameter, e.g. rootflags=data=journal.

---

### Post by lao_V on 2005-03-30
Isn't ext3 already journaled???

---

### Post by arctic on 2005-03-30
[QUOTE=lao_V]Isn't ext3 already journaled???[/QUOTE]
yes, it is and always has been.

---

### Post by defkewl on 2005-03-30
I don't know the main advantages between ext3 and ReiserFS. Where can I get the comparison between these two? All I know that SuSE recommends ReiserFS but I'm currently using ext3.

---

### Post by jdong on 2005-03-30
[QUOTE=steffen]Is it safe to add data=journal to my ext3 line in fstab?

Do I need journal=update?

My 'man mount' gives me (on data=journal):[/QUOTE]

You do NOT need "journal=update" -- that's for converting to the 'new' (which is old ;)) journal format.

data=journal can be directly added to fstab. During the bootup process, the root filesystem is first mounted read-only by the kernel, and then read-write by the bootup process, which will respect options in fstab.

BTW, I'm currently using XFS. I have a nice UPS hooked up to my desktop ;). As long as you don't abuse XFS, it's a hard-working, stable filesystem.

---

### Post by neighborlee on 2005-03-30
[QUOTE=jdong]I heavily use reiserfs and reiser4. I find that:

1. ALL (that's **ALL**) filesystems can be reproducibly corrupted by abrupt shutdowns, etc.

2. Reiserfs is fast.[/QUOTE]
-----------------
do you have any data to back this up ?

cheers
nl
---

---

### Post by neighborlee on 2005-03-30
[QUOTE=topcop]my filesystem!
[IMG]http://www.las-vegas-gallery.com/items/26.jpg[/IMG]  :p[/QUOTE]
---------------
disgusting in a forum.

cheers
nl
---

---

### Post by roachk71 on 2005-09-17
XFS all the way on this HP Pavilion xt125 notebook... Seems to work best on this model in its default configuration (20GB HD, 256MB RAM). ;)

I have about two dozen favorite albums and like ripping to FLAC streams, and XFS handles large files quite well.

---

### Post by angkor on 2005-09-17
ext3 for all partitions, never bothered to try anything else since it doesn't give me any problems. If reiser is a_lot_ faster I'd like to give it a try, but ext3 doesn't feel too slow to me.

---

### Post by papangul on 2005-09-17
Ext2 for boot and Reiserfs for everything else.
Actually I know next to nothing about filesystems, my confusion is compounded by the fact that people give the same same reasons for using either ext3 or reiserfs, but I use reiserfs, since back when I used Gentoo, I noticed that almost all the gentoo geeks use reiserfs.

---

### Post by godzero on 2005-09-17
ext3 for all right now, but looking forward to switching to reiser 4 sometime in the future.
My logic is that reiser was designed for good drives (read: scsi) first, and cheap ata drives had problems durring a power failure that the scsi/reiser combo didn't have.
Reiser has matured allmost enough for me, but not quite.
SATA2 drives + reiser 4 sounds like a good combo.

---

### Post by xequence on 2005-09-17
I use ext3 as it is the default and I dont really have any reason not to. Except it cant be resized for some reason...

---

### Post by papangul on 2005-09-17
[QUOTE=godzero]ext3 for all right now, but looking forward to switching to reiser 4 sometime in the future.
My logic is that reiser was designed for good drives (read: scsi) first, and cheap ata drives had problems durring a power failure that the scsi/reiser combo didn't have.
Reiser has matured allmost enough for me, but not quite.
SATA2 drives + reiser 4 sounds like a good combo.[/QUOTE]
Personally, I have never had any file corruption problems during many power cuts(or mishandling by my family members) with my reiserfs partitions, on non-scsi cheap hdds.
When I used ext2 about 5 years ago, everytime there was a power-cut, linux had to be reinstalled. This is also a reason why I never use ext3 (ext3 has roots in ext2).

---

### Post by mlomker on 2005-09-17
> Reiser has matured allmost enough for me, but not quite.
SATA2 drives + reiser 4 sounds like a good combo


Strange set of comments.  3.x is so stable that they only get a genuine bug every six months or so.  4.x should be solid but it is brand-new.

I've been running reiser on my desktop for quite a while.  We run ext3 on our servers because our vendors 'officially' support it.

---

