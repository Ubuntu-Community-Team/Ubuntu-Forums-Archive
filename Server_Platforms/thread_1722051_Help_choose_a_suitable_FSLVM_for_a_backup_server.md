---
title: "Help choose a suitable FS/LVM for a backup server"
date: 2011-04-05
forum: Server Platforms
---

### Post by abadr on 2011-04-05
Hi,

I'm setting up a new backup server and I appreciate your help in choosing the most suitable FS/LVM. 

I have the OS on a dedicated hard drive. For the backup storage, I will now add 2x 2TB hard disks and expect to add a 3rd in the near future. 
I'm thinking of using LVM2 but not to manage several logical partitions, but to make a single network share point and ease management. 

1)Is such use of LVM the best solution? or is there a more suitable multi volume FS or LVM?
2)I'm a fan of XFS but it seems that I can't shrink it which is a must if I need to replace a drive in LVM2. What do you recommend instead as a file system?

Thanks.

---

