---
title: "Vmware server, windows xp, very slow start"
date: 2008-08-03
forum: Virtualisation
---

### Post by Zalbor on 2008-08-03
I'm using vmware server (not the latest version, but the one before it: 1.0.5) with a windows xp guest, on 8.04.
Windows is installed and activated, vmware tools is installed also.

The problem is that every time the VM starts, *after* the xp user is logged in, everything goes realllllly sloooooowly. All this time, the vmware icon has the red sign over it: vmware tools is not running.
After several minutes (at least 5) the vmware icon goes normal and everything in the system runs normally (as far as I can tell).
Shutting down xp also takes a long time.

I've installed XP before, on the same computer, using an older vmware server version, and everything worked fine then. But I deleted the VM and have created a new one to start over.

Can you help me with any suggestions? 5 minutes for the system to be usable every time it starts is too long...

---

### Post by KatBuntu on 2008-08-04
Have you checked the amount of RAM you are giving to the XP? it could be low!. Otherwise if you don't want to wait for the virtual machine to start, you can set it's status to paused, the next time you start, it will begin from the point you stopped.

---

### Post by Zalbor on 2008-08-04
The RAM is more than the recommended amount, I gave it 1024MB (the computer has 2GB). It's the same as last time (I don't plan to have many things running on the host when using it).
As for the pausing, that's what I did last time, but installing things in windows often requires a reboot...

---

### Post by LinuxRocks713 on 2008-08-04
Your virtual Windows has 1GB memory and is slow? 64MB memory is even slower!

---

### Post by Zalbor on 2008-08-04
It seems to me that the problem is caused by vmware tools. Before it tries to load and after it has loaded everything is fine, but when it's loading nothing works and it takes a long time.
I did try to repair the tools installation, but nothing changed.

---

