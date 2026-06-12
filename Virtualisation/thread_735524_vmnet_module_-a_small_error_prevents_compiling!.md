---
title: "vmnet module -a small error prevents compiling!"
date: 2008-03-25
forum: Virtualisation
---

### Post by deepclutch on 2008-03-25
Hi,I have vmware-any-any-116 applied.still vmnet does not compile :( the error is as below:
```
Extracting the sources of the vmnet module.

Building the vmnet module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmnet-only'
make -C /lib/modules/2.6.24-zen4-praka1/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/zen-sources'
  CC [M]  /tmp/vmware-config3/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config3/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config3/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config3/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config3/vmnet-only/bridge.o
/tmp/vmware-config3/vmnet-only/bridge.c:35:8: error: "defined" cannot be used as a macro name
make[2]: *** [/tmp/vmware-config3/vmnet-only/bridge.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/zen-sources'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```
and the particular line that refers is 
```
#ifdef defined CONFIG_NET_RADIO || defined CONFIG_WLAN_80211
```
the file /tmp/vmware-config3/vmnet-only/bridge.c is attached here:
[http://pastebin.ca/957391](http://pastebin.ca/957391)

What should I do?
Thanks!

---

### Post by jlward4th on 2008-03-26
I was able to get past this problem by untaring vmnet.tar, fixing the broken file, retaring and overwriting the old vmnet.tar, then rerunning the runme.pl script.

But then I tried to start vmware and got an error about incorrect modules versions.  I then ran "sudo vmware-config.pl" recompiled the modules, restarted vmware, and then everything worked.  Strange.

-James

---

### Post by deepclutch on 2008-03-26
I got vmnet compiled somehow by trying an unofficial any-any patch.I have attached it here.
also,I have compiled a custom kernel from zen4 sources with gcc-4.2 .

This is unofficial one I got from some forum.(due credits to them!) originally from vmware-friends google list.

vmware-any-any-116 failed for me :( but this one worked.got lot of warnings when compiling modules(vmmon and vmnet),but finished successfully.

Thanks :):guitar:

---

### Post by sirgeek on 2008-04-21
> **deepclutch said:**
> particular line that refers is 
```
#ifdef defined CONFIG_NET_RADIO || defined CONFIG_WLAN_80211
```
the file /tmp/vmware-config3/vmnet-only/bridge.c is attached here:
[http://pastebin.ca/957391](http://pastebin.ca/957391)

What should I do?
Thanks!

The fix that I used was: 

tar -xf vmnet.tar 
vi vmnet-only/bridge
I changed #ifdef to #if
mv vmnet.tar vmnet.tar.orig
tar -cf vmnet.tar vmnet-only 

Then I ran the runme.pl and it compiled without any hassle and it appears to be running happily now.

---

