---
title: "XEN and VNC guests not starting up"
date: 2009-03-23
forum: Server Platforms
---

### Post by MasterMaxus on 2009-03-23
Hi All,

I have just installed Xen on my unbuntu hardy heron server, seems to have installed perfectly, now I'm trying to create a guest OS (windows2008). When I run the xm create configfile.cfg with SDL=1 and VNC=0 the guest starts up and appears in xm list, but when I try to do SDL=0 VNC=1 the guest never starts.

Any ideas why its doing this?
Also is XEN being moved away from due to citrix buying it?

My guest config file:

```

import os, re
arch = os.uname()[4]
if re.search('64', arch):
    arch_libdir = 'lib64'
else:
    arch_libdir = 'lib'

kernel = "/usr/lib/xen/boot/hvmloader"
builder='hvm'
memory = 1024

# Should be at least 2KB per MB of domain memory, plus a few MB per vcpu.
shadow_memory = 8
name = "devserver01"
vif = [ 'type=ioemu, bridge=xenbr0' ]
acpi = 1
apic = 1
disk = [ 'tap:aio:/mnt/hda1/xen/domains/devserver01.img,hda,w', 'tap:aio:/mnt/hda1/xen/images/windows2k8.iso,hdc:cdrom,r' ]

device_model = '/usr/' + arch_libdir + '/xen/bin/qemu-dm'

#-----------------------------------------------------------------------------
# boot on floppy (a), hard disk (c) or CD-ROM (d)
# default: hard disk, cd-rom, floppy
boot="cd"
sdl=0
vnc=1
vncconsole=0
vnclisten="0.0.0.0"
vncpasswd=''
vncunused=1

serial='pty'
usbdevice='tablet'

```

Logs (cat /var/log/xen/qemu-dm-1.log):
```

xs_read(): vncpasswd get error. /vm/0cddc3b8-3236-679c-516a-afa40dca6931/vncpasswd.
vncviewer execlp failed
char device redirected to /dev/pts/1
qemu_map_cache_init nr_buckets = 10000 size 3145728
shared page at pfn 3ffff
buffered io page at pfn 3fffd
Time offset set 0
Register xen platform.
Done register platform.
I/O request not ready: 0, ptr: 0, port: 0, data: 0, count: 0, size: 0

```

uname -a
```

Linux TeraServer 2.6.24-23-xen #1 SMP Mon Jan 26 03:09:12 UTC 2009 x86_64 GNU/Linux

```

---

### Post by MasterMaxus on 2009-03-24
Hi All,

I still haven't had any luck with this issue, Here are some additional details.

```

 Xen version 3.2.1-rc1-pre (buildd@buildd) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4

```

I have tried installing all the differnet VNC packages but none of those seem to have made a difference, Also is xen-ioemu part of the xen tools package? becuase if I try and install the one currently in the repoitory, it wantes to uninstall all of the parts of xen I currently have and go back to an older version?

I tried KVM, but when I tried to log into the machine all of the keys were messed up so A was F and D was J.

Should I give up on XEN and use VMware Server?

Thanks!
M

---

### Post by MasterMaxus on 2009-03-25
Thanks Useless Spammer for wasting my time and everyone elses...

-M

---

