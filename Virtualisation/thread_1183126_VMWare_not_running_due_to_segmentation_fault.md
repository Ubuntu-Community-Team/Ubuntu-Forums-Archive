---
title: "VMWare not running due to segmentation fault"
date: 2009-06-09
forum: Virtualisation
---

### Post by lpetersson on 2009-06-09
Hi,

When I try to run VMWare Workstation 6.51 from a terminal, I get the following error:

lars@Khaine:/media/D$ vmware &
[1] 7273
lars@Khaine:/media/D$ Xlib:  extension "RANDR" missing on display ":0.0".
Logging to /tmp/vmware-lars/setup-7276.log
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
/usr/bin/vmware: line 31:  7276 Segmentation fault      "$BINDIR"/vmware-modconfig --appname="VMware Workstation" --icon="vmware-workstation"

I'm using Ubuntu 9.04 x64.

When installing from the file VMware-Workstation-6.5.1-126130.x86_64.bundle I don't get any errors, and the installation exits successfully.

Any ideas or more info I need to provide?

I'm pretty new to Linux, so I can easily imagine that there's something I'm just not getting...

Cheerio,
Lars

---

### Post by lpetersson on 2009-06-11
Oh well, never mind. Switching back to Vista now. It'll be nice to use an OS that works...

---

### Post by codonnell on 2009-06-18
hello.

just ran into this same situation. you have to allow vmware to compile modules for your system. this is accomplished by (as root) deleting or renaming the modules directory and starting vmware. it will compile what it needs automatically.

# sudo mv /usr/lib/vmware/modules/binary /usr/lib/vmware/modules/binary.old
# sudo vmware

let vmware do its thing, then close it and reopen it normally.

best,

chuck

---

### Post by JimmyKatz on 2009-06-20
Confirmed.  That's the way to go.  Took me a while figuring this out.

---

### Post by jmaryinchina on 2009-06-20
Actually I got that same behaviour after upgrading to 2.6.28-13 kernel. The point if the building of the new modules is failing and, the following commands are doing a part of the job but not totally : 
[I]
sudo mv /usr/lib/vmware/modules/binary /usr/lib/vmware/modules/binary.old

sudo vmware-modconfig --console --install-all[/I]

At the end of this process we are still left with :

Stopping VMware services:
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Blocking file system                                                done
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual machine communication interface                             done
   Blocking file system                                                done
   Virtual ethernet                                                   failed


**That means no network for the virtual machines.**

---

