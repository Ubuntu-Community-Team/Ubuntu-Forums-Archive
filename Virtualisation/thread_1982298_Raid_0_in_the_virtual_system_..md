---
title: "Raid 0 in the virtual system ."
date: 2012-05-18
forum: Virtualisation
---

### Post by Docmero on 2012-05-18
[CENTER]Hi , I have ubuntu 11.10 (host)
and Win 7 6bit inside Vmware .
I have 2 hard disks . Can I use them to make 
a virtual raid inside the virtual system ?
If yes , How ?
Also , If the there is a RAID 0 in the host system ,
Will this boost the guest's performance ?
Thanks 
[/CENTER]

---

### Post by CharlesA on 2012-05-18
Just one thing to note: RAID 0 offers no data redundancy. If you lose one disk, you loose all your data.

In order to run RAID on a VM, you need to have 1 or more virtual drives attached to the machine and set them up in a RAID configuration. I'm not sure if you Set Windows up to use RAID post install tho.

---

### Post by Docmero on 2012-05-18
well , As I don't have valuable information on my virtual machine , I don't care about losing the data in it  .
Indeed I have multiple hard disks , but how to connect them to Vmware. No I didn't set windows to use RAID upon installation .

---

