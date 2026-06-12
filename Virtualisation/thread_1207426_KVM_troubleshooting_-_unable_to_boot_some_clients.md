---
title: "KVM troubleshooting - unable to boot *some clients*"
date: 2009-07-08
forum: Virtualisation
---

### Post by freakalad on 2009-07-08
This is an odd one.

I'm want to start testing more advanced functionality, like hot/live-migration, clustering, HA, etc., so I've introduced a second machine into the mix.

2 system:
* laptop, MBP SR 3.1, dual-core, Jaunty-64 w VT
* desktop/server, quad-core, Jaunty-64 w VT

* The laptop's working fine & all clients gel OK. KVM version "1:84+dfsg-0ubuntu12"
* The server is acting up (details to follow). KVM version "1:84+dfsg-0ubuntu11" (why this discrepancy, I don't know...)

So, the laptop's OK, so I'll leave it out of the equation for the time-being.

On the server/desktop, I can start up some clients, like xp & 2003, but not others, like vista & 2008. BIOS boots up & the screen is simply black.
This holds true for both 32- & 64-bit clients, via libvirt or KVM CLI.
If copy & run these images on the laptop, they all work fine.

The simple KVM command I user to start up the clients are (nothing special here):
```
sudo kvm -hda $WINOS.img -m 1024 -boot c -vga std
```
where $WINOS is the respective OS's

When the problematic machine was still Hardy-64, it worked fine, but now those very same images I've created on my older system version are no longer working, which is very, VERY bad indeed (so much for abstraction...). 
I'm now using newly-created system images, to at least eliminate that as a cause.

I've (at least twice) tried removing & purged the VM services & tried removing ALL traces of the KVM/libvirt installation:
```
sudo aptitude purge kvm libvirt-bin ubuntu-vm-builder qemu bridge-utils python-virtinst virt-image virt-manager virt-viewer uml-utilities virsh kvm_intel ubuntu-virt-server virtio
```
& deleted the appropriate log locations & users & groups

Rebooted & installed the Ubutnu VM host via tasksel.
Followed instructions as provided by the Ubuntu KVM guide.

Unfortunately, KVM does not offer much in the way of verbose interaction, so I have absolutely NO idea that KVM is up to, or why it's failing on these clients on this system.

Added the following lines to my /etc/syslog.conf :
```
kvm.*		/var/log/kvm
libvirt.*	/var/log/libvirt
```
& created the corresponding resources & made sure they where writable.

Still nothing....

So, I have 2 different VT-capable multi-64-core machines, running near-identical OS's, fully-updated/patched Jaunty-64, behaving differently, and I have little to no logging info to by

Any help would be appreciated, or an indication that this is a but that is being attended to.

Thanks

- J

---

### Post by freakalad on 2009-07-08
Created a script to quickly fire up the image & provide me whatever logging I can get: (pretty ghetto, but does the trick)
```

#!/bin/bash

IMAGEFILE=$1
MEMSIZE=$2
MEMDEFAULT=1024
VIDDEFAULT="std"
TODAY=$(date +%Y%m%d)

if [ ! -n "$MEMSIZE" ]; then
  MEMSIZE=$MEMDEFAULT
fi
 
if [ ! -n "$1" ]; then
  echo "no image specified"
else
  echo "starting up KVM: $IMAGEFILE, RAM= $MEMSIZE MB "
  kvm -hda $IMAGEFILE -m $MEMSIZE -vga $VIDDEFAULT -boot c 1>>$IMAGEFILE.$TODAY.log 2>>$IMAGEFILE.$TODAY.err &
  watch -n1 "tail $IMAGEFILE.$TODAY.*"
fi

```

Still not getting any details out re what's happening (& dmesg isn't much help).

How does one then go about debugging/troubleshooting KVM?

---

### Post by freakalad on 2009-07-09
Had enough, so scratched machine & re-installed OS (mint this time).
Pretty simple proposition, since /home & VM images are on patritions seperate from rest

Seems to have resolved the issue, but would still like to know what went on & how to resolve it...

logs...logs...logs...

---

