---
title: "LVM basic size / move"
date: 2010-05-14
forum: Server Platforms
---

### Post by xkaliburx on 2010-05-14
ok I have the original install 170GB partition mounted on / 

I need the following;
OS on / 30 GB
data mounted on / data 140GB

Fdisk would have been a joke, but the box was setup via lvm, so I am learning on the fly.  I was able to shrink the partition using;
lvreduce -L 30G /dev/mapper/server-root

vgcreate shows;
VG Size 169/76GiB
Alloc PE / Size 9453 / 36.93GiB
Free PE / Size 34005 / 132.83 GiB

Now, per my DBA, I need that 130 on a seperate 'partition' and I am not 100% sure on the next step.  I am reading on vgcreate, lvcreate, etc. but a little unsure and rather consult the forums for a quick one / two sentence answer.

Thanks

---

### Post by moep on 2010-05-14
```
lvcreate -L 130G -n data server
```

should do what you want, assuming "server" is the name of your volume group and "data" is the name of your new logic volume.

You can alternatively use 

```
lvcreate -l 100%FREE -n data server
```

to fill all remaining space on the volume group with the new logic volume.

PS: Be very careful when shrinking logic volumes that have filesystem on them, terrible things happen when you forget to resize the filesystem first.

---

