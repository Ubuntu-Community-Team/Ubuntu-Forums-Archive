---
title: "grow raid array"
date: 2011-09-17
forum: Server Platforms
---

### Post by king_duck on 2011-09-17
Hi, I have a raid 5 array with 5 2TB drives and I'm trying to add another drive to the array.

It looks like I've added the drive to the array inside webmin and the usable size is 9TB, however if i run df -h the array still appears to be 7.2TB and other clients can only see 7.2TB.

Any clue what to do?

---

### Post by Habitual on 2011-09-17
I can't remember if you have to stop the array or not, but the command to grow is
```
xfs_growfs -d /dev/md0
```

substitute md0 for the appropriate array device.

---

### Post by YesWeCan on 2011-09-17
If the array is md0 and the fs is ext4

sudo e2fsck -f /dev/md0
sudo resize2fs /dev/md0

Consider RAID6 for a large array if data protection is a priority.

---

### Post by king_duck on 2011-09-17
Oops, guess I didn't really give any info in the first post.  Anyway it is ext4 and it looks like YesWeCan's post is right.  Do I have to have the array unmounted, and about how long will this take with 6 2TB drives?

---

### Post by Habitual on 2011-09-17
> **YesWeCan said:**
> If the array is md0 and the fs is ext4

sudo e2fsck -f /dev/md0
sudo resize2fs /dev/md0

Consider RAID6 for a large array if data protection is a priority.

+1 
shows how little I know. See my sig for disclaimer. :)

---

### Post by rubylaser on 2011-09-18
For the fsck, you'll want to not have the array mounted. So just unmount it, run the fsck, then expand it, and remount the filesystem.

```
sudo -i
umount /path/to/array
fsck.ext4 /dev/md0
mount -a

```

---

### Post by king_duck on 2011-09-18
Thanks guys I'm resizing the array now with resize2fs, seems to be working.  I started the command without noticing the -p switch to show progress, is there any other way to check the progress or should I just leave it until it's done?

update
Wow nevermind that didn't take long and all. But thanks again for everyone's help

---

### Post by YesWeCan on 2011-09-18
Well done. Don't forget to mark this as solved in [COLOR=Red]Thread Tools[/COLOR].

---

