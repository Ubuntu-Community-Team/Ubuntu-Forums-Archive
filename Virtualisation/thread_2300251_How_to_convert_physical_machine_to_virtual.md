---
title: "How to convert physical machine to virtual"
date: 2015-10-24
forum: Virtualisation
---

### Post by deepakdeshp on 2015-10-24
Hello,

I am running Ubuntu 14.04 physical server and Vmware workstation 12. How can I convert it to a virtual machine.
I want to try out different VMware guests. Which is the lightweight Linux distro supporting vmware so that I can try various Guest OS at the same time least loading my resources?

Thank you in advance.. Any help is appreciated.

---

### Post by TheFu on 2015-10-24
Don't know anything about VMware Workstation 12 and you didn't provide enough information to cover every detail needed to ensure a successful move.

However, Linux installs that are not dependent on fancy hardware/RAID/networking can often be cloned (backup/restore using any of the 100+ methods) into a virtual HDD for any virtualization tool. Then connect a live-boot Linux system, mount the storage location where /etc/ is located and fix a few items. The disk mount points, NIC udev/rules and grub for booting are usually all that is needed.  Of course, the details depend completely on the server and what virtual hardware is presented to the VM. When you know what you are doing, these changes take 30 seconds each-under  5min total, if the time to reboot and setup the VM including the VM storage aren't counted.

Be certain to remove any proprietary video drivers first.  It won't hurt if they are there, but those drivers won't be used inside a VM.

VMware used to have a tool that converted physical-to-virtual VMDKs.  Never used it for Linux and haven't used it for Windows since 2007-ish.

A general virtual machine setup guide: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) follow the general ideas to be happiest.  Works for all hypervisors.

---

### Post by deepakdeshp on 2015-10-24
Thank you that was a great information

---

