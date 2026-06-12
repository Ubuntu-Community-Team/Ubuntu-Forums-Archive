---
title: "After running update and upgrade unable to detect VMs"
date: 2018-01-08
forum: Virtualisation
---

### Post by satimis on 2018-01-08
Hi all,

Host - Ubuntu 16.04 desktop on 120G SSD (including VirtualBox)
VMs - Ubuntu/debian/mints/windows etc on 1.8TB WD HD
VirtualBox

&#10219; apt-cache policy virtualbox```

virtualbox:
  Installed: 5.0.40-dfsg-0ubuntu1.16.04.2
  Candidate: 5.0.40-dfsg-0ubuntu1.16.04.2
  Version table:
 *** 5.0.40-dfsg-0ubuntu1.16.04.2 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages
        100 /var/lib/dpkg/status
     5.0.18-dfsg-2build1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages

```

Recently after running apt-get update and upgrade, VMs can't be detected.

Warning```

Runtime error opening '/media/satimis/c52984f7-6e0a-42c4-ab38-b4b5c5cc0bc82/VM_core8_VDI/viewtouch1/viewtouch1.vbox' for reading: -102(File not found.).
/build/virtualbox-n1JPUg/virtualbox-5.0.40-dfsg/src/VBox/Main/src-server/MachineImpl.cpp[740] (nsresult Machine::i_registeredInit()).
Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
MachineWrap
Interface: 
IMachine {f30138d4-e5ea-4b3a-8858-a059de4c93fd}

```

File -> Preference - General ->
Default Machine Folder```

/media/satimis/c52984f7-6e0a-42c4-ab38-b4b5c5cc0bc8/VM_core8_VDI

```
VRDP Authentication Library: VBoxAuth

The path is correct.

But on the Warning:```

Runtime error opening '/media/satimis/c52984f7-6e0a-42c4-ab38-b4b5c5cc0bc82/VM_core8_VDI/viewtouch1/viewtouch1.vbox' for reading: -102(File not found.).

```
the path is;```

/media/satimis/c52984f7-6e0a-42c4-ab38-b4b5c5cc0bc82/VM_core8_VDI/viewtouch1/viewtouch1.vbox'
```
b4b5c5cc0bc82 - '2' is added after 'b4b5c5cc0bc8"

Rename 'c52984f7-6e0a-42c4-ab38-b4b5c5cc0bc8' as c52984f7-6e0a-42c4-ab38-b4b5c5cc0bc82' ?

Please help how to fix the problem.  Thanks

Regards
satimis

---

### Post by deadflowr on 2018-01-08
I think it's mounted at the wrong location.
The additional #2 at the end is usual if you created a mount point and then the system tried mounting the partition.
To explain a little, if I have a partition labelled as vbox and then create a directory in /media for it like
/media/me/Vbox
if I mount in manually I can mount it at that location.
But if I allow the system to mount it with something like Files or Gnome-disks, then it will see that location as made and then create a new location with the 2 distinction.
and then you end up with /media/me/vbox2

Does that make sense?

---

### Post by satimis on 2018-01-08
> **deadflowr said:**
> I think it's mounted at the wrong location.
- snip -

I haven't changed anything.  After running apt update, apt upgrade and apt dist-upgrade it became such a situation.  Neither I have created a new mounting point.

satimis

---

