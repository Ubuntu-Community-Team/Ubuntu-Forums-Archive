---
title: "I am abe to mount but not access second hard drive after formatting it"
date: 2022-09-23
forum: Ubuntu/Debian BASED
---

### Post by dkdman001 on 2022-09-23
I just added and formatted a 320 gb WD hard drive. This drive is not the boot drive. Now it is showing an  error and i can't access it? I can mount it, though. How do I fix this and get it to be mounted upon start up of the  computer.  I attached a couple pictures of the problem.  I am a new user to Linux. I am using Zorin Linux lite which I know is a variant of Ubuntu.  I appreciate the help
 
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291065&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=291066&stc=1[/IMG]

---

### Post by yancek on 2022-09-23
The error permission denied would indicate that you need root privileges (use sudo) to access the drive partition.  Generally, a normal user will not have write permissions to anything outside the /home/user directory.  You need to change the ownership or permissions on the mount point directory:  /media/joel/uuid

If you want it mounted on boot, you need a line entry in the /etc/fstab file which must be edited with root permissions.  If you try to boot when the drive is not attached and you have an entry in /etc/fstab, you will have problems booting.  There are many sites explain how to create an entry in the fstab file on line.

Is the GParted image you posted the boot drive?  What filesystem type did you format the partition on the the new drive?

---

### Post by dkdman001 on 2022-09-23
I appreciate your help!  I did just figure it out. I reformatted the hard drive and now I have access.  Thanks again!!

---

### Post by coffeecat on 2022-09-23
Zorin.

*Thread moved to **Ubuntu/Debian Based** sub-forum.*

---

