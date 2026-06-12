---
title: "Vmware 6.5, 64 bit Ubuntu 8.10 host, &quot;Gio::Error&quot;"
date: 2008-11-02
forum: Virtualisation
---

### Post by sleemanj on 2008-11-02
After installing 6.5 on Ubuntu 8.10 without any cause for error (using the bundle install method), it does not start, Google doesn't reveal anything either except something in Russian which I can't understand.  Anybody have any ideas where I might find the error (the log mentioned below does not contain anything more useful than posted here).

    boffin@mortimer:~$ vmware
    Logging to /tmp/vmware-boffin/setup-15008.log
    filename: /lib/modules/2.6.27-7-generic/misc/vmmon.ko
    license: GPL v2
    description: VMware Virtual Machine Monitor.
    author: VMware, Inc.
    srcversion: 96CBF0250D0FB3F01BFBFFC
    depends:
    vermagic: 2.6.27-7-generic SMP mod_unload modversions
    filename: /lib/modules/2.6.27-7-generic/misc/vmnet.ko
    license: GPL v2
    description: VMware Virtual Networking Driver.
    author: VMware, Inc.
    srcversion: 6B003CA83CD311898EEFEFB
    depends:
    vermagic: 2.6.27-7-generic SMP mod_unload modversions
    filename: /lib/modules/2.6.27-7-generic/misc/vmblock.ko
    version: 1.1.2.0
    license: GPL v2
    description: VMware Blocking File System
    author: VMware, Inc.
    srcversion: 768B08090715A2D8C721BF3
    depends:
    vermagic: 2.6.27-7-generic SMP mod_unload modversions
    parm: root:The directory the file system redirects to. (charp)
    filename: /lib/modules/2.6.27-7-generic/misc/vmci.ko
    license: GPL v2
    description: VMware Virtual Machine Communication Interface (VMCI).
    author: VMware, Inc.
    srcversion: F400DF976CFE388EBC1A0A2
    depends:
    vermagic: 2.6.27-7-generic SMP mod_unload modversions
    filename: /lib/modules/2.6.27-7-generic/misc/vsock.ko
    license: GPL v2
    version: 1.0.0.0
    description: VMware Virtual Socket Family
    author: VMware, Inc.
    srcversion: EC2E0BE1F6FB039D1109ADB
    depends: vmci
    vermagic: 2.6.27-7-generic SMP mod_unload modversions
    filename: /lib/modules/2.6.27-7-generic/misc/vmmon.ko
    license: GPL v2
    description: VMware Virtual Machine Monitor.
    author: VMware, Inc.
    srcversion: 96CBF0250D0FB3F01BFBFFC
    depends:
    vermagic: 2.6.27-7-generic SMP mod_unload modversions
    terminate called after throwing an instance of 'Gio::Error'
    boffin@mortimer:~$ terminate called after throwing an instance of 'Gio::Error'

---

### Post by Davidhal on 2008-11-17
Had the exact same problem.

Running it as root using "sudo vmware" fixed it for me :D

---

### Post by awi on 2008-11-18
I have the same scenario/problem. 
Running the program with sudo, did not work either.

---

### Post by awi on 2008-11-19
I found this link, but still no luck :(

[http://communities.vmware.com/message/1089575#1089575](http://communities.vmware.com/message/1089575#1089575)

---

### Post by sleemanj on 2008-11-27
Oh man, I fixed it I think!

Here's what I did...

  Step 1: remove all the vmware modules from the kernel modules directory /lib/modules/[version here]/misc/

  Step 2: there were broken symlinks in my /usr/local relating to an old version of vmware, especially broken symlinks to icons which caused crashing (!!!), so I did this to remove all broken symlinks from /usr/local

for i in `find /usr/local -type l`; do [ -e $i ] || sudo rm $i; done

If you installed your old vmware somewhere else, maybe you have broken links there too, so perhaps do the same for /usr as a whole, if the links are broken they are no good to you anyway so I don't see any harm doing it in /usr.

  Step 3: I run vmware as:
  LD_LIBRARY_PATH=/usr/lib/vmware/lib:$LD_LIBARY_PATH VMWARE_USE_SHIPPED_GTK=yes vmware

It works so far! :guitar:

---

### Post by awi on 2008-12-08
Updates were made to this post

[http://communities.vmware.com/message/1118449#1118449](http://communities.vmware.com/message/1118449#1118449)

Now it works!
I have vmplayer 2.5.1 and ubuntu 8.10, full updated.

---

