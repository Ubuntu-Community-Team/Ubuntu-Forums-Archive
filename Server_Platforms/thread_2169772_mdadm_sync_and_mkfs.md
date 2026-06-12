---
title: "mdadm sync and mkfs"
date: 2013-08-23
forum: Server Platforms
---

### Post by Dreadslayer on 2013-08-23
[SIZE=2][FONT=arial]Hi there

I've created a raid1 with mdadm:

```
**[COLOR=#000000]sudo [/COLOR]****[COLOR=#000000]mdadm --create --verbose /dev/md0 --level=mirror --raid-devices=2 /dev/sda1 /dev/sdb1[/COLOR]**
```

While syncing (which takes quite a while), is it save to run

```
**[COLOR=#000000]sudo mkfs.ext4 /dev/md0[/COLOR]**
```

and start copying data onto it?

Thanks for your answers![/FONT][/SIZE]

---

### Post by chrisguk on 2013-08-23
Assuming you followed this guide then I would imagine that will be fine:

[http://www.howtogeek.com/51873/how-to-setup-software-raid-for-a-simple-file-server-on-ubuntu/](http://www.howtogeek.com/51873/how-to-setup-software-raid-for-a-simple-file-server-on-ubuntu/)

---

### Post by Dreadslayer on 2013-08-23
I used parted instead of fdisk due to its size of 3TB. Apart from that, yes.

---

### Post by SaturnusDJ on 2013-08-24
Yes it's ready. Most of the times there's even a speed limit applied at the sync process, so performance for normal data transfers is reasonable at least.

---

