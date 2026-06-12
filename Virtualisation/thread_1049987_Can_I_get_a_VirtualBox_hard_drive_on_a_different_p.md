---
title: "Can I get a VirtualBox hard drive on a different partition other than the file system"
date: 2009-01-25
forum: Virtualisation
---

### Post by Fionnzer on 2009-01-25
Can I get a VirtualBox hard drive on a different partition other than the file system (where ive installed Ubuntu)
It just doesnt show up when I try to make a harddrive it only shows the file system

---

### Post by sanderj on 2009-01-25
> **Fionnzer said:**
> Can I get a VirtualBox hard drive on a different partition other than the file system (where ive installed Ubuntu)

Yes, you can; I've done that myself.
> **Fionnzer said:**
> 
It just doesnt show up when I try to make a harddrive it only shows the file system
Well, that's good: in the file system (/) you can see the *mounted* other partitions.

So: have you *mounted* the partition where you want to create the VirtualBox hard drive? You can mount under /mnt or /media, for example.

---

### Post by Fionnzer on 2009-01-25
> **sanderj said:**
> Yes, you can; I've done that myself.

Well, that's good: in the file system (/) you can see the *mounted* other partitions.

So: have you *mounted* the partition where you want to create the VirtualBox hard drive? You can mount under /mnt or /media, for example.

Thanks so much mate ;)

---

