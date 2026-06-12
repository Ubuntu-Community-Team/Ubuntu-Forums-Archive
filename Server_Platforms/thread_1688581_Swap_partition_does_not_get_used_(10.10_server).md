---
title: "Swap partition does not get used (10.10 server)"
date: 2011-02-15
forum: Server Platforms
---

### Post by clevershark on 2011-02-15
After unsuccessfully trying to install Oracle Express I find that for some reason the swap partition on my server disk does not get used. 

My setup: 10.10 server x64 on an intel server with two 500gb HDs in a mirror array

This is puzzling, because I definitely created a swap partition for this system and indeed if I look at /etc/fstab I actually have two swap partitions, one on /dev/mapper/[some long raid name]_ar05 and one on /dev/mapper/cryptswap1, but AFAIK this is normal with 10.10.

"swapon -a" fails with this message:

```
swapon: /dev/mapper/[raid name]_ar05: read swap header failed: Invalid argument
swapon: /dev/mapper/cryptswap1: stat failed: No such file or directory
```

there's always the option of using a file on the server's filesystem, but I want to see if this can be fixed. I only have remote access to server via SSH, which makes startup troubleshooting pretty impossible.

I have a local server at home also using 10.10 server 64-bit with an encrypted swap file running on a RAID array, but it does not have this problem.

Any ideas?..

---

### Post by clevershark on 2011-02-15
After running mkswap on the non-encrypted swap partition the problem appears to have resolved itself.

---

