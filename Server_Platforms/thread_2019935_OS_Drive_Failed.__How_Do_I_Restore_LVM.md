---
title: "OS Drive Failed.  How Do I Restore LVM?"
date: 2012-07-07
forum: Server Platforms
---

### Post by Falklian on 2012-07-07
Several months ago, I set up an old desktop computer with Ubuntu Server 11.10.  I have two 1TB drives set up with LVM and an 8GB USB drive set up with the OS.  Found out today that the USB drive failed completely, checked it with another computer and it's not recognized at all.  I'm about to head out to get another drive, but I wanted to be able to restore the LVM I had set up.  I did some searching, but was unable to find anything on restoring an LVM, only on setting it up from scratch or recovering a failed drive that was already set up for LVM.

If anyone could point me in the right direction, it would be much appreciated.  I have backups, but would only want to do this as a last resort, as all the data is still intact on functioning drives.

Thanks!

---

### Post by darkod on 2012-07-07
You should have no problem using the same LVM. This explains how you would activate and read it from live mode, to copy the data for example:
[http://quonn.wordpress.com/2010/12/01/how-to-mount-lvm-partition-on-ubuntu/](http://quonn.wordpress.com/2010/12/01/how-to-mount-lvm-partition-on-ubuntu/)

But in your case you don't need to specifically copy (rescue) this data, you only want to use it once you install ubuntu again.

After installing the OS, or during it, you can activate and mount the LVM easily. If you do it during OS installation, make sure you don't delete it. Or simply ignore it (leave it as not used) during OS install, and create an entry in /etc/fstab after that.

Which ever way, it will work.

---

### Post by Falklian on 2012-07-07
Thanks!  That worked perfectly!

---

