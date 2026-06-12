---
title: "VMware 7 Ubuntu 11.04 64-bit PLEASE HELP"
date: 2011-08-04
forum: Virtualisation
---

### Post by llarsen on 2011-08-04
I am trying to install VMware Workstation 7 on Ubuntu 11.04 64-bit. I have read a bunch of peoples posts on trying to get it to work but it just will not do it. I got past the issue where it was asking for the linux-headers-2.6.38-10-generic, and now it starts loading the "Kernel Module Updater" and then fails on the first step (Virtual Machine Monitor) and it throws me an error saying:

"Unable to build kernel module.

See log file /tmp/vmware-root/setup-19175.log for details.

then i check that log and it says that it cant compile the vmmon module, and i cannot for the life of me find any information on this... does anybody have any idea why this isnt working? PLEASE HELP! I love ubuntu, but if i cannot get VMware working i may be forced to go back to windows, since there are some applications that i need. --SEE LOG BELOW--

THANK YOU IN ADVANCE!:)


Aug 04 20:10:48.668: app-139962148480800| Log for VMware Workstation pid=17982 version=7.0.0 build=build-203739 option=Release
Aug 04 20:10:48.668: app-139962148480800| The process is 64-bit.
Aug 04 20:10:48.668: app-139962148480800| Host codepage=UTF-8 encoding=UTF-8
Aug 04 20:10:48.668: app-139962148480800| Logging to /tmp/vmware-root/setup-17982.log
Aug 04 20:10:48.793: app-139962148480800| modconf query interface initialized
Aug 04 20:10:48.794: app-139962148480800| modconf library initialized
Aug 04 20:10:48.818: app-139962148480800| Your GCC version: 4.5
Aug 04 20:10:48.823: app-139962148480800| Your GCC version: 4.5
Aug 04 20:10:48.832: app-139962148480800| Your GCC version: 4.5
Aug 04 20:10:48.845: app-139962148480800| Your GCC version: 4.5
Aug 04 20:10:48.855: app-139962148480800| Your GCC version: 4.5
Aug 04 20:10:48.881: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:48.883: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:48.885: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:48.887: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:48.889: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:48.902: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:48.904: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:48.906: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:48.908: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:48.909: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:48.913: app-139962148480800| Your GCC version: 4.5
Aug 04 20:10:48.922: app-139962148480800| Your GCC version: 4.5
Aug 04 20:10:48.951: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:48.953: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:48.955: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:48.957: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:48.959: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:48.963: app-139962148480800| Your GCC version: 4.5
Aug 04 20:10:48.972: app-139962148480800| Your GCC version: 4.5
Aug 04 20:10:49.009: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:49.011: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:49.013: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:49.015: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:49.017: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:49.482: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:10:49.482: app-139962148480800| Building module vmmon.
Aug 04 20:10:49.516: app-139962148480800| Extracting the sources of the vmmon module.
Aug 04 20:10:49.551: app-139962148480800| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.38-10-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.5.2
Aug 04 20:10:51.601: app-139962148480800| Failed to compile module vmmon!
Aug 04 20:14:55.082: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:14:55.084: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:14:55.086: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:14:55.088: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:14:55.090: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:14:55.095: app-139962148480800| Your GCC version: 4.5
Aug 04 20:14:55.105: app-139962148480800| Your GCC version: 4.5
Aug 04 20:14:55.145: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:14:55.147: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:14:55.149: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:14:55.151: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:14:55.153: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:14:55.321: app-139962148480800| Trying to find a suitable PBM set for kernel 2.6.38-10-generic.
Aug 04 20:14:55.322: app-139962148480800| Building module vmmon.
Aug 04 20:14:55.322: app-139962148480800| Extracting the sources of the vmmon module.
Aug 04 20:14:55.334: app-139962148480800| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.38-10-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.5.2
Aug 04 20:14:56.163: app-139962148480800| Failed to compile module vmmon!

---

### Post by llarsen on 2011-08-17
no one knows?

---

### Post by Jake.Debord on 2011-08-17
> **llarsen said:**
> no one knows?


Check this link out:
[http://forums.opensuse.org/english/get-technical-help-here/applications/456059-vmware-player-opensuse-11-4-cannot-compile-module-vmmon.html](http://forums.opensuse.org/english/get-technical-help-here/applications/456059-vmware-player-opensuse-11-4-cannot-compile-module-vmmon.html)

Please report back if that helps or not.

---

