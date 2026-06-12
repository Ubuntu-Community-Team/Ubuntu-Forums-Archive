---
title: "Which file system works both in Mac and Ubuntu (for external hard drive) ?"
date: 2010-09-19
forum: The Cafe
---

### Post by legolas_w on 2010-09-19
Hi,

I wan to format my external hard drive a way that both Ubuntu and Mac OS could detect it. 

Any suggestion in addition to FAT because fat32 does not support files larger than 4 GB :(.

Thanks.

---

### Post by Dustin2128 on 2010-09-19
hm..
google shows me that apple's support for file systems other than its own are horrendous, talk about vendor lock in. 
As far as read/write in HFS+, this was all I could find that appeared current:
[http://packages.debian.org/sid/hfsprogs](http://packages.debian.org/sid/hfsprogs)

---

### Post by hessiess on 2010-09-19
According to google, ntfs-3g also supports OSX. Its not ideal but it could be an option. IMO anything is better than FAT, have experienced some quite major data corruptions with this FS.

---

### Post by Bachstelze on 2010-09-19
> **Dustin2128 said:**
> 
google shows me that apple's support for file systems other than its own are horrendous, talk about vendor lock in. 


The kernel is Open Source, if you want support for other FSes, submit patches. Apple is under no obligation to support a filesystem that is used by less than 1% of its users.

@legolas_w: HFS+ shuld be well-supported in Linux. Only the journaling is causing issues (last I checked, a journaled HFS+ required the -force option of mount to be mounter read-write). Make it non-journaled and you should be fine.

---

### Post by sandyd on 2010-09-19
> **legolas_w said:**
> Hi,

I wan to format my external hard drive a way that both Ubuntu and Mac OS could detect it. 

Any suggestion in addition to FAT because fat32 does not support files larger than 4 GB :(.

Thanks.
NTFS
[http://macntfs-3g.blogspot.com/2010/09/ntfs-3g-for-mac-os-x-201088.html](http://macntfs-3g.blogspot.com/2010/09/ntfs-3g-for-mac-os-x-201088.html)

---

### Post by handy on 2010-09-19
I access ext3 using "ExtFS for Mac OS X":

[http://www.paragon-software.com/home/extfs-mac/](http://www.paragon-software.com/home/extfs-mac/)

It is pretty cheap commercial software. I've been using it for well over a year with not a hint of a problem. It is really easy to install setup on OS X, it integrates with the system particularly well.

There is also free software that I think is in beta. Forgotten its name. People who use it say it is great too. Last I looked it was read only on ext4.

It won't take long to find out what it is called if you are interested.

---

### Post by Bachstelze on 2010-09-19
> **sandyd said:**
> NTFS
[http://macntfs-3g.blogspot.com/2010/09/ntfs-3g-for-mac-os-x-201088.html](http://macntfs-3g.blogspot.com/2010/09/ntfs-3g-for-mac-os-x-201088.html)

Yay for no permissions or symlinks!

Seriously, HFS+ and apparently ext3 are supported and are much better choices on a *NIX system than NTFS.

---

### Post by stmiller on 2010-09-19
hfs+ journaling off is fully supported read and write by both.

Format the drive in os x as hfs non-journaled. 

Install the hfs related ubuntu packages.

fuse on os x is a pain IMO and can make your system unstable. ymmv

:)

---

### Post by sandyd on 2010-09-19
> **stmiller said:**
> hfs+ journaling off is fully supported read and write by both.

Format the drive in os x as hfs non-journaled. 

Install the hfs related ubuntu packages.

fuse on os x is a pain IMO and can make your system unstable. ymmv

:)

works on my computer stably. hmm... Ive heard that statement many times before. in this very forum in fact. lol.

---

### Post by handy on 2010-09-20
If you use "ExtFS for Mac OS X" there is no need for reformatting partitions & carrying on; it just recognises any ext2/3/4 file systems & makes them available as though they were HFS+.

To be honest I can't imagine the process of installation & setup being any simpler. You just install it & reboot.

---

