---
title: "Auto mount CD/DVD on insert?"
date: 2011-09-25
forum: Server Platforms
---

### Post by W. Irving on 2011-09-25
Is there a way to have optical media automatically mounted when inserted? I've cobbled together a bash script called by a few udev rules to mount/unmount USB mass storage devices, but can't see a way to do the same with CD/DVDs since udev appears oblivious to media changes.

---

### Post by W. Irving on 2011-09-25
> **zackwasa said:**
> Are you using a X Window? The automount is already implemented in Gnome.

Check these links:
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

Using Ubuntu Server. No window system, no hal. Usbmount uses udev, and udev by itself won't care about media change to a ODD. Now looking at udisks and the devmon wrapper. Will update thread if I find a solution.

Edit: Scratch devmon. Still needs x11. :(

---

### Post by Vegan on 2011-09-25
The CLI environment is not designed to automount anything, for security reasons

---

### Post by W. Irving on 2011-09-25
> **Vegan said:**
> The CLI environment is not designed to automount anything, for security reasons

Strange comment, as udev facilitates precisely this. :)

---

### Post by linux2001 on 2011-09-26
Check your /etc/fstab
/dev/cdrom	/media/cdrom	auto	ro,noauto,user,exec	0

---

### Post by W. Irving on 2011-09-26
> **linux2001 said:**
> Check your /etc/fstab
/dev/cdrom	/media/cdrom	auto	ro,noauto,user,exec	0 0

Merely configuring fstab with an entry for the ODD will not result in the media being mounted automatically when a disc is inserted, but thank you anyway. :)

I think I'm about to crack this, using udisks and a custom built daemon.

---

