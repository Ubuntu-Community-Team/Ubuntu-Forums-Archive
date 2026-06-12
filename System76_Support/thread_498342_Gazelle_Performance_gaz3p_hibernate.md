---
title: "Gazelle Performance gaz3p hibernate"
date: 2007-07-11
forum: System76 Support
---

### Post by voidmage on 2007-07-11
When I try to hibernate, it gives this error:
```

[40179.892000] swsusp: free swap pages: 103243
[40179.892000] swsusp: Not enough free swap

```

I have 2GB of ram and a (factory setting) swap partition of 1GB. I added a 1GB swap file to bring the swap total up to 2GB. Does hibernate only use swap partition space, and if so, how can I add more swap without requiring a reinstall or a reformat?

---

### Post by thomasaaron on 2007-07-11
Could you please post the results of:
```
swapon -s
```

---

### Post by voidmage on 2007-07-11
Filename                                Type            Size    Used    Priority
/dev/mapper/ubuntu-swap_1               partition       1032184 68844   -1
/mnt/1GB.swap                           file            1064952 0       -3

---

### Post by thomasaaron on 2007-07-11
I'm not exactly sure, but Gazelles are now hibernating much better than they did.
I think activating that swap file must have thrown it off.

Can you disable it (I think with swapoff) and see if you can hibernate?

There are tools for adjusting LVM partitions.
I need to figure out what they are because LVM partitioning has made hibernation better and dual booting more difficult.

---

### Post by voidmage on 2007-07-11
It did hibernate successfully, but (probably because of compiz) X did not give me my desktop back (just a black screen). After restarting X, I could not get wireless to work.

---

