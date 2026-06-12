---
title: "moving from a VM to a real box"
date: 2013-10-27
forum: Virtualisation
---

### Post by clearski on 2013-10-27
Hello, everyone.    I've got a server running on a VirtualBox VM. It is fully configured and offering services to some hosts on a LAN.  I just received a PC and would like to move the whole server (12.04.3) on the real box.    Any info / link / howto / help would be much appreciated. I can't figure out how to start and wouldn't like to spend a week to reinvent the wheel because I am sure it was already invented. :)   Thank you.

---

### Post by TheFu on 2013-10-28
a) why not make the new PC a VM host and just migrate the VM using "Export ..."?
b) Backup from the VM, then restore to the new box.

I've used both methods successfully with Linux systems.  Windows is a completely different problem, however. Too many are-the-hardware-similar chekcs and DRM stuff, I suppose.

---

### Post by clearski on 2013-10-29
Hello, TheFu!

Thank you for the answer. 

It will be a headless PC and won't run any GUI. I think I'll install the OS again and try to move some config files, just to see if it works. :)

---

### Post by TheFu on 2013-10-29
> **clearski said:**
> Hello, TheFu!

Thank you for the answer. 

It will be a headless PC and won't run any GUI. I think I'll install the OS again and try to move some config files, just to see if it works. :)

I recently posted a non-trivial backup script to my blog that should work with a minimal install on the real target hardware. [http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use) - be certain to use **dpkg** --get-selections and --set-selections ... to save and restore all the installed packages.  Stuff installed outside the package management system is completely up to you. I avoid that stuff.

Just copying some settings probably isn't enough.

Incremental backups take 1-3 minutes, though the 1st backup will take as long as a copy does.  To restore to a new machine takes about 30 min - 15 to load a minimal Ubuntu OS, then 15 to restore all the settings, data and reinstall the prior list-o-packages. Simple, simple.  Ending with a replicated server in all the most important ways.  Only the network settings usually need to be manually tweaked in /etc/udev/ to clean out the old eth[0-4] MAC addresses.

---

### Post by CharlesA on 2013-10-29
I'd probably just run KVM and convert the VM over that way. I seem to recall doing that with my original Vbox VMs, but I don't remember the actual conversion process except that it involved converting the virtual hard drive to RAW and then converting that to QCOW2.

And here it is...
[http://cheznick.net/main/content/converting-a-virtual-machine-from-virtualbox-to-kvm](http://cheznick.net/main/content/converting-a-virtual-machine-from-virtualbox-to-kvm)

Woo!

---

### Post by clearski on 2013-10-30
Thank you, guys.

Let me read a little bit about your solutions and see what I can do.

I've never heard of KVM & Qemu until now... so it needs some reading.

---

### Post by coldraven on 2013-10-30
```
**VBoxManage clonehd /path/to/hard_drive_image/guesthd.vdi /path/to/hard_drive_image.img --format raw**
```
So in theory you could burn this image to the new drive and it would boot?
Or am I reading this wrong?

---

### Post by TheFu on 2013-10-30
> **coldraven said:**
> ```
**VBoxManage clonehd /path/to/hard_drive_image/guesthd.vdi /path/to/hard_drive_image.img --format raw**
```
So in theory you could burn this image to the new drive and it would boot?
Or am I reading this wrong?

Doubtful.  Raw is a disk format for VMs and includes a partition table that probably is NOT compatible with real HDDs.

There really isn't any way shorter than doing the backup, installing a base OS on the new machine, then doing a restore. Should take about an hour total - depending on the size of the OS+data to be moved.  While the backup happens, install the fresh, limited OS on the new box .. should be 15 min or so.

Still ... Try it - nothing to lose since it is a new box, right? Try the 'raw' disk too ...   If something fails, copy/paste the exact command and errors back here.

---

### Post by CharlesA on 2013-10-30
> **TheFu said:**
> Doubtful.  Raw is a disk format for VMs and includes a partition table that probably is NOT compatible with real HDDs.

There really isn't any way shorter than doing the backup, installing a base OS on the new machine, then doing a restore. Should take about an hour total - depending on the size of the OS+data to be moved.  While the backup happens, install the fresh, limited OS on the new box .. should be 15 min or so.

Still ... Try it - nothing to lose since it is a new box, right? Try the 'raw' disk too ...   If something fails, copy/paste the exact command and errors back here.

I guess you could try cloning the VM and restoring it to a physical box, but that could cause problems with hardware mismatch. I'd probably go with "install KVM and mess with it" :p

---

### Post by TheFu on 2013-10-30
> **CharlesA said:**
> I guess you could try cloning the VM and restoring it to a physical box, but that could cause problems with hardware mismatch. I'd probably go with "install KVM and mess with it" :p

Hardware mismatch doesn't usually matter to Linux.  SATA = SATA and a different MAC address will just make eth1.  If virtio was used for the partitions inside the /etc/fstab, then the vda -> sda and that's about it.  I think everything else is detected at boot.  I've moved HDDs between physical systems lots - it barely mattered.

Oh --- but be certain to remove the Guest Additions before moving.

---

### Post by CharlesA on 2013-10-30
> **TheFu said:**
> Hardware mismatch doesn't usually matter to Linux.  SATA = SATA and a different MAC address will just make eth1.  If virtio was used for the partitions inside the /etc/fstab, then the vda -> sda and that's about it.  I think everything else is detected at boot.  I've moved HDDs between physical systems lots - it barely mattered.

Done that with a few *nix boxes, so yep. Windows on the other hand... :roll:

---

