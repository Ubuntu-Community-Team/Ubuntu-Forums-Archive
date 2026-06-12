---
title: "Virtualbox VDI Actual vs Virtual size"
date: 2013-04-17
forum: Virtualisation
---

### Post by kmand on 2013-04-17
I'm running Virtualbox 4.2.12 on Ubuntu 12.10. The Win7 client has a VDI  which shows as

Normal (VDI)
Virtual Size 25.39GB
Actual Size 16.51GB
Dynamically Allocated Storage

Snapshots just shows current.

From the Linux side the vdi file is what the Actual Size says, which is also all the Win7 sees in disk properties.

The VBoxManage modifyhd command succeeds and can increase the Virtual Size.

How do I actually get the Actual Size to go up?

---

### Post by SeijiSensei on 2013-04-17
I believe it just grows until it reaches the 25.39 max.  That's what is meant by "dynamically allocated storage."  Try copying a large file to the Windows guest and see what the numbers are like after that.

---

### Post by kmand on 2013-04-17
> **SeijiSensei said:**
> I believe it just grows until it reaches the 25.39 max.  That's what is meant by "dynamically allocated storage."  Try copying a large file to the Windows guest and see what the numbers are like after that.

No that can't work, win7 sees the filesystem as nearly full and keeps complaining, which is why I'm trying to expand the disk. If Win7 saw the disk as larger than the NTFS filesystem I know about expanding the filesystem. But it sees the filesystem as using the whole C disk.

---

### Post by CharlesA on 2013-04-17
I've tried to increase the size of dynamic disks before on a Windows guest, but even booting a Gparted livecd showed the same size drive as before. I ended up just creating a new virtual drive and cloning the OS to it.

No idea why it wasn't working, just that it apparently doesn't work all the time:
[http://askubuntu.com/questions/88647/how-do-i-increase-the-hard-disk-size-of-the-virtual-machine](http://askubuntu.com/questions/88647/how-do-i-increase-the-hard-disk-size-of-the-virtual-machine)

---

### Post by kmand on 2013-04-17
I found my problem. It turns out you have to boot the guest into gparted. Although win7 doesn't see the virtual disk size, gparted does. When you repartition (expanding the NTFS) on the vdi that actual size changes, and windows sees it as a larger disk when you next boot the guest from the windows vdi.

---

