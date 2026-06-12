---
title: "Fresh Ubuntu installation with TrueCrypt with hidden volume"
date: 2012-08-11
forum: Security
---

### Post by fathburt on 2012-08-11
What is the best way to do this? I know TrueCrypt isn't included with Ubuntu because of liscencing reasons. 

First step is almost certainly: do an install of Ubuntu with encrypted install + automatic partitioning, etc.

Then what? If you only have one hard drive, how do you proceed? Resize the ext4 partition and create free space? Then you have to create the visible volume and the hidden volume in that free space?

Is there some way to do an install with TrueCrypt with hidden out of the box?

---

### Post by Hungry Man on 2012-08-12
Why not simply create a hidden container in a file?

---

### Post by Soul-Sing on 2012-08-12
> **fathburt said:**
> What is the best way to do this? I know TrueCrypt isn't included with Ubuntu because of liscencing reasons. 

First step is almost certainly: do an install of Ubuntu with encrypted install + automatic partitioning, etc.

Then what? If you only have one hard drive, how do you proceed? Resize the ext4 partition and create free space? Then you have to create the visible volume and the hidden volume in that free space?

Is there some way to do an install with TrueCrypt with hidden out of the box?

Do you mean an installation of Ubuntu via the alternate cd? It is possible to encrypt Ubuntu with the alernate install cd.
(Not only the your <home>)
Why creating an additional partition, which is possible via the Gparted cd, if your op system is encrypted? But it is possible, and again I would recommand using the Gparted cd.
This new partition could be transformed into a hidden volume, using Truecrypt.

---

### Post by HermanAB on 2012-08-15
You could use Realcrypt.

---

### Post by rookcifer on 2012-08-17
> **fathburt said:**
> Is there some way to do an install with TrueCrypt with hidden out of the box?

No.  Truecrypt does not support FDE for Linux.  You can only create containers.

---

