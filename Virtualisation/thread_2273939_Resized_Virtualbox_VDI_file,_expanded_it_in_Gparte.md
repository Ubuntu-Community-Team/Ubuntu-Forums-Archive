---
title: "Resized Virtualbox VDI file, expanded it in Gparted...Ubuntu doens't see extra space"
date: 2015-04-16
forum: Virtualisation
---

### Post by liquidcross on 2015-04-16
I used VBoxManage to expand the default 8GB VDI for Ubuntu to 12GB. Then I booted the VM into Gparted to enlarge the main partition. No problems yet. However, when booting into the Ubuntu VM, it doesn't see the 12GB drive; it's only seeing 8GB, and telling me I'm running out of space (which was why I resized in the first place). Running Gparted again confirms it's a 12GB drive. Please advise?

---

### Post by ajgreeny on 2015-04-16
How did you boot to gparted in your VM?

When I needed to do exactly what you are wanting to do, I added a live CD iso file as a new IDE cdrom drive in the Settings ->Storage part of the virtual disk in VBox (in my case I used a live Lubuntu iso which I already had), then booted to that by pressing F12 when booting that virtual disk in order to choose the IDE cdrom drive as boot device.  I was then able to resize the partitions of my virtual install of Ubuntu without a problem.

What took most time for me was actually managing to get vboxmanage to resize the disk, and it failed several times; resizing the partitions within that disk, however, was very easy.

---

### Post by liquidcross on 2015-04-16
That's exactly what I did, except I used a Gparted ISO to boot from. But after I boot into Ubuntu proper, it still says the disk is only 8GB under Disk Usage...while Gparted (within Ubuntu) says 12GB.

---

### Post by ajgreeny on 2015-04-16
Strange.

Did the vboxmanage job go as you expected because, as I said, this was the difficult part for me.

---

### Post by liquidcross on 2015-04-16
Yep, that worked fine, too.

---

### Post by gedakc on 2015-04-18
Are you using Logical Volume Management (LVM2) for your Ubuntu installation?

If so, then GParted would grow only the LVM2 PV (Physical Volume).  You would still need to perform some extra work to determine and grow the appropriate LVM2 LV (Logical Volume).  The command line tool for this is **lvresize**.

---

### Post by liquidcross on 2015-04-19
> **gedakc said:**
> Are you using Logical Volume Management (LVM2) for your Ubuntu installation?

If so, then GParted would grow only the LVM2 PV (Physical Volume).  You would still need to perform some extra work to determine and grow the appropriate LVM2 LV (Logical Volume).  The command line tool for this is **lvresize**.
Thanks! Do I need to use a boot disk, or can I perform that while I'm logged in normally?

---

### Post by TheFu on 2015-04-20
You can increase ext4 file systems on a running file system, however, it is smart to boot off an ISO and do this sort of work. 
If you are NOT using lvm, you can run **resize2fs**. Check the manpage for details. I wasn't running virtualbox (was using KVM), but the same stuff applies. [http://blog.jdpfu.com/2010/10/31/solved-increase-kvm-vm-image-file-size](http://blog.jdpfu.com/2010/10/31/solved-increase-kvm-vm-image-file-size) explains.

---

