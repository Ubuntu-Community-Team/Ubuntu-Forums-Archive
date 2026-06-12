---
title: "Boot Failure on Alpha-1"
date: 2014-08-02
forum: Ubuntu Development Version
---

### Post by crcarson on 2014-08-02
Continue to have boot failures on Utopic Unicorn.  Re-installed using the 8/1/14 daily build (think this is Alpha-1) and still unable to boot using upstart.  The boot progresses to a blank screen with the Ubuntu banner and stops.  Can get a limited function system up by ctl-alt-f1 and logining in and then startx. The auth.log shows an error message about pam_systemd failing but I thought the default boot is with upstart.  I can boot using systemd (adding init=/lib/systemd/systemd to the boot command) but my shared printer is not available.  Appears that cupsd is expecting upstart to be available but it is not.

Update: This boot problem is occuring on the Gnome Utopic build only.  Have the 8/3/14 build of Unity up and running without a boot problem.

---

### Post by syntaxerror74 on 2014-08-07
Aug 1 ? 

That would be Alpha **2**, most likely

> I can boot using systemd (adding init=/lib/systemd/systemd to the boot command)

Ouch. Sounds somewhat related to ...
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1351295](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1351295)

---

### Post by crcarson on 2014-08-20
Had been running 14.10 Unity until about a week ago.  After an update the Unity system fails to boot successfully, get a flashing screen of the desktop.  If the linux boot is changed to nomodeset or i915.modeset=0 the system will boot but desktop is cut off on the left and performs badly. Rebuilt the unity system from the 8/18 daily build. Here is my display device...

        *-display
             description: VGA compatible controller
             product: 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:fe400000-fe7fffff memory:d0000000-dfffffff ioport:cc00(size=8)

Any suggestion on changing the linux boot?  

Given up trying to get the gnome system to boot with either upstart or systemd.

---

### Post by jerrylamos on 2014-08-22
Sounds very much like the launchpad bug I've had:

[http://ubuntuforums.org/showthread.php?t=2240600](http://ubuntuforums.org/showthread.php?t=2240600)

Currently 14.10 Utopic 3.16.0-10 (really everything after 3.16.0-6) amd64 boot to desktop and cursor, no panels, on this Lenovo ThinkCentre 58p Intel Core 2 duo 3 gHz.

Oddly, 3.16.0-10 i386 32 bit boots O.K. most of the time.  Rarely gets the same failure....

---

