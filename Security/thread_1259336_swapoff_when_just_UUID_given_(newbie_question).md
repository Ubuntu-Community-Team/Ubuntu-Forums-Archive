---
title: "swapoff when just UUID given (newbie question)"
date: 2009-09-06
forum: Security
---

### Post by js31 on 2009-09-06
hello,

I hope this is the right place to post this. wanted to encrypt my swap drive of 2GB as described, here:
[http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu](http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu)
(or [https://wiki.ubuntu.com/EncryptedFilesystemHowto3](https://wiki.ubuntu.com/EncryptedFilesystemHowto3))

problem is, despite I knew it, the use of UUIDs. I could find only information about the advantages, but not practical handling for the command line. how to address the drive in order to properly turn off the swap, wipe it clean, then apply the encryption and enable with swapon.

in case needed, here's what I found out:

```

-> /etc/fstab
# swap was on /dev/sda5 during installation
UUID=5d08de78-827f-44c1-bfaf-58cb6720f41c  none  swap  sw  0  0

-> free
Swap:      2104472     184872    1919600

-> blkid
/dev/sda5: UUID="5d08de78-827f-44c1-bfaf-58cb6720f41c" TYPE="swap"
```

thanks in advance
J.

---

### Post by bodhi.zazen on 2009-09-06
the first link you gave takes you through it step by step. You may refer to your swap partition as /dev/sda5 (rather then UUID),

You can turn swap off with :

```
sudo swapoff -a
```

encrypt the partition (/dev/sda5) and edit /etc/fstab

You should be good to go

```
sudo swapon -a
```

---

### Post by js31 on 2009-09-06
thank you :)
I kind of felt I'd have to specify the drive in the swapoff/-on command, perhaps therefore my confusion

only problem left, I get this error message; is it just something to ignore, or does it mean swap is not turned off?

[HTML]swapoff: /dev/sda5: Cannot allocate memory[/HTML]

---

