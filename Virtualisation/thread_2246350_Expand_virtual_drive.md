---
title: "Expand virtual drive"
date: 2014-09-30
forum: Virtualisation
---

### Post by selo2 on 2014-09-30
Hi,

i know very various methods about expanding vmware virtual disk for ubuntu . but i confused more. i installed form Dspace liveCD an ubuntu OS our ESX server with 40 GB of HDD. whan i looked up with fdisk -l /dev/sda 

/dev/sda1   *        2048    77279231    38638592   83  Linux
/dev/sda2        77281280    83886079     3302400    5  Extended
/dev/sda5        77283328    83884031     3300352   82  Linux swap / Solaris

how can i resize primary disk to 80 GB. 

as i can see , i have no logical volume, no volume groups.

thanks in advance

selcuk

---

### Post by Bucky Ball on 2014-09-30
*Thread moved to **Virtualisation**.*

Better chance of support here. Your request has nothing to do with Desktop Environments .... ;)

Good luck and welcome.

---

### Post by selo2 on 2014-09-30
thanks.

---

### Post by varunendra on 2014-10-01
While there may be ways to do this, why don't you simply add a new 80GB virtual disk, then clone this one (using clonezilla) to that new one, and remove the older disk from the VM. After testing the new one successfully, delete the existing 40 GB virtual disk.

Should be the fastest way I think, if you have that much extra space on the physical disk.

---

