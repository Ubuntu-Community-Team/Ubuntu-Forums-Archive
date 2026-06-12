---
title: "Unable to resize GPT Partition"
date: 2017-06-07
forum: Server Platforms
---

### Post by belmarrebalde on 2017-06-07
I have a Ubuntu Server 16.4 LTS VM on Hyper-V with a Root Drive and another Data Drive (6TB).
I did the GPT partition using GPART and file system ext3 on the whole 6TB. Mounted and setup directly for file share.
I edited the VM disk and increase it to 8TB. When type gdisk I get the correct size of the device /dev/sdb which is 7.9TB.
The problem is that whenever I tried to resize partition the system doesn't recognize the extra 2TB.
Here is the steps I did:
1. delete the 6tb parition
2. attempted to create a new partition
3. enter the start sector 2048 by default
4. the end sector only allows the value of the end sector of the deleted partition in my case 12884899839.
5. The Disk sectors is 16928210944 which I cannot use.
6. If I leave the options by default i end up with this.
[IMG]https://static.spiceworks.com/shared/post/0025/2325/sdb.png[/IMG]
Please help I am lost.
PS I am newbie with Linux

---

### Post by howefield on 2017-06-07
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by darkod on 2017-06-07
Which part is confusing you? As you can see on that screenshot, you have another small partition of 1MB at the end of the 6TB disk. So even after extending to 8TB in vmware and deleting partition #1, you can only use the same space you had because partition #2 is still there. You can't create a new bigger partition overlapping #2. But you need to check if #2 is used first before deciding whether to delete it or not.

Also, did you already delete partition #1 once and then created a new one? Did you have data you wanted to keep and in such case is it still there?

Usually you would resize a partition, not delete it and create new one, if you want to keep the data. I usually use parted for that, not fdisk/gdisk.

---

### Post by belmarrebalde on 2017-06-07
> **darkod said:**
> Which part is confusing you? As you can see on that screenshot, you have another small partition of 1MB at the end of the 6TB disk. So even after extending to 8TB in vmware and deleting partition #1, you can only use the same space you had because partition #2 is still there. You can't create a new bigger partition overlapping #2. But you need to check if #2 is used first before deciding whether to delete it or not.

Also, did you already delete partition #1 once and then created a new one? Did you have data you wanted to keep and in such case is it still there?

Usually you would resize a partition, not delete it and create new one, if you want to keep the data. I usually use parted for that, not fdisk/gdisk.


How do you resize a partition? Can you give me the correct series of commands? Say for example there is only 1 partition in /dev/sdb disk which sdb1 with a size of 4GB.
The total size of sdb disk is 8GB. I want to use all 8GB for sdb1.

---

### Post by darkod on 2017-06-07
According to parted manual:
[https://www.gnu.org/software/parted/manual/parted.html#resizepart](https://www.gnu.org/software/parted/manual/parted.html#resizepart)

1. Open the disk with parted:
```
sudo parted /dev/sdb
```

2. Set unit size, for example MiB:
```
unit MiB
```

3. Lets say on sdb partition #1 right now is starting at 1MiB and ending at 51200MiB. To move the end point to 102400MiB you would do:
```
resizepart 1 102400
```

4. Quit parted and resize the filesystem to be able to use all space on the new bigger partition:
```
quit
sudo resize2fs /dev/sdb1
```

That's it.

---

### Post by belmarrebalde on 2017-06-07
> **darkod said:**
> According to parted manual:
[https://www.gnu.org/software/parted/manual/parted.html#resizepart](https://www.gnu.org/software/parted/manual/parted.html#resizepart)

1. Open the disk with parted:
```
sudo parted /dev/sdb
```

2. Set unit size, for example MiB:
```
unit MiB
```

3. Lets say on sdb partition #1 right now is starting at 1MiB and ending at 51200MiB. To move the end point to 102400MiB you would do:
```
resizepart 1 102400
```

4. Quit parted and resize the filesystem to be able to use all space on the new bigger partition:
```
quit
sudo resize2fs /dev/sdb1
```

That's it.


Thank you so much I was able to test it out and started with small number and a few slightly different step. Here's what I did, I edited the VM disk to 4TB

1.
```
parted /dev/sdb
```

2. For some reason after I typed P, I always get this Warning: Not all of the space available tp /dev/sdb appears to be used, you an fix the GPT to use all of the space (an extra xxx blocks) or continue with current settings? Fix/Ignore - I typed in Fix and then Press P again and it will display my Disk Properties.
```
P
```

3. After which I then type resizepart 1 100% - I experimented 100% to use the entirety of the disk space. It worked
4. I have to run 
```
[COLOR=#666666][FONT=Monaco]e2fsck -f /dev/sdb1[/FONT][/COLOR]
```
5. Then run the 
```
resize2fs /dev/sdb1
```
6. Mount the disk and check the size and boom! Thank you so much for your help!

---

### Post by darkod on 2017-06-07
No problem. You can mark the thread as Solved in Thread Tools above the first post.

---

