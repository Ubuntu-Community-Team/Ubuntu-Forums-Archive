---
title: "Virtual Sever backups"
date: 2010-11-23
forum: Server Platforms
---

### Post by psychobyte on 2010-11-23
Hi,

 not sure if this is the right forum for this question but,

If I used xen,kvm,virtual box what are some strategies to backup the virtual host and guest machines?  

Any hints would be appreciated.

---

### Post by Irregular Joe on 2010-11-23
I use virtualbox, while it stores the virtual machine's disk images as .vdi files (a vdi file represents a physical disk to the vm), there are other configuration items that you need to keep for a guaranteed usable backup.  My backup strategy is to make a copy of the entire ~/.VirtualBox directory to another disk (or system).  Rsync works great for this.

Internal to the configuration files are lots of random ids for referencing the .vdi files, snapshots, and several other things you can't manually recreate.  It's complete, and can be restored with minimal hassle.


For a more complicated setup, I made the  ~/.VirtualBox directory a separate mount point in /etc/fstab, and replicate that with rsync to a second machine on my local network.  I recently lost my primary machine, but have been able to access my vm's via the second machine by pointing to the backup of my primary vbox directory.  It worked much more easily than I expected.

Hope this helps!

---

