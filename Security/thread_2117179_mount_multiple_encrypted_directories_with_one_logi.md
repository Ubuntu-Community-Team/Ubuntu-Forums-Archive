---
title: "mount multiple encrypted directories with one login"
date: 2013-02-17
forum: Security
---

### Post by monkblah on 2013-02-17
Hi--hope someone can help me with this. I have ubuntu 12.10 installed. Have an ecryptfs-encrypted home directory. So when I login, my home directory gets automatically ecryptfs-mounted. This is fine.

However, I also have several other partitions, some on different disks. I would also like to encrypt them, and have them also automatically ecryptfs-mounted when I login.

Is this possible to achieve? Any help appreciated!

---

### Post by monkblah on 2013-02-17
Hi--hope someone can help me with this. I have ubuntu 12.10 installed. Have an ecryptfs-encrypted home directory. So when I login, my home directory gets automatically ecryptfs-mounted. This is fine.

However, I also have several other partitions, some on different disks. I would also like to encrypt them, and have them also automatically ecryptfs-mounted when I login.

Is this possible to achieve? Any help appreciated!

---

### Post by cariboo on 2013-02-17
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by bodhi.zazen on 2013-02-18
IMO it is best to use LUKS for what you want.

See [http://ubuntuforums.org/showthread.php?t=1472396](http://ubuntuforums.org/showthread.php?t=1472396)

---

### Post by monkblah on 2013-02-19
> **bodhi.zazen said:**
> IMO it is best to use LUKS for what you want.

See [http://ubuntuforums.org/showthread.php?t=1472396](http://ubuntuforums.org/showthread.php?t=1472396)

Possibly you are right. I am open to the possibility of using LUKS if it will work better for this purpose. Can you please explain how?

I would certainly agree with you that the workaround in thread you linked to is not a good one.

---

### Post by bodhi.zazen on 2013-02-19
With LUKS you make a crypt, then you use LVM within the crypt.

You would mount it automatically at boot or script it at log in.

---

