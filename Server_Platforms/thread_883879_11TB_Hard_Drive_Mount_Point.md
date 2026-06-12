---
title: "11TB Hard Drive Mount Point"
date: 2008-08-08
forum: Server Platforms
---

### Post by whitemts on 2008-08-08
Hello,
I built out a two x64 Ubuntu 8.04.1 servers on Pogo hardware.  I have a RAID 1 OS drive with 1TB, I also created a RAID 5 drive with 11TB on each of the servers.  I have the servers all built and the second drive mounted.  My questing is: the mount point is /media/disk is this standard practice or should I choose a different mount point, maybe at the root?  Also if I choose to change the mount point is the only step changing the fstab file?

Thank you in advance,

---

### Post by smileypaul on 2008-08-08
You can mount it wherever you please.. just make sure you update the fstab file.. 

Although "standard practise" is that disks get mounted in /media .. its not a must.

---

### Post by tamoneya on 2008-08-08
i like to think of /media/device as the default.  There is no reason why you have to do it that way its just that ubuntu will put it there unless you tell it otherwise.  There is no magic to the mount point.  It just depends on what you need it for.  For example, if you were using it for a webserver it might make the most sense to mount in /var/www/.

---

### Post by whitemts on 2008-08-08
Thanks for the replies.  This clarifies things.

---

### Post by bab1 on 2008-08-08
You can mount any partition at any mount point.  Since a mount point should be an empty directory, no mount at / will work.

---

