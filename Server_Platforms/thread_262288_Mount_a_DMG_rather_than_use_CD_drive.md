---
title: "Mount a DMG rather than use CD drive"
date: 2006-09-21
forum: Server Platforms
---

### Post by riverman on 2006-09-21
I'm running an Ubuntu server on an old Dell box. At the moment, when I apt-get anything, Ubuntu asks me to insert the Ubuntu Server installation disk, which I do. The system gets some data from the CD, some from the net, and installs whatever it is I'm installing no problem. Right now I've taken to just leaving the disk in the drive so it's there when I need it.

My questions:

1) Is there a way to work round this by mounting a dmg and directing apt-get to that, rather than the CD drive (so I can keep the CD drive empty).

2) Failing that, could I 'encourage' apt-get to go online for the info it's currently getting from the CD (again, freeing up the CD drive).

Thanks all!

---

### Post by spp on 2006-09-22
Remove the CD from the repository list either via synaptic OR by commenting them out in /etc/apt/sources.list

It will then go online for all updates.

SP

Edit: It *is* possible to mount an iso image file as a device. To do so...

```

sudo mkdir /mnt/iso

sudo mount <name of iso file> /mnt/iso/ -t iso9660 -o loop,ro


```

However, I usually just go online :)

---

