---
title: "LXC Guest Backup"
date: 2012-05-02
forum: Virtualisation
---

### Post by svtguy88 on 2012-05-02
I'm working on refining my LXC setup, and was wondering if there's a good way to back up an entire container?  I've got a few containers that supply different services (email, web, database), and backing up the entire container would be nice.

I tried simply copy/pasting the folder that contains the rootfs for the container, but it runs into a bunch of 'special files' that can't be copied.

Any ideas?

---

### Post by Dedoimedo on 2012-05-03
Did you try tarring before copying? Or rsync?
Did you try dd?
Dedoimedo

---

### Post by TheFu on 2012-05-21
I'm completely new to LXC, but I've been backing up paravirtual Xen and KVM image files for years. I'd think the techniques used there would work here too, but I **do not know for sure.**

**Steps**
* I shutdown the VM, 
* mount the image file from the hostOS, then 
* use rdiff-backup to backup everything. 
* On completion, umount and 
* restart the VM.  
Usually this happens in under 2-3 minutes.  rdiff-backup (and most other backup tools) let you selectively ignore certain file types when it makes sense - pipes, fifos, etc, so your backups don't get "stuck." 

For other backups, I remotely connect to the VM, shutdown the DB process, then run rdiff-backup for very specific file areas daily, and restart the DB process. This is much quicker, but doesn't backup the entire VM, just the application and DB parts. I do dump specific hardware and APT package lists into text files first. This provides a smaller backup overall, while letting someone rebuild the server quickly.  Use of non-repository package management (cpan, gems, etc) will make this more complex.  Dumping the DB contents to a flat file just before the backup would ensure uncorrupted DB data could be restored since backing up an open DB datafile is just asking for trouble later. This would not require the DB to be shutdown. I simply haven't bothered with the DB dump, since 2 minutes of downtime over night isn't any issue.

My experimentation with lxc is too new to set any of these up yet.  I think running lxc inside a KVM VM and using the hostOS as a pure VM platform is where I'm headed. Pros/cons?  

Another option would be to use LVM2 snapshots or ZFS, but these don't end with the backup files being easily accessible. That is a pretty big negative to me.

---

