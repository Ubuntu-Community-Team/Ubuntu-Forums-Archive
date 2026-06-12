---
title: "Possible to clone my notebook winxp as virtualbox image?"
date: 2009-01-27
forum: Virtualisation
---

### Post by carfield on 2009-01-27
Possible to clone my notebook winxp as virtualbox image? So that I don't have to reinstall everything?

---

### Post by istoff on 2009-01-27
Hi,

Quick answer yes.  I have been running my physical workstation install as a vm for the last 6 months or so without any incident.  I have even moved it between Linux and OSX when an emergency arose and I needed to use my wife's OSX machine.

Its been a while, but I will try and cover the steps and tools used.

1) Backup sensitive data on the xp image.
2) Follow the steps on [http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)
   This will prevent bluescreens related to the XP install not liking the virtual machine environment replacing the physical one
3) Try and free up as much space as you can on the windows install.
4) Download vmware converter from the VMware site and create a VMWARE image on an external usb drive.  You can actually do this while running the notebook xp you are converting.
5) Take the resulting .vmdk disk image and import it into a new virtualbox image.
6) On the settings tab of VirtualBox I have ACPI, IO-APIC, VTx-AMDv,PAE,3D enabled and NestedPaging disabled
7) I think I also had to ensure that the disk was SATA and not IDE in the Virtualbox configs.

After all of the above was done, tthe installation worked fine.

Note, you *may* have an activation issue with your XP serial no.  It might be an OEM DELL/HP/IBM number and won't work with Virtualbox.

Remember, if you don't follow steps 1 & 2 properly, this rest of this process is destined to fail!

Please post if you succeed.

Last tip.  I cloned a drive which had a ton of podcasts downloaded on it.  The resulting vm disk was about 40 GB.

To shrink it, I deleted the unnecessary files and booted of a livecd with a ghost-type application.

I created a new partition of 15 gb and ghosted (can't remember the tool I used) the .vmdk file to a Virtualbox disk image.  This wasn't compulsory, but I wanted to reclaim the space.

And like I said, I have tested the resultant image on Ubuntu, SUSE, OSX and even XP and it worked on all.

---

### Post by carfield on 2009-02-05
Look like it doesn't work for Encryption+ hard drive :-/

---

