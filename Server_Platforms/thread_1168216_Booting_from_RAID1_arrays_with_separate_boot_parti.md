---
title: "Booting from RAID1 arrays with separate boot partitions"
date: 2009-05-23
forum: Server Platforms
---

### Post by samosamo on 2009-05-23
What is the correct way to configure grub to boot off of sda, or sdb in the event of a failure?  My situation is a little different because of the separate /boot partition.  I could not find a grub how-to for this.

I have 2 drives configured like so:
```
128MB	/dev/sda1,sdb1	/dev/md0	
4GB	/dev/sda2,sdb2	/dev/md1
10GB	/dev/sda3,sdb3	/dev/md2
```

I then have the system configured for:
```
/boot	/dev/md0
swap	/dev/md1
/	/dev/md2
```

---

