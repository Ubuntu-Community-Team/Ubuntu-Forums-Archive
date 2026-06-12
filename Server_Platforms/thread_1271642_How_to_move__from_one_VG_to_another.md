---
title: "How to move / from one VG to another?"
date: 2009-09-21
forum: Server Platforms
---

### Post by Xianath on 2009-09-21
Hi all,

I have an Ibex server running successfully on top of a software RAID5 (/boot sits on a RAID1 built from the first partitions of component disks). I have a VG called "System" which contains four LVs: Boot, Root, Home and Var, with Boot residing on the RAID1 PV. All is fine and dandy, but now I want to migrate over to the new RAID6 array I've just built. How do I do that without reinstalling? I was thinking of copying over the system to the respective LVs on the new RAID6 VG, setting up a chroot with a modified fstab, running lilo from within the chroot, then booting into that -- will this work? Any hints as to how to get /dev to populate properly within the chroot? Or is there a howto on the subject that I've missed?

Thanks,
Peter

---

### Post by Xianath on 2009-09-21
OK so I bit the bullet and messed up. I copied the system over to the respective LV in the VG that sits on top of the RAID6 md device using xfsdump. I edited mdadm.conf to reflect the new array configuration (why is this still necessary?!) and ran update-initramfs.sh -u. I am now down to a busybox shell complaining about my old LVs missing (I did lvremove them).

Does anyone have an idea how to go about this, or should I just reinstall just like I do with Windows when it ultimately messes up?

Thanks,
Peter

---

