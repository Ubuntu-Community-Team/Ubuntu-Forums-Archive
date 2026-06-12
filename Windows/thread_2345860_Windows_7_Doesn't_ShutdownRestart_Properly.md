---
title: "Windows 7 Doesn't Shutdown/Restart Properly"
date: 2016-12-08
forum: Windows
---

### Post by midnite8 on 2016-12-08
I am having issues with my Windows 7 after removing dual boot of Ubuntu. I booted into Windows 7 startup repair and did a bootrec /fixmbr, /fixboot, /rebuildBCD. After that I went into the Disk Management to delete the Ubuntu partitions and shrank the size of the partitions back into the main Windows partition. 

Now after clicking Shutdown or Restart, it will say Shutting Down, then the monitor will turn black as if it was going to shutdown but the computer is still running. I tried to boot into Safemode and Shutdown from there but it just hangs at Shutting Down. 

Are there still remnants of Ubuntu somewhere that is preventing Windows from shutting down/restarting entirely?

---

### Post by oldfred on 2016-12-08
Windows needs a chkdsk on any NTFS partition resize. And that can take a while. Are you shutting down or restarting too quickly?

Your fixes should be the required ones, so then you are into other Windows repairs.

---

### Post by midnite8 on 2016-12-08
I will re-do the chkdsk as I stopped it at Stage 4 of 5(the longest duration). I am not shutting down/restarting too quickly.

---

### Post by midnite8 on 2016-12-08
What if I re-install a Dual Boot with wubi and see if that makes any difference? What is the proper way to uninstall the dual boot? Was my original steps of uninstallation incorrect?

---

### Post by oldfred on 2016-12-08
Wubi is now so obsolete, you should not even attempt to use it.
It has to be inside a working Windows install.

---

### Post by yancek on 2016-12-08
> What if I re-install a Dual Boot with wubi and see if that makes any  difference? What is the proper way to uninstall the dual boot?

Which brings up the question 'was the original install you are referring to a wubi install'?  If it was, there was no need to go through the process you did, removing a wubi install is explained at the wubi guide documentation site below.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If you had Ubuntu on it's own partition, the method you used and running chkdsk to completion would be the expected process.

---

### Post by midnite8 on 2016-12-08
I just completed the entire chkdsk on the 1TB drive, took a long time, but it made no difference. Computer still does not shutdown entirely after clicking Shut Down. Fans and everything still run.

---

