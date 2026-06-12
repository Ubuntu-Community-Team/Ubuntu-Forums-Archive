---
title: "How actually does UBUNTU handle isw"
date: 2015-06-23
forum: Server Platforms
---

### Post by Victor_Cheung on 2015-06-23
Problem description:
Ubuntu Server 12.04 LTS

My HDD is using RAID-1 isw, message shows sign of breaking so decide to do a swap.

Swap the first drive, reboot, change the isw_xxxxxxx in fstab,
```
sudo dmraid -R isw_xxxxxxx
```
wait for the sync to complete, reboot, see system booting normally.
Shutdown, swap the second drive, drops me to ramfs and do dmraid -r isw_xxxxxxx, wait for the process to complete, lvm can't find any group.

reboot, says system can't find OS, the whole partition is deleted.
really frustrating.

Could anyone help on this? Thanks.

---

### Post by darkod on 2015-06-23
Is that intel fakeraid? Isn't the array created in raid bios, not from inside ubuntu?

---

### Post by Victor_Cheung on 2015-06-24
Yes it is. And can be configured by dmraid too.

And seems it applies a master slave pattern when switching one drive is OK, but switching the other is not, that seems to me make the Intel raid1 useless.(back then the installer recognized the raid so I didn't expect that I should have used madam)

Or it could be that I misunderstood how it works.

---

### Post by Victor_Cheung on 2015-06-24
Oh also, adding a spare using dmraid just creates a new subset which doesn't allow me to do any rebuild.

---

### Post by darkod on 2015-06-24
Honestly, I haven't worked with fakeraid, especially with server version. You say "the installer recognized the raid" so I assume you originally had it configured using raid bios, not dmraid. I would say in such case continue handling the array with the bios and not with dmraid commands. Maybe it doesn't like the fact that it wasn't created by dmraid but later you tried managing it using dmraid. But that's only my opinion...

The way I understand raid with ubuntu, if you use SW mdadm you handle it from the OS. If you use fakeraid or HW card, you handle it from its bios.

---

### Post by Victor_Cheung on 2015-06-24
Switch drive in SATA2, complete sync, switch SATA2 drive to SATA1, add new SATA2, sync succeed.
So I think the isw meta info probably lack identifier for either GRUB or dmraid to determine which one is the one with data, which one is the replaced drive.

The case in which it dropped me into ramfs I would assume that it's recognizing the empty drive as the drive with data and then wiped the drive with data empty after sync.
I still can't pin-point the problem but at least can narrow down the possibility so that if anyone see similar problem there's a procedure that won't wipe your entire drive.

---

