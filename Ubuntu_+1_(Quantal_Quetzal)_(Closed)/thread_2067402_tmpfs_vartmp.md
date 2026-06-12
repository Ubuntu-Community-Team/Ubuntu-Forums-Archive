---
title: "tmpfs /var/tmp?"
date: 2012-10-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Yahoé on 2012-10-06
I've implemented tmpfs on my Quantal setup, but I have a question about /var/tmp.
Most SSD optimization pages recommend something lilke:
tmpfs  /var/tmp tmpfs  defaults,noatime,mode=1777,size=10% 0    0
However, the archlinux wiki says: "Do NOT use it on [/var/tmp]("http://www.pathname.com/fhs/2.2/fhs-5.15.html"), because that folder is meant for temporary files that are preserved across reboots."
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

Could a savvy forum member please clarify if yes or no I should have it in tmpfs for a SSD setup,

---

### Post by cariboo on 2012-10-06
[This]("http://linuxers.org/article/differences-between-tmp-and-vartmp") should clarify things for you.

---

### Post by Paddy Landau on 2012-10-06
/var/tmp is intended to hold "temporary" files across boots.

There is supposed to be an automatic process to clear out old files regularly.

I do not know what effect there would be if you were to put it on temps; but, presumably, some programs would lose their state.

---

### Post by Yahoé on 2012-10-09
Thanks guys, it all confirms that /var/tmp should not be in tmpfs.

---

### Post by zika on 2012-10-09
> **Yahoé said:**
> Thanks guys, it all confirms that /var/tmp should not be in tmpfs.I've kept it for year+ in tmpfs and did not encounter any ill effect... So, it is kinda inconclusive...
```
tmpfs        /tmp           tmpfs    defaults,noatime    0    0
tmpfs        /var/run       tmpfs    defaults,noatime    0    0
tmpfs        /var/lock      tmpfs    defaults,noatime    0    0
tmpfs        /var/log       tmpfs    defaults,noatime    0    0
tmpfs        /var/run       tmpfs    defaults,noatime    0    0
tmpfs        /var/mail      tmpfs    defaults,noatime    0    0
tmpfs        /var/spool     tmpfs    defaults,noatime    0    0
tmpfs        /var/tmp       tmpfs    defaults,noatime    0    0
tmpfs        /var/cache     tmpfs    defaults,noatime    0    0
```
P.S. The only caveat is that this way /tmp could get filled... But, a bit of care and that is also non-problem... ;)

---

### Post by Paddy Landau on 2012-10-09
I think zika has given you the answer. You do not need [FONT=Lucida Console]/var/tmp[/FONT] to be on your SSD; it just makes it a bit easier for a few applications to maintain state. If you have the RAM, why not try it in [FONT=Lucida Console]tmpfs[/FONT]?

But I wouldn't put [FONT=Lucida Console]/tmp[/FONT] in [FONT=Lucida Console]tmpfs[/FONT], because when working on large files (for example when I record and edit videos and audio), there wouldn't be sufficient space.

---

### Post by funicorn on 2012-10-09
Archlinux is different. If you just want to make an easy tmpfs, you can mount it to /tmp.

---

### Post by zika on 2012-10-09
> **Paddy Landau said:**
> But I wouldn't put [FONT=Lucida Console]/tmp[/FONT] in [FONT=Lucida Console]tmpfs[/FONT], because when working on large files (for example when I record and edit videos and audio), there wouldn't be sufficient space.Totally true. I emphasized that this only my experience and that I'm able to contain my needs for /tmp accordingly within my RAM... Even in the case that You mention I think there might be a way to redirect (temporary and output) files (only) from those applications in a folder that resides on HDD and thus prevent any problem. I know I did... ;)

[http://ubuntuforums.org/showpost.php?p=12286346&postcount=3](http://ubuntuforums.org/showpost.php?p=12286346&postcount=3) reminded me that putting /var/cache in tmpfs might be a bad idea. I'll investigate more. This thread made me open tmpfs again and it seems that I should have read my notes before that... There was one reinstall in the meantime  at the end of testing 12.04... and...
Update: Yes, it seems that putting /var/cache in tmpfs produced error in [http://ubuntuforums.org/showpost.php?p=12286346&postcount=3](http://ubuntuforums.org/showpost.php?p=12286346&postcount=3) . Mea culpa...

---

### Post by Paddy Landau on 2012-10-10
> **zika said:**
> … there might be a way to redirect (temporary and output) files (only) from those applications in a folder that resides on HDD…
Indeed, some applications provide that option. Not all do so, though; and, especially in the case of a shared computer, this could cause confusion and errors.

There is a way to "combine" two folders into a single one, thus make [FONT=Lucida Console]/tmp[/FONT] in [FONT=Lucida Console]tmpfs[/FONT] with an overflow on the HDD or SSD, using [FONT=Lucida Console]unionfs[/FONT] (the mount-point version seems to be unavailable on Ubuntu, but you can install and use [[FONT=Lucida Console]unionfs-fuse[/FONT]]("apt:unionfs-fuse")). I have not tested this thoroughly, though, so I do not know the restrictions and caveats.

> **zika said:**
> Update: Yes, it seems that putting /var/cache in tmpfs produced error in [http://ubuntuforums.org/showpost.php?p=12286346&postcount=3](http://ubuntuforums.org/showpost.php?p=12286346&postcount=3) .
Thanks for that update.

---

### Post by Paddy Landau on 2012-10-10
New discovery:

Making [FONT=Lucida Console]/var/cache[/FONT] transient disables the Ubuntu Software Centre, which fails with an error. (I now have to fix this.)

Therefore, leave [FONT=Lucida Console]/var/cache[/FONT] on the HDD or SSD!

---

### Post by Yahoé on 2012-10-11
The filesystem hierarchy standard is very clear about this:

[http://refspecs.linuxfoundation.org/FHS_2.3/fhs-2.3.html#VARTMPTEMPORARYFILESPRESERVEDBETWEE](http://refspecs.linuxfoundation.org/FHS_2.3/fhs-2.3.html#VARTMPTEMPORARYFILESPRESERVEDBETWEE)

---

### Post by Yahoé on 2012-10-11
Still, it's not meant to be.
Moreover /var/run and /var/lock are already redirected to tmpfs by default, so placing them in fstab is redundant.

---

### Post by Paddy Landau on 2012-10-11
> **Yahoé said:**
> The filesystem hierarchy standard is very clear about this…
Thank you for the link to the standards.

> **Yahoé said:**
> … /var/run and /var/lock are already redirected to tmpfs
I am curious as to why [FONT=Lucida Console]/run/lock[/FONT] and [FONT=Lucida Console]/run/shm[/FONT] are set up as [FONT=Lucida Console]tmpfs[/FONT] when [FONT=Lucida Console]/run[/FONT] already is [FONT=Lucida Console]tmpfs[/FONT]? It seems redundant.

---

### Post by Yahoé on 2012-10-17
> **Paddy Landau said:**
> Thank you for the link to the standards.


I am curious as to why [FONT=Lucida Console]/run/lock[/FONT] and [FONT=Lucida Console]/run/shm[/FONT] are set up as [FONT=Lucida Console]tmpfs[/FONT] when [FONT=Lucida Console]/run[/FONT] already is [FONT=Lucida Console]tmpfs[/FONT]? It seems redundant.

My point exactly.

---

