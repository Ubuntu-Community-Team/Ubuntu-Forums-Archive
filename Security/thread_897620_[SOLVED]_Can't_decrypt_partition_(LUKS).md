---
title: "[SOLVED] Can't decrypt partition (LUKS)"
date: 2008-08-22
forum: Security
---

### Post by psie on 2008-08-22
Hey,

I had some trouble with my laptop, yesterday, see here: [http://ubuntuforums.org/showthread.php?t=897483](http://ubuntuforums.org/showthread.php?t=897483) 
Now I booted from a Live-CD and trying to mount my partition. The issue is that if I am trying to decrypt the partition...
```
sudo cyptsetup luksOpen /dev/hda3 hda3
``` 
...it asks me 3 times for my password and then tells me: Command failed: No key available with this passphrase
I am definitely using the right passphrase and have no clue what am I doing wrong... Thanks for help!

---

### Post by psie on 2008-08-22
Ok, I wasn't paying attention that my keyboard was switched from a german version to a us one, so y and z were swapped....

---

