---
title: "Adding LVM and a new drive"
date: 2008-06-01
forum: Server Platforms
---

### Post by keymoo on 2008-06-01
Hi there,

My home Ubuntu Server 8.04 has filled up. It is currently configured:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              72G  2.5G   66G   4% /
/dev/sda1             466G  466G   48M 100% /var/lib/backuppc

```sdb is an 80Gb drive
sda is a 500Gb drive

My plan is to buy another 500Gb drive and create a logical volume called /var/lib/backuppc and copy the existing  /var/lib/backuppc to it. I then intend to reformat the sda1 device and extend the LVM onto this device to give 1TB storage.

Does this sound like the right way to do it? I may even use the sdb drive and repartition some of that and add it to the LVM group. I just wondered what you thought.

Thanks

---

### Post by nix4me on 2008-06-01
Yes.  That is exactly how i would do it also.

---

