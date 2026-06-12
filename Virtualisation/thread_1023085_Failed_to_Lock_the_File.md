---
title: "Failed to Lock the File"
date: 2008-12-27
forum: Virtualisation
---

### Post by fester225 on 2008-12-27
I just got Vmware-Server 1.08 running under Ubuntu 8.10. Now I can't start VMware, instead I get the diagnostic, "Failed to lock the file".

How do I get VMware running again?

---

### Post by Dedoimedo on 2008-12-28
Can you please post the full error you get when you try to run the server? Try running the server from the command line.
Dedoimedo

---

### Post by fester225 on 2008-12-28
From the desktop I get;

"Cannot open the disk '/var/lib/vmware/Virtual Machines/Windows XP Professional/Windows XP Professional.vmdk' or one of the snapshot disks it depends on.
Reason: Failed to lock the file."



There are no other diagnostics of any type from the terminal.
My virtual disk is now called, "Windows\ XP\ Professional.vmdk.WRITELOCK".

---

### Post by Dedoimedo on 2008-12-28
Did you create a snapshot and then delete any of the snapshot files?
Dedoimedo

---

### Post by fester225 on 2008-12-29
There are no snapshots.

---

### Post by geforce123 on 2008-12-31
> **fester225 said:**
> There are no other diagnostics of any type from the terminal.
My virtual disk is now called, "Windows\ XP\ Professional.vmdk.WRITELOCK".

No I don't think so, I had this problem before, and the .WRITELOCK is a file **created while** vmware is using the .vmdk file.

You can simply delete the .WRITELOCK file.  Look for a .READLOCK file too, you can delete it if you find it.

You must be root to delete those files.


[http://ubuntuforums.org/showthread.php?t=495301](http://ubuntuforums.org/showthread.php?t=495301)

---

### Post by fester225 on 2008-12-31
> **geforce123 said:**
> No I don't think so, I had this problem before, and the .WRITELOCK is a file **created while** vmware is using the .vmdk file.

You can simply delete the .WRITELOCK file.  Look for a .READLOCK file too, you can delete it if you find it.

You must be root to delete those files.


[http://ubuntuforums.org/showthread.php?t=495301](http://ubuntuforums.org/showthread.php?t=495301)


Thank you! That did it!

---

### Post by geforce123 on 2009-01-01
I'm glad to hear it :)

---

