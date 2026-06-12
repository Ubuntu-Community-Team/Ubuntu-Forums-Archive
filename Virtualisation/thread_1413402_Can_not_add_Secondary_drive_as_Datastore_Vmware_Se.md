---
title: "Can not add Secondary drive as Datastore Vmware Server 2.0"
date: 2010-02-22
forum: Virtualisation
---

### Post by underminded000 on 2010-02-22
Ok. I'm fairly new to Linux so bare with me. I have Vmware server 2.0 setup on Karmic. My primary datastore is pointed to a folder located  in /home/cjohnson/vmachines (On my primary drive)  which is perfectly fine. I have a secondary drive which im trying to point the other datastore, to no avail. I keep getting "file not found error" which leads me to believe there is some permission issue going on. I have ran vmware-configure.pl several times to make sure there is something i have not skipped in the configuration process with no luck.  Any help will be greatly appeciated as this is drivin me crazy lol.

---

### Post by dcstar on 2010-02-24
> **underminded000 said:**
> Ok. I'm fairly new to Linux so bare with me. I have Vmware server 2.0 setup on Karmic. My primary datastore is pointed to a folder located  in /home/cjohnson/vmachines (On my primary drive)  which is perfectly fine. I have a secondary drive which im trying to point the other datastore, to no avail. I keep getting "file not found error" which leads me to believe there is some permission issue going on. I have ran vmware-configure.pl several times to make sure there is something i have not skipped in the configuration process with no luck.  Any help will be greatly appeciated as this is drivin me crazy lol.

I do not understand what your issue is, on my VMware Server 1.0.10 system I can nominate additional VM drive storage anywhere in my mounted filesystems for new or existing VMs.

I assume you actually have mounted this second drive and it is a Linux filesystem (not some crappy FAT32 filesystem which will not work)?

---

### Post by underminded000 on 2010-02-24
Thanks for the reply. I figured it out. I didn't realize when you specify the path of your datastore it has to be typed exactly as you created it in Ubuntu. For example, my secondary drive path to my Virtual Machines are: /media/MediaDrive/vmachines and I was typing: /media/mediadrive/vmachines/   . Noob mistake .

---

### Post by dcstar on 2010-02-26
> **underminded000 said:**
> Thanks for the reply. I figured it out. I didn't realize when you specify the path of your datastore it has to be typed exactly as you created it in Ubuntu. For example, my secondary drive path to my Virtual Machines are: /media/MediaDrive/vmachines and I was typing: /media/mediadrive/vmachines/   . Noob mistake .

Linux uses case sensitive filesystems, other more primitive filesystems/OSs are not.

---

