---
title: "Partitioning and volume manage question"
date: 2012-01-05
forum: Server Platforms
---

### Post by deepakdeshp on 2012-01-05
I am using 10.04 server version and not using lvm. My existing system partition is big and there isnt much data in the partition. How do I shrink the partition without losing the data and free up the space and create another new partition with this freed space?

Is there Veritas volume manager and netbackup (Now taken over by Symantec) available for Ubuntu to try at home in the lab? Or do I need to purchase a license?

---

### Post by volkswagner on 2012-01-06
the easiest method in my opinion is use a live CD.  You will want to backup your system first in case problems occur.  

Boot the live CD  use partition manager (gParted) to resize the partition.  You can also create new partitions at this point.  When you reboot, you can mount the new partitions to your liking.

---

### Post by deepakdeshp on 2012-01-06
But if I shrink the partition , wont I lose the data and I will have to re-install the system. What I am looking forward is to retain the installed system even after shrinking the partition.

---

### Post by volkswagner on 2012-01-06
The system will be intact.  

The reason you should create a backup 1st, is in case of a problem occurence.  If you have a power failure during the resize, that would be bad.
 
I have had great success with this method.

Gparted is great for this.  They even make a live CD, but I find other live distro's more user friendly to get it done.

Just make sure you are on the correct disk then right click the partition and select resize. 

DON'T create a new partition table!

---

### Post by deepakdeshp on 2012-01-07
[QUOTE=volkswagner;11591711]The system will be intact.  



DON'T create a new partition table![/QUOTE
]Thanks, I am using Gparted. It tooka  very long time to shrik a 50b partitioon  to 16 but it did it successfully and I didnt loose data. Thank you

---

### Post by deepakdeshp on 2012-01-08
Is there Veritas volume manager and netbackup (Now taken over by  Symantec) available for Ubuntu to try at home in the lab? Or do I need  to purchase a license?  Does anybody know please?

---

