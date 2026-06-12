---
title: "So, if I need my VB Win 7 hard drive to be larger ..."
date: 2014-09-19
forum: Virtualisation
---

### Post by Tom_ZeCat on 2014-09-19
... is the only way to delete my current VirtualBox Windows 7 install and start from scratch?  I've been looking in the settings and can't seem to find a way to increase the size of hard drive resources allocated.  

I thought 60 GB would be enough when I set this up.  It's surprising how quickly you can use it up.

---

### Post by TheFu on 2014-09-21
vboxmanage to increase the vhdd size, then using partitioning tools to increase the partition size.
Or
just add some more storage with a D: drive in another virtual hdd that is assigned to the VM - moving your c:/users to d:/users has many how-tos on the internet - also move any large data there ... or better onto network/hostOS storage (i.e. outside the VM).
Or
just create a larger vHDD and use disk cloning tools to migrate the partition from the smaller disk to the larger disk - fsarchive, dd, gparted, whatever.

---

### Post by Tadaen_Sylvermane on 2014-09-21
Adding another hard drive the easiest thing to do.

---

