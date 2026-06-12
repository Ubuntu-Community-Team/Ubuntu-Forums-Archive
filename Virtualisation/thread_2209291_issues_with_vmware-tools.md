---
title: "issues with vmware-tools"
date: 2014-03-05
forum: Virtualisation
---

### Post by ryan-wade1 on 2014-03-05
Hello, I'm using both xubuntu 14.04 beta, and xubuntu 13.10 in vmware workstation 10 on a windows 8.1 host. As of late I have been unable to get vmware-tools running. 

1. this issue appears on both versions (13.10 and 14.04) at the end of the install or when invoking vmware-config-tools.pl :

```

Creating a new initrd boot image for the kernel.
update-initramfs: Generating /boot/initrd.img-3.11.0-17-generic
initctl: Unknown job: vmware-tools-thinprint
Unable to start services for VMware Tools
 

Execution aborted.
```


2. this only on xubuntu 14.04 beta :

```
make: Entering directory `/tmp/modconfig-bllaQt/vmhgfs-only'
/usr/bin/make -C /lib/modules/3.13.0-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-15-generic'
  CC [M]  /tmp/modconfig-bllaQt/vmhgfs-only/backdoor.o
  CC [M]  /tmp/modconfig-bllaQt/vmhgfs-only/backdoorGcc32.o
  CC [M]  /tmp/modconfig-bllaQt/vmhgfs-only/bdhandler.o
  CC [M]  /tmp/modconfig-bllaQt/vmhgfs-only/cpName.o
  CC [M]  /tmp/modconfig-bllaQt/vmhgfs-only/cpNameLinux.o
  CC [M]  /tmp/modconfig-bllaQt/vmhgfs-only/cpNameLite.o
  CC [M]  /tmp/modconfig-bllaQt/vmhgfs-only/dentry.o
  CC [M]  /tmp/modconfig-bllaQt/vmhgfs-only/dir.o
  CC [M]  /tmp/modconfig-bllaQt/vmhgfs-only/file.o
  CC [M]  /tmp/modconfig-bllaQt/vmhgfs-only/filesystem.o
/tmp/modconfig-bllaQt/vmhgfs-only/file.c: In function ‘HgfsOpen’:
/tmp/modconfig-bllaQt/vmhgfs-only/file.c:685:27: error: incompatible type for argument 3 of ‘HgfsSetUidGid’
                           current_fsuid(), current_fsgid());
                           ^
In file included from /tmp/modconfig-bllaQt/vmhgfs-only/file.c:46:0:
/tmp/modconfig-bllaQt/vmhgfs-only/fsutil.h:92:6: note: expected ‘uid_t’ but argument is of type ‘kuid_t’
 void HgfsSetUidGid(struct inode *parent,
      ^
/tmp/modconfig-bllaQt/vmhgfs-only/file.c:685:27: error: incompatible type for argument 4 of ‘HgfsSetUidGid’
                           current_fsuid(), current_fsgid());
                           ^
In file included from /tmp/modconfig-bllaQt/vmhgfs-only/file.c:46:0:
/tmp/modconfig-bllaQt/vmhgfs-only/fsutil.h:92:6: note: expected ‘gid_t’ but argument is of type ‘kgid_t’
 void HgfsSetUidGid(struct inode *parent,
      ^
make[2]: *** [/tmp/modconfig-bllaQt/vmhgfs-only/file.o] Error 1
make[2]: *** Waiting for unfinished jobs....
/tmp/modconfig-bllaQt/vmhgfs-only/filesystem.c: In function ‘HgfsInitSuperInfo’:
/tmp/modconfig-bllaQt/vmhgfs-only/filesystem.c:234:15: error: incompatible types when assigning to type ‘uid_t’ from type ‘kuid_t’
       si->uid = current_uid();
               ^
/tmp/modconfig-bllaQt/vmhgfs-only/filesystem.c:240:15: error: incompatible types when assigning to type ‘gid_t’ from type ‘kgid_t’
       si->gid = current_gid();
               ^
make[2]: *** [/tmp/modconfig-bllaQt/vmhgfs-only/filesystem.o] Error 1
make[1]: *** [_module_/tmp/modconfig-bllaQt/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-15-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/modconfig-bllaQt/vmhgfs-only'

The filesystem driver (vmhgfs module) is used only for the shared folder 
feature. The rest of the software provided by VMware Tools is designed to work 
independently of this feature.
```


any help would be appreciated

---

### Post by lisati on 2014-03-05
*Thread moved to **Virtualisation**.*

---

### Post by Simon_WM on 2014-03-05
Hi Ryan, 

Normally when I install VMware-tools on Ubuntu, I do this:


sudo -s

mount /dev/media /media/cdrom

ls /media/cdrom (check its mounted)

tzxf /media/cdrom/vMwareTools.x.x.x-xxxx.tar.gz -C /tmp/

cd /

cd tmp

cd vmware-tools-distrib

./vmware-install.pl -d

and reboot and VMware  tools is installed.

VMware KB: [http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1022525](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1022525)

---

### Post by ryan-wade1 on 2014-03-07
Hello,
I've tried installing vmware tools a number of different ways. unfortunately this suggestion does not work either. The same two errors I posted above still appear

---

### Post by Simon_WM on 2014-03-09
What happens on a fresh install of Ubuntu Server?

---

### Post by newbie2244 on 2014-03-10
What system are you on? Does your system (BIOS) support vitualization? If so, be sure that you've enabled it. See    [http://virt-tools.org/learning/check-hardware-virt/ ](http://virt-tools.org/learning/check-hardware-virt/ )

---

### Post by mike.emery on 2014-03-11
I've seen this type error before with Ubuntu (slight variation), and am currently seeing it now with Fedora 20 (kernel 3.13.6-200).
VMWare issued a new version of the tools that resolved the problem after a few months.
Last time, I was able to use the tool patcher from here: [https://github.com/rasa/vmware-tools-patches](https://github.com/rasa/vmware-tools-patches)

Unfortunately, it doesn't seem to be helping at all for this problem.

---

### Post by ryan-wade1 on 2014-03-22
```
-----------------------------------------------
System Information
-----------------------------------------------
Machine name: OK_COMPUTER
Operating System: Windows 8.1 Pro 64-bit (6.3, Build 9600) (9600.winblue_gdr.131030-1505)
Language: English (Regional Setting: English)
System Manufacturer: Gateway
System Model: NV57H
BIOS: InsydeH2O Version V1.12
Processor: Intel(R) Core(TM) i3-2330M CPU @ 2.20GHz (4 CPUs), ~2.2GHz
Memory: 8192MB RAM
------------------------------------------------
Supporting Advanced Intel Processor Technologies
------------------------------------------------
Intel(R) Virtualization Technology                     Yes
Intel(R) Hyper-Threading Technology                Yes
Intel(R) 64 Architecture                                      Yes
Intel(R) Enhanced SpeedStep Technology         Yes
Intel(R) Advanced Vector Extensions                 Yes
Intel(R) VT-x with Extended Page Tables           Yes
------------------------------------------------
```

[http://www.intel.com/support/processors/tools/piu/sb/CS-014921.htm](http://www.intel.com/support/processors/tools/piu/sb/CS-014921.htm)

---

### Post by houstonbofh on 2014-03-23
I have actually had much better luck with open-vm-tools.  They install cleaner, and seem more stable.

---

### Post by derekh4 on 2014-04-29
I had this same issue.  I was running VMplayer 6.0.1 which used VMware-Tools-9.6.1.  When I upgraded to VMplayer 6.0.2 with VMware-Tools-9.6.2 the HGFS mounts worked fine again.  Give that a shot.

---

