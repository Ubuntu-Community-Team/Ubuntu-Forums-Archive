---
title: "VirtualBox can't find existing VMs"
date: 2008-06-08
forum: Virtualisation
---

### Post by RTrev on 2008-06-08
I had 8.04 installed, and installed VirtualBox from the repositories.  I needed to go back and get the appropriate kernel driver, as somehow that dependency got overlooked, I guess.

Everything was working well, and I had changed my preferences so that my VDI and Machines were stored out on a big RAID-1 data array.

When I reinstalled Ubuntu 8.04 with a clean install after its release, I reinstalled VirtualBox, again had to choose the correct kernel driver, set my preferences to the same directories I had used before, added the user to the vboxusers group, but now VirtualBox can't see any of the old, previously created, VMs.

The VDI and Machines directories are set as they were before, and the VirtualBox app comes up and runs fine, but something is missing.  I'm thinking it might be VRDPAuth, which I don't know what to do with and don't recall ever having to change before.  I'm not even sure what it is.  A quick search of my file system shows no such file or directory anywhere.

Do I need to re-create my VMs, or is there some way to tell VirtualBox how to use them?

Thanks!
Bob

---

### Post by niteshifter on 2008-06-08
Hi,

It's not VRDPAuth - that's security (keys) for Remote Desktop Protocol. What's missing is ~./VirtualBox/VirtualBox.xml. This file "describes" the linkage between items in the Machines folder and .vdi files in the VDI folder. If you have a backup of the previous, pull it from there. As long as paths are exactly the same, the retrieved copy will work. If paths are different you need to edit the VirtualBox.xml file.

No backup? Then all you can do is use VBox' Virtual Disk Manager to add the various .vdi files back. IIRC you'll have to fiddle with each VM's configuration.

---

### Post by Unix_Slayer on 2008-06-08
My problem is creating the vboxdrv. I followed the install carefully, but to no avail.

---

### Post by RTrev on 2008-06-08
> **niteshifter said:**
> Hi,

It's not VRDPAuth - that's security (keys) for Remote Desktop Protocol. What's missing is ~./VirtualBox/VirtualBox.xml. This file "describes" the linkage between items in the Machines folder and .vdi files in the VDI folder. If you have a backup of the previous, pull it from there. As long as paths are exactly the same, the retrieved copy will work. If paths are different you need to edit the VirtualBox.xml file.

No backup? Then all you can do is use VBox' Virtual Disk Manager to add the various .vdi files back. IIRC you'll have to fiddle with each VM's configuration.

Thanks!  Plenty of backups, just didn't have a clue what to restore.  <g>

Appreciate the tip!!

---

