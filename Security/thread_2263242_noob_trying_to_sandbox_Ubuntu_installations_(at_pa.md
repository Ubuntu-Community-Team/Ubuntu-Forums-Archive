---
title: "noob trying to sandbox Ubuntu installations (at partition layer)"
date: 2015-01-30
forum: Security
---

### Post by haplorrhine on 2015-01-30
My old Ubuntu partition automatically mounts the other Ubuntu partition with unmediated read-write access.  I wanted the partition table to act as an impenetrable sandbox enforcing complete isolation!

```
sudo fdisk -l

[...]

   Device Boot      Start      End           Blocks     Id      System
/dev/sda1   *      2048      390627047    195312500    83         Linux
/dev/sda2       390627326    429688831    19530753      5     Extended
Partition 2 does not start on a physical sector boundary
/dev/sda3       429688832   917970943     244141056    83         Linux
/dev/sda4       917970944   927735807      4992432     83         Linux
/dev/sda5       390627328   429688831      19530752    82       Linux swap / Solaris



```

One of those should have been a logical partition for /tmp, but I might have accidentally made it a logical partition on its own primary (not extended) partition.  I really don't know.  :rolleyes:

---

### Post by TheFu on 2015-01-30
No such thing as "impenetrable sandbox enforcing complete isolation!" when a device is physically connected. If you don't want it mounted, do not put the partition into the machine.

However, you could just remove the partition you don't want mounted from the /etc/fstab. That is usually good enough for most people.

I don't understand the rest of the post. Sorry.

---

### Post by bashiergui on 2015-01-31
If you want each partition to be unmountable by the other then encrypt each one separately. Then the only way to mount it would be to know the password to decrypt.

---

### Post by haplorrhine on 2015-02-03
But then don't I have to trust the human not to mix up passwords, or else withhold the other password? I guess I could do encryption alongside strict mount flags.  Should mounting option changes be made to /etc/mtab or /proc/mounts?  Can these options be set indepently for each Linux partition?

---

### Post by TheFu on 2015-02-03
> **haplorrhine said:**
> But then don't I have to trust the human not to mix up passwords, or else withhold the other password? I guess I could do encryption alongside strict mount flags.  Should mounting option changes be made to /etc/mtab or /proc/mounts?  Can these options be set indepently for each Linux partition?

I don't think it is safe to touch either of those files.

---

### Post by bashiergui on 2015-02-03
> **haplorrhine said:**
> But then don't I have to trust the human not to mix up passwords, or else withhold the other password?If you don't want users to access the other partition then don't give them the password. If they have both passwords then there would be no point.

---

### Post by haplorrhine on 2015-02-17
> **bashiergui said:**
> If you don't want users to access the other partition then don't give them the password. If they have both passwords then there would be no point.

What if it's an intruder?

-

I'll tinker with the files whether you want me to or not, so you might as well give me advice.

---

### Post by bashiergui on 2015-02-17
> What if it's an intruder?Assuming you pick passwords that don't suck, he'd have to crack LUKS which hasn't been done yet. Use a long complex password and it will be more than sufficient. Why don't you trust disk encryption?

You're over thinking this. With strong encryption the mount flags would be superfluous. If your adversary is able to crack LUKS then he's sophisticated enough to overcome a few flags anyway.

If you have that little trust in the users you let use your computer then don't let them use it. Or get a separate computer for them.

---

