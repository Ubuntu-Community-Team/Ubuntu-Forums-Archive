---
title: "Virtual box"
date: 2009-04-12
forum: Virtualisation
---

### Post by elleppahc on 2009-04-12
Can anyone help me to expand my disk space from 10Gb.
I thought that I chose expand in the set up. But now windows XP keeps telling me I am low on disk space and will not complete a task as a result.

---

### Post by Jose Catre-Vandis on 2009-04-13
Can't be done in VBox. You did choose expand in the setup, but that means it will expand from 0 upto 10gb. Three things you can do.

1. Easy

Clear out everything you really do not need in your XP VM. if it is just "content", you can always share a folder with your host.

2. Harder

Create a new hard disk and attach this to your VM, then you can move some stuff across.

3. Hard

3. Image your existing installation across to a new and bigger disk, then point your VM at it as the main vdi.

---

### Post by elleppahc on 2009-04-13
Hi Jose,
I would like to do no 2 or 3. Have you any guide to do this.
Thanks

---

### Post by Jose Catre-Vandis on 2009-04-14
Background reading
[http://forums.virtualbox.org/viewtopic.php?f=1&t=8046](http://forums.virtualbox.org/viewtopic.php?f=1&t=8046)

From elsewhere:
> 1. Create a new VDI of the desired size.
2. Boot GParted Live in a VM with both old and new VDIs attached.
3. Check in the partition editor (opened automatically after booting) what your old and new disk locations are. (It'll be something like /dev/hda and /dev/hdb.)
4. Copy contents from old to new disk. This will take a fair amount of time. (Here /dev/hdX is your original disk and /dev/hdY the new one).

Code: Select all Expand viewCollapse view
dd if=/dev/hdX of=/dev/hdY

* Warning: Make sure you do not mix up your input and output disks or you'll wipe all information from your original disk! (if= specifies the input and of= specifies the output.)
5. Reboot (again with GParted-Live). Now you should be able to increase the Windows partition size on the new disk.

Once you've verified the larger VDI boots Windows fine (and disk size is as you'd expect) you can of course delete the old smaller VDI.

and the VBox forums with lots of help :)

---

