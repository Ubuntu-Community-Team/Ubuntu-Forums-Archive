---
title: "[SOLVED] Server 8.04 fails to start inside a VirtualBox VM"
date: 2008-08-20
forum: Server Platforms
---

### Post by de0xyrib0se on 2008-08-20
After the installation the kernel fails to boot with the following message:

The kernel requires the following features not present on the CPU 0:6

RESOLUTION: Make sure you check off Enable PAE/NX which exposes your CPUs Physical Address Extensions to the guest OS, the Ubuntu server in this case. After that its smooth sailing.

---

### Post by MaindotC on 2008-08-27
Thanks for the help - works great for me now!  Star for you.

---

