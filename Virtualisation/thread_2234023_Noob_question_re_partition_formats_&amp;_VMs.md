---
title: "Noob question re partition formats &amp; VMs"
date: 2014-07-12
forum: Virtualisation
---

### Post by ian49 on 2014-07-12
I'm going to have 64-bit Ubuntu running on my primary SSD with 64-bit Win 7 on the same drive as a virtual machine (using VMWare).

I'd like both Ubuntu and Win 7 (via the VM) to be able to access files on a 2TB secondary HDD and what I was wondering is whether there was a way they could both access files in the same partition on this secondary drive or would they need to have separate partitions formatted accordingly (msdos for Ubuntu and NTFS for Win 7)?

---

### Post by ian49 on 2014-07-12
Just to follow up on my previous post - I've now set up a Windows 7 VM on the SSD primary drive which is running Ubuntu. I had hoped that both the Win 7 VM and the Ubuntu host could access files on a secondary 2TB HDD.

Unfortunately, the Win 7 VM isn't aware of the existence of the secondary HDD. I then tried creating a shared folder on the HDD and edited the VM settings Shared Folder, selecting the shared folder I'd created. However, when running the VM I then get the following error message:

Cannot connect the virtual device sata0:1 because no corresponding device is available on the host.

So, at this point I'm stumped. Is there a way to achieve what I'm trying to do?

Any constructive help much appreciated.

---

### Post by mooreted on 2014-07-12
Did you look under Network Places?

[https://www.vmware.com/support/ws5/doc/ws_running_sharedfolder_viewing.html](https://www.vmware.com/support/ws5/doc/ws_running_sharedfolder_viewing.html)

---

### Post by mooreted on 2014-07-12
VmWare Player 6.0.3 build-1895310

What I did:

1. Select Windows 7 x64 virtual machine
2. Click "Edit virtual machine settings
3. Click "Options"
4. Click "Shared Folders/Always Enabled/Map as a network drive in Windows"
5. Click "Add"
6. Entered name and path to folder
7. Click "Save"

---

### Post by ian49 on 2014-07-12
> **mooreted said:**
> VmWare Player 6.0.3 build-1895310

What I did:

1. Select Windows 7 x64 virtual machine
2. Click "Edit virtual machine settings
3. Click "Options"
4. Click "Shared Folders/Always Enabled/Map as a network drive in Windows"
5. Click "Add"
6. Entered name and path to folder
7. Click "Save"

Those are the exact steps I took myself but I got the error that I mentioned in my previous post when I came to run the VM, i.e. Cannot connect the virtual device sata0:1 because no corresponding device is available on the host.

---

### Post by mooreted on 2014-07-12
That's odd, it worked perfectly for me and I have a Linux SSD drive and and NTFS secondary drive.

I assume the drive you are trying to access is mounted. Also, you don't actually connect to a drive, you connect to a folder on that drive. It's just like network file sharing. You can mount a folder as a virtual drive. You cannot access a whole drive.

---

### Post by mooreted on 2014-07-12
In the VM settings, do you have a CD-Rom attached? Try turning that off and see if you still get the same message.

---

### Post by ian49 on 2014-07-12
> **mooreted said:**
> That's odd, it worked perfectly for me and I have a Linux SSD drive and and NTFS secondary drive.

I assume the drive you are trying to access is mounted. Also, you don't actually connect to a drive, you connect to a folder on that drive. It's just like network file sharing. You can mount a folder as a virtual drive. You cannot access a whole drive.

Again, that's how I'm doing it. I have a shared folder on the secondary drive which is mounted. Frustratingly, the VM can see my external USB drives without any problem. It just appears to be the secondary SATA drive it can't see.

---

### Post by ian49 on 2014-07-13
Just to follow up to say after several further attempts I'm still getting the error message but the shared folder is now visible... hurrah!  I'm not sure why I'm getting the error message but I'll live with it :)

---

### Post by mooreted on 2014-07-13
That is weird, but I guess if it's working that's what really matters.

---

### Post by TheFu on 2014-07-14
Which VMware?  They make at least 6 different VM products.

For sharing files from a Linux host, use a Linux file system and use NFS or CIFS sharing over the network. The real file system doesn't matter, provided it is Linux (avoid NTFS, FAT-whatever, ... ).  The fact that the OS trying to access the files is running inside a VM means nothing - it isn't important.  I would avoid the "host file system sharing" stuff that desktop VM tools allow. IME, they suck, don't do file locking correctly and are just .... slow.  NFS blows them away.

If the drive is portable and might be connected to non-Linux systems directly, use NTFS.  Be prepared for occasional file corruption - maybe once every year or so. Also, always, always, "eject" the device or **umount** on Linux before unplugging it.  A clean system shutdown does what you need as well.

Linux has no issue accessing GPT/MBR partitions with any sort of file system, provided you load the correct drivers.  Regardless - avoid FAT or vfat - that file system needs to die, die, die.

Of course, YMMV on all these things. We all come from different backgrounds with different skills.

---

### Post by at_first_light on 2014-07-15
> **ian49 said:**
> 
Cannot connect the virtual device sata0:1 because no corresponding device is available on the host.


Sorry to hear you are having troubles. I hate it when things that **should work**, don't.

Your error is odd; I would expect to see an error like this when using direct partition/disk mounting to add a disk to the virtual machine, but not when using shared folders??? This error is especially weird because by default VMware Player (and presumably VMware Workstation, I'm not sure about other VMware products) uses SCSI to connect virtual drives on Windows 7 vms, not SATA. 

What VMware product are you using (Eg: VMware Player, VMware Workstation, and etc.)? In your vm's settings does it list any hard drives/cdrom drives as using SATA 0:1?

---

