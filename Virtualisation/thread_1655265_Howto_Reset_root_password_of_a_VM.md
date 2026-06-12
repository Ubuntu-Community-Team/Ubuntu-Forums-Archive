---
title: "Howto: Reset root password of a VM"
date: 2010-12-29
forum: Virtualisation
---

### Post by HermanAB on 2010-12-29
Howdy,

I just wasted a couple hours of my life trying to reset the root password of a virtual machine. Trying to boot into Single user mode, just would not work. Eventually, I found a quite trivial method. VMware Player can mount the VM disk on the host and then you can edit the /etc/shadow file at your leisure.

Run VMware Player and Open the VM.
Click Edit Virtual Machine Settings, Hard Disk, Utilities (at the bottom) has an entry for Mount Disk.

Create a mount point:
$ sudo mkdir /mnt/vm

Now mount the Vm disk on this point.

Enter the mount point and go to /etc:
$ sudo vi /etc/shadow

Delete the root password between the first two colons and save the file:
 [esc]wq:

Now unmount the VM disk and boot normally.  Open a terminal in the VM and set the root password:
$ su
# passwd

La voila!

---

