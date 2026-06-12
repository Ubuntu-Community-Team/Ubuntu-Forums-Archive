---
title: "Error when trying to patch grsec"
date: 2008-05-28
forum: Security
---

### Post by borkborkbork on 2008-05-28
I am trying to patch grsec to the linux kernel

I downloaded the latest kernel (2.6.25.4) with the latest grsecurity patch (2.1.11-2.4.36.2) and when I enter the command:

patch -p0 <./grsecurity-2.1.11-2.4.36.2-200804211830.patch

I get this error message:

```

root@prime:/home# patch -p0 < ./grsecurity-2.1.11-2.4.36.2-200804211830.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -urNp linux-2.4.36.2/arch/alpha/config.in linux-2.4.36.2/arch/alpha/config.in
|--- linux-2.4.36.2/arch/alpha/config.in	2008-02-24 15:38:03.000000000 -0500
|+++ linux-2.4.36.2/arch/alpha/config.in	2008-03-11 14:12:45.000000000 -0400
--------------------------
File to patch: 

```

What do I do?

---

### Post by borkborkbork on 2008-05-28
Please, I need some help.

---

### Post by /etc/init.d/ on 2008-05-29
You have downloaded the wrong patch.  The patch you have is for Linux 2.4.36.2, but you have 2.6.25.4.

Download the latest grsecurity patch from here:

[http://www.grsecurity.net/test/grsecurity-2.1.12-2.6.25.4-200805181334.patch](http://www.grsecurity.net/test/grsecurity-2.1.12-2.6.25.4-200805181334.patch)

Then patch it with this command:

```
patch -p0 < grsecurity-2.1.12-2.6.25.4-200805181334.patch	
```

Remember you need to have unzipped the kernel source code, and have the patch in the parent directory.  For example, if you unzip the kernel to your home directory, you'll have a directory called "/home/<username>/linux-2.6.25.4".   In this case you'll need to put the patch into "/home/<username>/".

Also, the GRsecurity documentation is worse than useless.  Take a look at [http://www.tuxmachines.org/node/8676](http://www.tuxmachines.org/node/8676) -- this is much more helpful.

---

