---
title: "lvm using the wrong device"
date: 2008-10-11
forum: Server Platforms
---

### Post by promodus on 2008-10-11
lvm keeps taking the wrong device!


```
root@storage1:~# pvs
```

So nothing is there, now:
```
root@storage1:~# pvcreate /dev/drbd0
  Physical volume "/dev/drbd0" successfully created
```

Ok then, so that would be awesome if it was to use /dev/drbd0 but...

```
root@storage1:~# pvs
  Found duplicate PV dwbVb79bSb9Y3B28F3eeK0IQz5eoSPsa: using /dev/sdb not /dev/drbd0
  PV         VG   Fmt  Attr PSize  PFree 
  /dev/sdb        lvm2 --   32.00G 32.00G
```

This is not what I want.
However, If I change /etc/lvm/lvm.conf to use a seperate /dev directory, maybe /dev2 and I put drbd0 there it works:

```
root@storage1:~# pvcreate /dev/drbd0
  Physical volume "drbd0" successfully created
```

Lets make sure...
```
root@storage1:~# pvs
  PV          VG   Fmt  Attr PSize  PFree 
  /dev2/drbd0      lvm2 --   32.00G 32.00G
```

I see there are filters within /etc/lvm/lvm.conf but none of them are working. 

Any ideas?

Thanks in advance.

---

