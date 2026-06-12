---
title: "Error setfacl operation not supported"
date: 2010-08-05
forum: Server Platforms
---

### Post by brouka on 2010-08-05
Hi guys

I have a problem with acl's in Ubuntu Server 10.04. When i write in a terminal the command setfacl, the machine returns error: **setfactl /home/xxxx: operation not supported.**
Please, help me.
Thanks for all.
Regards

---

### Post by brouka on 2010-08-06
Hi friends :D
Im going to post my own aswer. I found the solution for this problem.
the key was in a /etc/fstab. 

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

[SIZE=3]**I change this line, added ",acl" to end of the remount****-ro**[/SIZE]

# / was on /dev/sda1 during installation
UUID=9e691515-208d-46a8-8ebc-698d98fc38ea /  ext4   [SIZE=3] **errors=remount-ro,acl 0       1**[/SIZE]


[B]I have been added this line to my fstab. Dont' work
#/dev/sda1        /home          ext4    defaults,acl      0       0
[/B]
Now the command setfacl work perfectly.

Regards.

---

