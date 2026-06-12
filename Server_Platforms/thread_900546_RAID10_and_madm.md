---
title: "RAID10 and madm"
date: 2008-08-25
forum: Server Platforms
---

### Post by TheGameAh on 2008-08-25
Had trouble finding any solid info on this, at least on RAID10.

Say you have a 4 disk RAID 10 setup.  Down the road, you want to add 2 more disks.  Is it possible to use the grow option in mdadm to just expand the array?

---

### Post by fjgaude on 2008-08-25
I think so. But first in **mdadm**, you simply add the two drives as spares, and then add them into the raid10 array. I've never done such a thing but I'm sure it works if you do everything just right, i.e., correctly.

---

### Post by TheGameAh on 2008-08-26
Can anyone else chime in?

---

### Post by nhbubba on 2008-11-07
I believe the answer to this is a resounding no!

[http://www.mail-archive.com/linux-raid@vger.kernel.org/msg08796.html](http://www.mail-archive.com/linux-raid@vger.kernel.org/msg08796.html)

> The man page for mdadm does not mention it because it is not
supported.

There are several reshape options that I would like to implement
including

...

  - raid10 growing and layout change

Of course there are creative ways of doing such a thing. [Here]("http://www.linuxquestions.org/questions/linux-server-73/convert-raid-1-system-into-raid-10-557471/") is a description of how to grow a 2-volume RAID1 set into a 4-volume RAID10 set. I have successfully done such a thing.

It is extra easy if you float LVM volumes on top of your RAID sets. This means you don't have to go copying files between volumes, you simply do a pvcreate->vgextend->pvmove->pvremove and LVM nicely migrates the data for you.

---

