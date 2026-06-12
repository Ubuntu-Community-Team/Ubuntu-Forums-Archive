---
title: "Can not encrypt swap"
date: 2012-06-01
forum: Security
---

### Post by bustard on 2012-06-01
I tried to set up 11.10 using the alternate install cd.

There was no problem making partitions for / and /home and encrypting them, but when it came to the swap partition, there was only one place to specify it was swap, and that was the same place I needed to specify it was to be encrypted. 

There is no mount point for swap, just the 'use as...', and the 'use as...' is also the place I have to tell it to make an encrypted file.

I have tried this 3 times but do not see what I am doing wrong.

Any suggestions?

Thanks

---

### Post by codemaniac on 2012-06-01
You might need the ecryptfs-utils package.
```
sudo ecryptfs-setup-swap
```

---

### Post by bustard on 2012-06-01
I got it installed by not trying to specify the mount point until everything else was done - passwords and so on. Initially, you just tell it to 'use as...encrypted'.

Then you go back and click on each partition and specify the 'use as swap' in the case of the swap file, and the '/' mount point for the root partition.

As it turned out, I could not use it anyway because clonezilla, which I use to make an image of the system every week or so, can not handle encrypted files very well, and uses 'dd' which is very slow it looks like.

---

