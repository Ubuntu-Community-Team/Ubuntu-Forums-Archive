---
title: "Virtial Disk Image"
date: 2012-08-13
forum: Virtualisation
---

### Post by amin021023 on 2012-08-13
Hi all

I want to put some files into a V disk image...

so I creat one by this command:
```
qemu-img create virtdisc.img
```

**but how to put my files into it?**

---

### Post by amin021023 on 2012-08-13
no idea?

---

### Post by howefield on 2012-08-14
Thread moved to the "*Virtualization*" forum.

---

### Post by slooksterpsv on 2012-08-14
You'll need to format the img as some type of a file system (how you do that, the only way is through an OS via qemu). If you're looking for virtual volume images look into truecrypt.

---

### Post by Dedoimedo on 2012-08-16
You will need to create a partition table.
And then create filesystems on it.
You can do this inside a virtual machine.

And later, from the host, partx can mount virtual disks as loopback images:
[http://linux.die.net/man/8/partx](http://linux.die.net/man/8/partx)

Dedoimedo

---

