---
title: "Saucy and F2FS"
date: 2013-05-17
forum: Ubuntu Development Version
---

### Post by vinibali on 2013-05-17
hi,
i was wondering how my Toshiba SSD performs with F2FS byside. so search trough many sites, at that subject and found this: [https://wiki.archlinux.org/index.php/F2fs](https://wiki.archlinux.org/index.php/F2fs). so tried to make the saucy by this tutorial, but as good as i know the saucy(maybe raring too) neednt boot partition, so have no idea how to do this. installing the f2fs-tools with editing the sources.list was easy and made the partition, however the installer cant recognize it.
can someone help? :)

---

### Post by dino99 on 2013-05-17
the 3.8 kernel have builtin f2fs support, but 3.10 is still improving it. Thats said, even if some tools like the latest gparted understand f2fs, some others like ubiquity ignore it right now. So you might need to wait and glance at the coming packages changelogs, to know when real things could be started.

---

### Post by vinibali on 2013-05-17
i saw a preview about the 3.10 speed at phoronix, that was slower. but so the main problem is the ubiquity. i never saw it further, but is there any other text installer for Ubi?

---

### Post by serdotlinecho on 2013-05-17
[http://ubuntuforums.org/showthread.php?t=2137837&page=2&p=12628312#post12628312](http://ubuntuforums.org/showthread.php?t=2137837&page=2&p=12628312#post12628312)

---

### Post by grahammechanical on 2013-05-17
Some of us experimented with Raring and btfs. Not only was a separate boot partition needed but I am of the opinion the Grub cannot read a btfs file system and it may be the same with F2FS. Try a format for the boot partition that you know Grub can read.

Regards.

---

### Post by vinibali on 2013-06-01
im already freaking tired of that shhh windows, so...
as the guy said here: [http://ubuntuforums.org/showthread.php?t=2137837&page=2&p=12628312#post12628312](http://ubuntuforums.org/showthread.php?t=2137837&page=2&p=12628312#post12628312)
#the 2.23 version of libblkid is needed, i fount the github repo: [https://github.com/karelzak/util-linux/tree/master/libblkid](https://github.com/karelzak/util-linux/tree/master/libblkid)
#how can i compile this module?

EDIT:

i downloaded from here: [ftp://ftp.kernel.org/pub/linux/utils/util-linux/v2.23/](ftp://ftp.kernel.org/pub/linux/utils/util-linux/v2.23/) the [util-linux-2.23.1.tar.gz]("ftp://ftp.kernel.org/pub/linux/utils/util-linux/v2.23/util-linux-2.23.1.tar.gz") than build the * libblkid.la * but now i dont know what to do. help me pls :/

---

