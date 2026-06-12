---
title: "MDADM renames new array after reboot."
date: 2017-12-15
forum: Server Platforms
---

### Post by kaosvold on 2017-12-15
So i am curious as to why I have interesting luck with mdadm since 16.04 and later iterations.  When creating any array, it will be fine until i go to reboot.  The raid fails to auto assemble,and into recovery I go.  What i find is completely unreal to me, it takes the name of the machine, and interjects it into the array device itself.

For instance if i do 
mdadm --create /dev/md/0 --level=6 --raid-devices=16 /dev/sd[b-q] 
it will create the array just fine, and doing


mdadm --detail --scan >> /etc/mdadm/mdadm.conf
gives the result i am looking for.

it doesn't matter what filesystem i seem to use, ext4, xfs, zfs, i will get the same results.
fstab is updated to use something like /mnt/storage /dev/md/0 xfs defaults 0 0

now no matter what i do, it won't boot like this, which completely puzzles me
when i reassemble by scan i get
/dev/md/ComputerName:0 

the mdadm.conf seems to show the name=ComputerName:0 as well here.

I am perplexed, because i typically make sure that i follow a set of procedures for creating the mdadm array
convert to gpt, using 4tb drives
zero each drive
zero superblock


Does anyone have an idea why this occurs?

---

### Post by powersj on 2017-12-15
> **kaosvold said:**
> 
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
gives the result i am looking for.


What does mdadm.conf have in it?

Typically you want to have something like this:

> 
ARRAY /dev/md1 level=raid10 num-devices=4 UUID=41b9fb89:d6664ab6:957040dd:f08e8ef9 

---

### Post by darkod on 2017-12-15
I would manually make the ARRAY entry in mdadm.conf and that way you have maximum control. Plus, mdadm is very good assembling arrays and basically only needs the array UUID. My entries are dead simple, like this:
```
ARRAY /dev/md0 UUID=bf6d60f1:8dc54e7d:8a0059cd:62241355
```

As for fstab, this is why ubuntu started using UUIDs in it years ago. Note that the UUID for fstab is of the filesystem, which is not the same as the array UUID. Use this command to read all UUIDs and you will figure it out:
```
sudo blkid
```

You use the array UUID in mdadm.conf and the filesystem UUID in fstab. I have only used this with ext4 but I guess it should work for other filesystems too. With the filesystem UUID the correct device/array is always mounted even if it changes name.

---

