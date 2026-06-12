---
title: "How to recover raid 10 data?"
date: 2012-07-04
forum: Server Platforms
---

### Post by quickk on 2012-07-04
Hi everyone, 

    I installed linux mint and somehow it managed to break my raid array.  My usual system is kubuntu 12.04, and I thought that I'd try linux mint on a different partition.

My array was configured with mdadm as a raid 10 with 2 x 2TB drives /dev/sda and /dev/sdb (mdadm can do raid 10 with 2 drives).  

I think what happened is that linux mint installed grub onto one of the drives.   I'm not sure though.

Now, when I try to assemble the array, I get the following:

```
mdadm: device 1 in /dev/md/1 has wrong state in superblock, but /dev/sda1 seems ok
mdadm: /dev/md/1 assembled from 0 drives and 2 spares - not enough to start the array.

``` 

How do I get my data back?   I thought that I should be able to start the array even if one disk was bad.   How do I do this?

Thank you for any help you can provide.

---

### Post by quickk on 2012-07-04
After a lot of reading, I found that just recreating the array with the problematic drive name replaced by "missing" would fix my problem.

I originally created the array with the following command:

```
sudo mdadm --create /dev/md1 --metadata 1.2 --level=10 --layout=f2 --raid-devices=2 /dev/sda1 /dev/sdb1 
```

To get my raid array back I did:


```
sudo mdadm --create /dev/md1 --metadata 1.2 --level=10 --layout=f2 --raid-devices=2 /dev/sda1 missing 
```

(each "faulty" drive is replaced by missing, in my case /dev/sdb1).

I then got the following message:

```
mdadm: /dev/sda1 appears to contain an ext2fs file system
    size=1953512500K  mtime=Mon May 21 02:10:46 2012
mdadm: /dev/sda1 appears to be part of a raid array:
    level=-unknown- devices=0 ctime=Mon May 21 02:54:11 2012
Continue creating array?

```

I was afraid that I'd loose all the data, but having no alternative,I typed "yes", and then I got:
```
mdadm: array /dev/md1 started.
```   

The array started right away, and now I can access my files.   I'll now try to add the other drive back in.

---

