---
title: "Need advice on builiding my first Raid5 array."
date: 2009-09-30
forum: Server Platforms
---

### Post by u-slayer on 2009-09-30
I'm building my first Raid5 array and want to know what size disks I should be using. Right now I have 3 1TB disks (5200rpm WDs) I could combine, but I know that in the future 2TB disks will be more economical.

Should I combine 2 of my a 1TB drives into a block to use with another 2TB drive or should I stick to a 1TB disk size?

Also, is it possible to change the disk size in the future? Let's say i have an array with 4 1TB drives. Could I replace them 1 by 1 with 2TB drives and then expand the array?

---

### Post by lmlypfan on 2009-09-30
I'm using mdadm for a RAID5 config with 3 1TB drives. 
That being said, I'm pretty sure you cannot upgrade to 2TB drives one at a time. I also don't think combining 2 1TB drives into a single block to pair with a 2TB drive will work either. 

When building my RAID array, I was worried about a future upgrade path as well. I've only used 600GB of 1.9TB, so i have some time to figure it out :)

---

### Post by MJWitter on 2009-10-01
I haven't tried it before, but you are able to replace the drives, one by one, with larger drives, the link gives a good overview:
[http://cobraftp.serveftp.com/pub/raid.pdf]("http://cobraftp.serveftp.com/pub/raid.pdf")
Remember to have good backups of important data before doing anything that could be risky!

---

### Post by MJWitter on 2009-10-01
Sorry, duplicate post!

---

### Post by lmlypfan on 2009-10-01
I stand corrected. Thank you for the pdf, really handy.

---

### Post by u-slayer on 2009-10-02
> **MJWitter said:**
> I haven't tried it before, but you are able to replace the drives, one by one, with larger drives, the link gives a good overview:
[http://cobraftp.serveftp.com/pub/raid.pdf]("http://cobraftp.serveftp.com/pub/raid.pdf")
Remember to have good backups of important data before doing anything that could be risky!

As Regan said: "Trust but verify" I tested my assumptions about Raid5 by creating 3 loop file devices and assembling them into an array. It works.

---

### Post by u-slayer on 2009-10-02
My tests with Encrypted Raid:
Though you guys might be interested.

I created loop devices out of 3 100 meg files. Ram should be able to cache these.
```
root:/dev# losetup /dev/loop1 /x/test/1
root:/dev# losetup /dev/loop2 /x/test/2
root:/dev# losetup /dev/loop3 /x/test/3
```

Here I encrypted each raid drive separately:
```

root:/dev# cryptsetup create e1 loop1
Enter passphrase: 
root:/dev# cryptsetup create e2 loop2
Enter passphrase: 
root:/dev# cryptsetup create e3 loop3
Enter passphrase: 
root:/dev# cd mapper
root:/dev/mapper# mdadm --create --verbose /dev/md0 --level=5 --chunk=64 --raid-devices=3 e1 e2 e3
mdadm: layout defaults to left-symmetric
mdadm: size set to 102336K
mdadm: array /dev/md0 started.
```

Testing:
```
root:/dev/mapper# hdparm -t /dev/md0

/dev/md0:
 Timing buffered disk reads:  128 MB in  3.04 seconds =  42.07 MB/sec
root:/dev/mapper# hdparm -t /dev/md0

/dev/md0:
 Timing buffered disk reads:  164 MB in  3.02 seconds =  54.28 MB/sec
```

In the second test I put the encryption on top of the raid block, so only one thread was handling the encryption.
```
root:/dev# mdadm --create --verbose /dev/md1 --level=5 --chunk=64 --raid-devices=3 loop0 loop2 loop3
mdadm: layout defaults to left-symmetric
mdadm: size set to 102336K
mdadm: array /dev/md1 started.
root:/dev# cryptsetup create eraid md1
Enter passphrase: 

```

Testing array without any encryption:
```
hdparm -t md1

md1:
 Timing buffered disk reads:  198 MB in  0.76 seconds = 259.27 MB/sec
root@black:/dev# hdparm -t md1

md1:
 Timing buffered disk reads:  198 MB in  0.64 seconds = 311.56 MB/sec
```

And testing with encryption:
```
root:/dev# hdparm -t /dev/mapper/eraid

/dev/mapper/eraid:
 Timing buffered disk reads:  130 MB in  3.01 seconds =  43.17 MB/sec
/dev/mapper/eraid:
 Timing buffered disk reads:  136 MB in  3.04 seconds =  44.80 MB/sec

```

So the large encryption block on top is slightly faster than individual encrypted blocks. However, the downside is that if I ever wanted to change my password I would have to backup all the data first. With the raid block sitting on encrypted device blocks, I can change the password one drive at a time without backing up the data.

I tested this on a dual core laptop. I'll see if my cheap AMD quad core (only 512K per L2 cache and no L3 cache) can do any better with separate encryption blocks.

---

### Post by u-slayer on 2009-10-02
However, the downside is that if I ever wanted to change my password I would have to backup all the data first. With the raid block sitting on encrypted device blocks, I can change the password one drive at a time without backing up the data.[/QUOTE]

Maybe you can change the password without backing up your data. This actually seems to work:

Create maps for the old and new password pointing to the same device.
```
root:/dev/mapper# cryptsetup create old /dev/loop3
Enter passphrase: 
root:/dev/mapper# cryptsetup create new /dev/loop3
Enter passphrase: 
```

Copy the data from old to new:
```
root:/dev/mapper# dd if=old bs=1M of=new
100+0 records in
100+0 records out
104857600 bytes (105 MB) copied, 3.9763 s, 26.4 MB/s
```

Oh and if you screw up and transpose "old" and "new" it will destroy all your data. Have Fun!:P

---

