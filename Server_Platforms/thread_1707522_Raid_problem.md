---
title: "Raid problem"
date: 2011-03-15
forum: Server Platforms
---

### Post by 8Kuula on 2011-03-15
So I did decide make mdadm raid1 from my system disk, all went ok at that part.
/dev/md0 /
/dev/md1 swap
/dev/md2 /home

Problem is that I had existing raid5, mdadm one too.
So before I started to make raid1 I just removed cables from raid5 disks, and now when I connect them back mdadm (I asume) thinks that raid5 is /dev/md0 whitch is my raid1 boot partition that I created, so system wont boot up.

So how I can change that raid5 becomes /dev/md3?

<edit>
OS: Ubuntu Server 10.02.2
</edit>

---

### Post by rubylaser on 2011-03-15
You need to update your /etc/mdadm/mdadm.conf file to file the arrays in the proper order. Here's an example...
```
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=72d23d35:35d103e3:01b5209e:be9ff10a
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=a50c4299:9e19f9e4:01b5209e:be9ff10a
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=99fee3a5:ae381162:01b5209e:be9ff10a
ARRAY /dev/md3 level=raid5 num-devices=4 UUID=99fee3a5:ae381162:01b5209e:be9ff85b
```

You can get this by doing something like this...
```
cp /etc/mdadm/mdadm.conf /etc/mdadm/mdadm.conf.old
mdadm --examine --scan >> /etc/mdadm/mdadm.conf
```

---

### Post by 8Kuula on 2011-03-16
Yep, that and after that
update-initramfs -u

And bang, it did came up :)
Thanks, solved.

---

### Post by rubylaser on 2011-03-16
Glad to hear you got it working properly.

---

