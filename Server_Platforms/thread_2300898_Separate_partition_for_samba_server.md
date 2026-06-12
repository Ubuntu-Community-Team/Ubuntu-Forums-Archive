---
title: "Separate partition for samba server"
date: 2015-10-29
forum: Server Platforms
---

### Post by gardenair on 2015-10-29
[COLOR=#000000][FONT=verdana]I have install samba in my Linux box . For that purpose I  keep 10 GB free space for "public data". I create a partition using Fdisk command,restart it then formate it and then restart the system.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I can see the separate Hard Disk with a folder "lost+ found". I create a folder in it "public data".[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I want to mount that folder on that partition. Kindly any body guide me.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]thanks
gardenair[/FONT][/COLOR]

---

### Post by darkod on 2015-10-29
Created an empty folder for the mount point. For example /publicsamba.

Then lets assume the partition you created is /dev/sda5 and it has ext4 filesystem. To have it mount on each boot open /etc/fstab and make a line like:
```
/dev/sda5   /publicsamba  ext4   defaults   0   0
```

That should be enough. Inside /publicsamba you can have any folder structure you want.

---

### Post by gardenair on 2015-10-30
I even did that but no success......

---

### Post by darkod on 2015-10-30
Then you're doing something wrong. Print the partitions of the disk, for example if the disk is /dev/sda post the output of:
```
sudo parted /dev/sda print
```

That will show all partitions on it. Explain which one you want to use.

Also post the output of:
```
df -h
```

So we can see what is mounted right now...

---

