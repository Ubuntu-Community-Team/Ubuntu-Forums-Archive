---
title: "File System Crash - Home Directory now a file"
date: 2011-04-02
forum: Server Platforms
---

### Post by naviathan on 2011-04-02
Background - A customers file server that has been online flawlessly for 2 years crashed last night.  Would not come back due to file system corruption.  I ran e2fsck on the root and got it to boot, however, now the home directory is showing up as a file so I can't login to the user account.  Any suggestions on changing this "file" back to a directory would be greatly appreciated.

---

### Post by iponeverything on 2011-04-02
See if testdisk can turn anything up.

what was filesystem? I once spent 3 days trying to unscramble a reiser3 filesystem without success. 

As for the directory showing up as a file..

Look for filesystem editors.. here might be good place to start: 

[http://tldp.org/HOWTO/Filesystems-HOWTO-6.html#ss6.18](http://tldp.org/HOWTO/Filesystems-HOWTO-6.html#ss6.18)

---

### Post by naviathan on 2011-04-02
I didn't think about testdisk, but can it be run specifically looking for a file?  I think I'm just going to recreate the directory and rebuild the users profile from scratch.

---

### Post by dtfinch on 2011-04-02
What does /etc/fstab look like?

---

### Post by naviathan on 2011-04-03
My fstab has nothing to do with it.  The file system is mounting rw.  It was just a corrupted folder from the system crash.  The /var/lib/gdm folder was corrupted as well.  So far so good I haven't found any other.  This gave me an excuse to upgrade the OS to 10.04 and makes some changes in my virtual machine I'd been meaning to make.

---

