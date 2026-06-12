---
title: "Ubuntu MDADM Raid 1 Accidental Zero Superblock"
date: 2019-07-03
forum: Server Platforms
---

### Post by sithrage on 2019-07-03
[COLOR=#242729][FONT=Arial]I've spent the past 24 hours trying to resolve my issue. While attempted to add another 2 disc raid to my server I accidentally changed the label for one of my drives in the original raid. To further complicate my issue, I accidentally zeroed the superblock on the remaining good drive. I've been having a lot of medical issues lately and I should not have been trying to do this upgrade. But, I'm at a loss for recovering my data, 4TB worth, with many files not backed up elsewhere.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
To recap:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I was trying to setup labels on a new pair of drives (sdc and sdd), when I accidentally changed the label of an existing raid drive (sdb).
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]While trying to setup sdc and sdd as raid 1 after a failed attempt, I accidentally ran sudo mdadm --zero-superblock /dev/sda on my first raid, which ruined my remaining backup of the data.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I'm not a super expert in Ubuntu, but have gotten by until today. If anyone can help me recover this data I would be eternally grateful. I'm at a total loss.[/FONT][/COLOR]

---

### Post by darkod on 2019-07-03
Are the drives from first array still sda and sdb? And did you use whole drives, like sda and sdb, or partitions like sda1 and sdb1?

By changing the label you mean overwrote the partition table in parted?

And after you removed the superblock from sda did you do anything else on that drive?

---

### Post by sithrage on 2019-07-03
Hello, thank you so much for the questions.

sda and sdb are still the original raid drive and I used the whole drive following this tutorial: [https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04)

After I overwrote the superblock I tried a number of different recovery approaches I found on Google anywhere from testdisk to fs2ck. Nothing has worked so far.

As for the label question, I used "(parted) mklabel gpt" on the sdb drive on accident. I was copying the code from a site and accidentally captured a return, so it ran before I could change the drive letter.

---

### Post by darkod on 2019-07-03
Depending if the things you ran on sda later could have destroyed something more, you might be able to save this or not. Because only destroying the superblock is easily recoverable.

Usually you would try this with both disks, but since you have only one lets try to re-create the array with sda and one missing disk:
```
sudo mdadm --create /dev/md0 --assume-clean --verbose --level=raid1 --raid-devices=2 /dev/sda missing
```

The --assume-clean parameter is very important because it tells mdadm to keep the data on the disks instead of creating new array.

The above command should create new array with default values, so unless you used special command/values when creating the array in the first place, you should be OK trying this first.

After it assembles the array try to mount it as read only and check if you can see the data on it:
```
sudo mount -o ro /dev/md0 /mnt
cd /mnt
ls
```

Let us know how it goes.

---

### Post by sithrage on 2019-07-03
> **darkod said:**
> Depending if the things you ran on sda later could have destroyed something more, you might be able to save this or not. Because only destroying the superblock is easily recoverable.

Usually you would try this with both disks, but since you have only one lets try to re-create the array with sda and one missing disk:
```
sudo mdadm --create /dev/md0 --assume-clean --verbose --level=raid1 --raid-devices=2 /dev/sda missing
```

The --assume-clean parameter is very important because it tells mdadm to keep the data on the disks instead of creating new array.

The above command should create new array with default values, so unless you used special command/values when creating the array in the first place, you should be OK trying this first.

After it assembles the array try to mount it as read only and check if you can see the data on it:
```
sudo mount -o ro /dev/md0 /mnt
cd /mnt
ls
```

Let us know how it goes.

Oh my God... that worked! Thank you! I was losing my mind!!!!

---

### Post by sithrage on 2019-07-03
Do you have any recommended reading material on MDADM and how to properly setup RAID? I see so many varying practices and most of them don't work.

---

### Post by darkod on 2019-07-03
Honestly, I don't have anything at hand and no time to look online now...

Don't forget the half-array is mounted read-only now and it has only one disk.

Unmount it and add sdb to gain two-disk array again. After that mount it where ever it was mounted before.

```
sudo umount /mnt
sudo mdadm /dev/md0 --add /dev/sdb
```

It might take a while to sync, depending on size.

---

### Post by sithrage on 2019-07-03
Thank you, you're my hero!

---

