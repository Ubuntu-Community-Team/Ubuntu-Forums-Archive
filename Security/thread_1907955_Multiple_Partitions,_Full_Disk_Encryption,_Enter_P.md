---
title: "Multiple Partitions, Full Disk Encryption, Enter Passphrase Once at Boot"
date: 2012-01-12
forum: Security
---

### Post by Ri.Kenji on 2012-01-12
Just so there's no confusion, I'm trying to configure my system like this:
[IMG]http://i40.tinypic.com/34o2369.jpg[/IMG]
I've got a general idea what I have to do, but nothing concrete:

[LIST=1]
[*]Partition the system.
[*]Install Ubuntu with full disk encryption to a temporary partition.
[*]Move the directories into the correct partitions.
[*]Modify **initramfs**, **fstab**, and **cryptab** to reflect the changes.
[/LIST]
Stuff I'm not sure about:


[LIST]
[*]Since I've got the keys in an encrypted partition and no other partition has been mounted yet, I believe I'll have to mount the key partition as **/**, let **fstab** and **cryptab** do its magic, and somehow unmount the temporary **/** and let the real **/** take over. **fstab** and **cryptab**, however, are stored in the real **/**, so it's all going to have to somehow be done within **initramfs**.
[/LIST]

---

### Post by MadsRC on 2012-01-13
Is there any special reason you want 3 partitions (excluding the boot&key partitions)?

Why not just do:
 - Boot&key partitions.
 - OS partition (with persistent SWAP file).

---

### Post by Ri.Kenji on 2012-01-13
> **MadsRC said:**
> Is there any special reason you want 3 partitions (excluding the boot&key partitions)?

Why not just do:
 - Boot&key partitions.
 - OS partition (with persistent SWAP file).
It's my strong preference to keep things separated. But even if I were to merge most of the partitions, it wouldn't really solve the issue of mounting the key partition before **/**.

---

