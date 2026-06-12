---
title: "Encrypting an entire RAID1 system without LVM? What if one of the drives fail?"
date: 2014-02-21
forum: Security
---

### Post by Thavid88 on 2014-02-21
Hi there,

I would like to install a Debian Wheezy on my new Dell server. The plan is: RAID1 with two disks and encryption. I googled about encryption and I was surprised that 99% of the sites/forums are talking about LVM + LUKS. I really don't need LVM. I know what it can offer for my but I don't really need it: I don't mind to type the password for every encrypted partition and I don't want to resize my partitions in the future. And I also don't mind if somebody finds out how many partitions I have (encrypted). But basically that is what LVM offers me.

So, I know that I can use LUKS only, but I was wonder: what will I do if one of my HDD's will fail. How should I replace it? I know how to replace a drive with mdadm but in this scenario the partitions will be encrypted! If I rebuild the new disk from the booted system, it will loose encryption because at that level I already typed the key for my system. Am I right? I simply cannot find a site where somebody tells me exactly how to replace a drive in RAID1 + LUKS. Only RAID1 + LUKS + LVM.

Can anybody point me to the right direction? Should I use LVM just to find these type of answers easily??!

Thank you very much for your help!

David

---

### Post by Thavid88 on 2014-02-22
I just answered my own question..

The process is the very same, just like with non encrypted disks. I tested it out, the RAID1 arrays are rebuilding the same way and after that everything was encrypted. I used a Debian live DVD to boot then mounted the partitions and I had to use the password for all the partitions on both disks.

---

