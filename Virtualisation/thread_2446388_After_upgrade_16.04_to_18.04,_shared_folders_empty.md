---
title: "After upgrade 16.04 to 18.04, shared folders empty and gui window small"
date: 2020-06-29
forum: Virtualisation
---

### Post by david.karr on 2020-06-29
I had VirtualBox 6.0.4 and a Ubuntu 16.04 VM on my Win10 laptop.

Today, with help from an expert admin in my company who maintains the supported images, I upgraded this to VirtualBox 6.1.8 and Ubuntu 18.04.

What I'm left with after the upgrade are the following symptoms:
* My shared folders are all empty
* My window is tiny

I'm sure the reaction from most people would be that I haven't run the guest additions installer.  However, I have run it, many times now. The output doesn't indicate any error at all, and the admin sees no issue with it.

What is curious is that after running the GA installer, when I bring up the Files dialog to eject the GA disk, it also has my shared folders mounted. When I eject the GA disk, the shared folders remain. However, when I restart the VM, I still have a small window and my shared folders are empty.  The Files dialog no longer shows those mounts.

The output of the various ways of running the GA installer looks like this:
```
VirtualBox Guest Additions: Starting.
VirtualBox Guest Additions: Building the VirtualBox Guest Additions kernel
modules. This may take a while. VirtualBox Guest Additions: To build modules for other installed kernels, run
VirtualBox Guest Additions: /sbin/rcvboxadd quicksetup <version>
VirtualBox Guest Additions: or VirtualBox Guest Additions: /sbin/rcvboxadd quicksetup all
VirtualBox Guest Additions: Running kernel modules will not be replaced until the system is restarted
```

There are no obvious error messages that we can find.

---

