---
title: "Vm ware"
date: 2009-11-12
forum: Virtualisation
---

### Post by Drenriza on 2009-11-12
i've been using vm ware on my linux machine for a while now.
Windows xp.

Now i've upgrade to 9.10 and when i try running my vm ware it says it "unable to build kernel module" See log file /tmp/vmware-root/setup-12364.log for details.

I don't know what to do, hope some1 can help me.
Thanks on advance :KS

:EDIT:
Log Print - 
nov 12 10:05:09.967: app| Log for VMware Workstation pid=12364 version=6.5.0 build=build-118166 option=Release
nov 12 10:05:09.968: app| Host codepage=UTF-8 encoding=UTF-8
nov 12 10:05:09.968: app| Logging to /tmp/vmware-root/setup-12364.log
nov 12 10:05:11.232: app| Extracting the sources of the vmmon module.
nov 12 10:05:11.243: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.31-14-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.1

Kernel info:
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

---

### Post by Bunnybugs on 2009-11-12
Try to reinstall VMWare from the repositories... I'm not really sure wich version you are using, but you can find it on the bottom of your 'Applications' menu...

First remove it, and then reinstall it...

That should work... The VMWare files are seperated from the app, so they'll keep on existing

---

### Post by Drenriza on 2009-11-12
So even tho i uninstall and reinstall the virtualbox, my windows xp on that box with all its content wont change? or be deleted.

---

### Post by Bunnybugs on 2009-11-12
You could try to copy the Harddisk file to another location, to be sure that your stuff is save, after that, you can boot fresh again from that HDD

---

### Post by Drenriza on 2009-11-18
How can i check what version of vm ware workstation im using, without running the virtual machine. I cant run the virtual machine because i cant compile the program to the new ubuntu kernel version.

---

### Post by darco on 2009-11-18
You need to apply a patch for the new kernel. You need to head over to the vmware forums and search for it. Once patched, your modules will compile fine....



darco

---

