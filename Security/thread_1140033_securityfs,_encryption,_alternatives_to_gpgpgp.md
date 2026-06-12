---
title: "securityfs, encryption, alternatives to gpg/pgp"
date: 2009-04-27
forum: Security
---

### Post by Th3Professor on 2009-04-27
[SIZE=1][/SIZE]I tried setting up an encryption type file system (or maybe it was just a folder in /home), yet it doesn't appear to be working. I believe it's mounted as "securityfs".

How do I set that up correctly? 

(I use gpg, it's great... would like to use that application that allows an entire directory and its files to be more secure, hopefully encrypted, in a way other than gpg/pgp.)

Thanks! :)

---

### Post by nunki on 2009-04-27
I believe you're looking for ecryptfs
```

sudo apt-get install ecryptfs-utils
ecryptfs-setup-private

```
Now there should be a folder in your home directory called Private that gets automounted when you log in. Anything you place in there will be encrypted and the folder is unmounted at logout.

---

### Post by Th3Professor on 2009-04-28
> **nunki said:**
> I believe you're looking for ecryptfs
```

sudo apt-get install ecryptfs-utils
ecryptfs-setup-private

```Now there should be a folder in your home directory called Private that gets automounted when you log in. Anything you place in there will be encrypted and the folder is unmounted at logout.

Okay, looks like I already had it... just a little confused on how to use it.

...I tried a --force (unmounting it) and remount... well, hmm... how do I test trying to penetrate it?

---

### Post by nunki on 2009-04-28
I believe there is
```

ecryptfs-umount-private

```
and 
```

ecryptfs-mount-private

```

---

### Post by Th3Professor on 2009-05-01
is there any more in-depth documentation or HOWTOs out there anywhere on this?

---

### Post by tubbygweilo on 2009-05-01
Th3Professor,
A quick look through [EncryptedPrivateDirectory]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") may give you a few ideas and a few hints of other places to visit in your search for knowledge.

---

