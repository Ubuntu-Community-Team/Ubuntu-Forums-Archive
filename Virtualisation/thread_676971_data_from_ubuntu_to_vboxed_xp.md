---
title: "data from ubuntu to vboxed xp"
date: 2008-01-24
forum: Virtualisation
---

### Post by mosaic2s on 2008-01-24
how to copy or access data from host os to guest os in vbox?
running gutsy as host os.

---

### Post by p_quarles on 2008-01-24
First, you'll need to install the "Guest Additions" on XP. This can be done from administration menu at the top of XP's Vbox window. This will download a disk image to XP, and you can then install the extras by double-clicking on the disk.

It will probably tell you that the extras fail the MS Logo Standards test. Nothing to worry about, just to be aware of.

Now, from the main Virtualbox control panel, you'll need to setup "shared folders" for XP. This will allow you to select a folder in your home directory to mount inside XP. Once you restart the VM, the shared folder will be available as a network drive (i.e., in Network Places from the Control Panel in XP).

---

### Post by mosaic2s on 2008-01-25
thank you for tip. cud share folders in vm. on restart, cud not locate in xp, under computers, under network places.

---

### Post by NovaAesa on 2008-01-28
> **mosaic2s said:**
> thank you for tip. cud share folders in vm. on restart, cud not locate in xp, under computers, under network places.
It should be under Network Places >>> Entire Network

---

### Post by mosaic2s on 2008-01-30
thank you for your advise.

however using
net use f: //vboxsvr/folder

f: is the networked drive - shows up the folder that was shared under linux. this happens at computer and not at network.

---

