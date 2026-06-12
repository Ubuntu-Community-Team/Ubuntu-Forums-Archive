---
title: "Virtualbox VM says &quot;Disk Read Error.  Press CTRL-ALT-DEL to restart&quot;"
date: 2010-04-01
forum: Virtualisation
---

### Post by diablo75 on 2010-04-01
A friend of mine recently did a complete reinstall of Ubuntu and I had him copy all the files (including hidden items) from his Home folder onto a couple external hard drives (with NTFS partitions on them, I think).  I'm not exactly sure how he re-added the machines to his inventory, but he did copy his .Virtualbox folder from his external drive back to his new Home folder.

Anyway, when I tried to start up one of his machines, it spit an error message out similar to this one:

> Failed to power up VM! Error info:
Medium '/home/matt/VMImages/WindowsXPSP3.vdi' is not accessible. Could not open the hard disk '/home/matt/VMImages/WindowsXPSP3.vdi'.

I went into the Machine settings to check and see what it was using for storage (assuming the path name was incorrect) and re-selected the vdi file for the virtual disk.  Also, not too sure what the problem might be, I added the user to the vboxusers group and changed the permissions for everything in the /.Virtualbox folder to be read/write accessible for all users.

The next time I booted, the VM started but this time in the VM display (virtual screen, if you will) was a box that said "A Disk Read Error Occurred.  Press CTRL-ALT-DEL to restart."  (like the attachment).

So I'm not sure what to do about this.  I always thought you could just copy and paste the ~/.Virtualbox folder from one Home folder to another and then install VB, then add the machines back in or they'd already be there...

---

### Post by diablo75 on 2010-04-02
Bump?

---

### Post by falconindy on 2010-04-02
The error message is accurate.

Delete and re-add the .vdi to the Virtual Media Manager, and then reassociate the disk with the VM under the 'Storage' tab for the VM.

---

### Post by Nausser on 2010-06-16
Did this work for you? I have a friend having the same issue. There is also an extra .vdi in the Hard Disks folder. I don't understand where it came from. The vdi I they have been using all along is in the proper folder. Nothing has changed. Does this coincide with what you were experiencing as well?

---

### Post by diablo75 on 2010-06-16
> **Nausser said:**
> Did this work for you? I have a friend having the same issue. There is also an extra .vdi in the Hard Disks folder. I don't understand where it came from. The vdi I they have been using all along is in the proper folder. Nothing has changed. Does this coincide with what you were experiencing as well?

It did work... and one of the weird things I noticed at the time was the vdi files we were trying to load into Virtualbox were truncated in file size.  What was supposed to be about 16 gigs was cut off at 4 gigs; in fact all the vdi files were.  Fortunately we went back to the external hard drive he originaly backed the machines up on to and re-copied the full size vdi files over.  We then, more or less, re-created the machines from scratch.  The key here is to make sure that Virtualbox's little inventory is cleared, or made "unaware", of the old VDI files.  It's kind of like the way it "stores" a small selection of recently used ISO files you've mounted to the CD/DVD device for a VM.  If you deleted one of those ISO files, you'll still see the file listed in the inventory, but you'll likely get an error message that tells you the file is missing, so you have to also delete that iso out of Virtualbox.

One of the snags I also ran into while removing the old VDI files was that one machine had associated itself with a VDI file that had snapshots saved, but the VDI file was named slightly different, and as a result, the machine didn't want to delete.  I had to open up some Virtualbox configuration file to change the name of the VDI file it wanted to point to for that machine to match up with one that it used to be associated with, and then delete it.  Or something like that.  It's been a while since I did this, but the only other alternative was to leave this broken VM in the Virtualbox inventory and rename it to something like "Broken VM, don't use".  But I managed to get rid of it eventually.

---

