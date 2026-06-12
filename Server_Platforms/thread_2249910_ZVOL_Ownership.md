---
title: "ZVOL Ownership?"
date: 2014-10-25
forum: Server Platforms
---

### Post by serge12 on 2014-10-25
I'm setting up a server to use as a hypervisor

What I have so far is a light Ubuntu install, with ZFS, and Virtualbox + phpvbox to manage VM's once they've been created/configured. It works, but I'm at a minor snag.

I'm using zvols and vmdk pointers. There's a couple reasons for this, the first being that thin provisioned virtual disks don't seem to be recommended on zfs due to dynamic resizing adding i/o costs. Using zvols essentially allows me thin-provisioned storage, but also gives me the ability to do snapshots, and take advantage of other zfs features

The problem I've run into, is every time I start a VM, I have to manually reset the permissions on the ZVOL

After some research, I found this which seems like it would solve my problem
[http://wiki.complete.org/ZVolPermissionsWithUdev](http://wiki.complete.org/ZVolPermissionsWithUdev)

But now I'm trying to apply it, and I'm looking at the UDEV manpage and I'm just trying to make sure I'm not missing something here

If I have a zpool named vmstorage, If I get this correctly, I would add this line, assuming my vbox user is simply named vbox, and the group is vboxusers

KERNEL=="zd*" SUBSYSTEM=="block" ACTION=="add|change" PROGRAM="/lib/udev/zvol_id /dev/%k" RESULT=="vmstorage" OWNER="vbox" GROUP="vboxusers" MODE="0750"

but if I have additional zvols on the zpool for each vm, like the following

vmstorage/VM1
vmstorage/VM2
vmstorage/VM3

Do I need to add a line to the udev rule for each one like the following?

KERNEL=="zd*" SUBSYSTEM=="block" ACTION=="add|change" PROGRAM="/lib/udev/zvol_id /dev/%k" RESULT=="vmstorage/VM1" OWNER="vbox" GROUP="vboxusers" MODE="0750"
KERNEL=="zd*" SUBSYSTEM=="block" ACTION=="add|change" PROGRAM="/lib/udev/zvol_id /dev/%k" RESULT=="vmstorage/VM2" OWNER="vbox" GROUP="vboxusers" MODE="0750"
KERNEL=="zd*" SUBSYSTEM=="block" ACTION=="add|change" PROGRAM="/lib/udev/zvol_id /dev/%k" RESULT=="vmstorage/VM3" OWNER="vbox" GROUP="vboxusers" MODE="0750"

I tried both ways and reloaded the udev rules and when I shut down a test VM, I still had to manually reset the permissions, but looking at the page again, it states this will take effect the next time the pool is imported. so I assume I'm missing a reboot here which I can live with since I want to update virtualbox anyway and would need to shutdown all my VM's to do so

---

