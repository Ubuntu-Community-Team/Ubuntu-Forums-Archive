---
title: "Trying to recover deleted files and directory structure from a live Raid1 ext4 system"
date: 2018-01-19
forum: Server Platforms
---

### Post by CombatGod on 2018-01-19
Hey guys,

I could really use some help. I had about 10 gigs of pictures organized. I can't use photorec because the info is pretty much useless without the directory structure.

Client just told me he decided to unplug the backup and it hasn't been running for at least 6 months.

It's a Raid 1 so I was thinking of taking down one of the drives and running a recovery on it.

I don't need to recover all the files so I'm not concerned too much about using it in a live system but I need to recover at least a good portion of the recent files.


I have a remote folder mounted via FTP on this directory:
/mnt/backup/restore

I'm trying to use extundelete but I'm not sure how to specify the folder to save recovered files to and how to specify the folder to search for files.

Would be willing to even to pay for support.

---

### Post by darkod on 2018-01-19
Can you boot the server with desktop live cd into live mode?

In that case extundelete can be tried, but it has to run on unmounted partition, so your server OS can't be running. How is the server raid organized? Did you had only one big array assigned to /?

---

### Post by CombatGod on 2018-01-19
Sadly right now I can't because I have a few live sites on that server that need to be up. This is why I thought about booting into a degraded Raid. It's a simple Raid 1 setup with the entire root partition on it.

---

### Post by darkod on 2018-01-19
You can try if you prefer that... Power off, detach one disk, power on... Then attach the disk to another computer. In theory raid1 single partition should be readable on its own... Because don't forget, right now your device is for example /dev/md0 and moving the single disk to another computer will be /dev/sdb1 for example... Unless you assemble the degraded raid1 on that computer too...

So think about how you want to proceed depending which options are available to you.

---

### Post by CombatGod on 2018-01-19
The problem is that this is in my datacenter. I don't have physical access. I'm out of town so I need to try to do this all remotely. Not sure how I would even boot into a degraded array unless I modify fstab.

---

### Post by CombatGod on 2018-01-19
Wait I should be able to remove the drive from the array without even needing to reboot?

---

### Post by darkod on 2018-01-19
Yes, I was about to suggest that. You should be able to mark the second member as failed and removed, after that it should be unmounted anyway.

So you can try the extundelete on the unmounted second member...

---

### Post by darkod on 2018-01-19
To add: To make sure the standalone disk/partition can be readable, try temporarily mounting it read-only and check the folder structure. Don't forget to unmount it later before using extundelete because it needs to be unmounted.

Something like (lets assume the disk is sdb and you already removed sdb1 and sdb2 from raid):
```
sudo mkdir /mnt/temp
sudo mount -o ro /dev/sdb2 /mnt/temp
cd /mnt/temp   (check folders and files inside)
sudo umount /mnt/temp
```

---

### Post by CombatGod on 2018-01-19
Awesome, this is a good start, I got the second drive disconnected. Now, I just need to run extundelete, now my question how do I specify the output folder and that I want to preserve the folder structure if possible.

Haven't used that one before.

---

### Post by darkod on 2018-01-20
Did you check the exact path you need first by temporarily mounting the partition?

You need to specify which part you want to undelete, and it is important to get it right. If the md device was mounted as root then the path would be /mnt/backup/restore I guess. But I would double check it first.

I haven't used extundelete but reading its man page you don't specify output folder. I think it tried to undelete all files in their original location. So the files it can undelete will show in the folder where they were at deletion.

Assuming the partition is sdb2, and the path you are interested to recover is the above, the command would be something like:
```
sudo extundelete --restore-directory /mnt/backup/restore /dev/sdb2
```

After the process ends you can check the folder content by mounting it read-only again temporarily. Do not forget to always mount it read-only. When trying to recover deleted data it is important as soon as possible to unmount the folder/device so that sectors do not get overwritten with new data, and that you always access it read-only to prevent further writes...

PS. NOTE: Do not forget, according to the man page the --restore-directory parameter is the folder you want to try to restore, NOT the output folder where you want restored items to be saved!

---

### Post by CombatGod on 2018-01-20
So I ran into a small problem... I can't directly mount a Raid1 drive without using mdadm to assemble it. Then I'm not sure if extundelete would be able to detect the filesystem. I'm trying to see if it's possible to modify the partition tables and change it from Raid1 to just regular ext without killing the journal. As a safety precaution I ran ddrescue and saved the drive image on a backup nas.

Now I'm trying to see if I can run ext3grep on the image and just do a full recovery saving it to my nas to also preserver the original drive as much as possible.

Trying to figure out ext3grep... Thanks for the help so far.

---

### Post by darkod on 2018-01-21
I was unsure about that, if it will allow you to mount an array member without being in array, because the filesystem in mdadm is actually on top of the array.

One alternative that should be possible is something like this:
1. Remove the mdadm superblock on the removed disk. After that it should lose awareness that it belongs to a raid.
2. Create new raid1 array (for example md2) using this disk and one missing member (you can create raid1 with only one disk). BE CAREFUL, you have to use the --assume-clean parameter when using --create if you want to keep the existing data. Otherwise a new blank array will be created.
3. Mount this new md2 array temporarily as read-only to check data is there.
4. Unmount it and use extundelete.

---

### Post by CombatGod on 2018-01-21
I did a quick test using foremost and the files are definitly there. I saw it going through the directories and pulling out the image files. So frustrating that it doesn't keep any metadata.

I see all the directories it's going into to pull the images out. So sad it doesn't preserve any of the info.

Trying to get the Raid Array Mounted ATM.

---

### Post by CombatGod on 2018-01-21
Ok so the Raid Array is mounted.

I got it mounted using loop.

mdadm --assemble --run /dev/md1 /dev/loop1

Then I mounted it to check the files:
mount -t ext4 /dev/md1 /mnt

Unmoutned:
umount /mnt

I then ran extundelete and it only found 60 files.
Right now I'm running ext4magic to do a full recovery of all the files.

Will need to run the gamit to see what I can get recovered.

---

