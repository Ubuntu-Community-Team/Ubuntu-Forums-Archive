---
title: "silly fstab error"
date: 2010-02-05
forum: System76 Support
---

### Post by amasiar on 2010-02-05
Dear System76,
Why am I getting silly fstab error when I boot up my computer? Something about mounting the swap file. I took a peek at the fstab file to no avail. Hitting Esc makes it go away but naaaaaaag :)

It's all stock (with encrypted home partition)

---

### Post by thomasaaron on 2010-02-05
I'm seeing more of those errors lately, but I'm not sure what is causing them. Please try running fsck on your system from a live CD to see if that fixes it. Here are instructions...

> To run fsck, first boot from a live CD. Once you are booted, to to System > Administration > Partition Editor. This will show you your current partiton layout and the designations of your partition. For example, your partitions may be /dev/sda1, /dev/sda5, and /dev/sda7. Whatever the designations, make note of them. 

Then open a terminal (Applications > Accessories > Terminal) and run fsck as follows (only use your own partition designations)...

sudo fsck /dev/sda1
sudo fsck /dev/sda5
sudo fsck /dev/sda7

fsck will examine your filesystems and try to repair any damage. Occasionally, filesystems get too broken for fsck to fix them. In this is the case, it may be necessary to put a fresh image on your machine.

It could also mean that you have a faulty hard drive. However, this is pretty rare, and it is better to try re-imaging the machine first.

---

### Post by jdb on 2010-02-05
> **amasiar said:**
> Dear System76,
Why am I getting silly fstab error when I boot up my computer? Something about mounting the swap file. I took a peek at the fstab file to no avail. Hitting Esc makes it go away but naaaaaaag :)

It's all stock (with encrypted home partition)

Check your fstab for multiple swap entries.
There might be an old one with a bogus UUID.

jdb

---

### Post by thomasaaron on 2010-02-05
Good point. Could you post the output of...

cat /etc/fstab

---

### Post by amasiar on 2010-02-05
I think I want my swap turned off, no? After all, unless the swap is encrypted as well, I wouldn't want my key on the swap partition, it would make it pointless to encrypt the home directory :o

Here's the last line of my fstab:
/dev/mapper/cryptswap1 none swap sw 0 0

[http://ubuntuforums.org/showthread.php?p=8166845](http://ubuntuforums.org/showthread.php?p=8166845)

> Don't do anything, don't press any keys, just let it continue to boot.

It doesn't get mounted until you logon, so therefore it's just giving you a warning saying it can't be mounted yet.

---

### Post by jdb on 2010-02-05
> **amasiar said:**
> I think I want my swap turned off, no? After all, unless the swap is encrypted as well, I wouldn't want my key on the swap partition, it would make it pointless to encrypt the home directory :o

Here's the last line of my fstab:
/dev/mapper/cryptswap1 none swap sw 0 0

[http://ubuntuforums.org/showthread.php?p=8166845](http://ubuntuforums.org/showthread.php?p=8166845)

The swap is encrypted, dm-crypt created /dev/mapper/cryptswap1 .

Is there another occurrence of of swap earlier in fstab??
If so, put a # sign in front of the earlier one.
That will comment out the bogus entry.

jdb

---

### Post by amasiar on 2010-02-06
removed the previous swap entry - and viola - no funky error messages!

Thanks jdb, you are the man :)

---

### Post by thomasaaron on 2010-02-08
Indeed.

---

