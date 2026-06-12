---
title: "domU keep crashing when install ubuntu as pv domU"
date: 2013-10-09
forum: Virtualisation
---

### Post by aleiphoenix on 2013-10-09
I'm using xen 4.3 with gentoo as dom0.


the kernel and ramdisk file is taken from [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/xen/](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/xen/)


the pv domU config file (according to the ubuntu xen documentation [https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen))


precise.cfg


```

name   = "precise"
kernel = "/xen/kernels/precise/vmlinuz"
ramdisk = "/xen/kernels/precise/initrd.gz"
# builder = "linux"
# bootloader = "pygrub"
memory  = 512
extra   = "debian-installer/exit/always_halt=true -- console=hvc0"
# device_model_override = "/usr/lib64/xen/bin/qemu-dm"
vif     = ['bridge=br0',]
# disk    = ['file:/xen/livecd/ubuntu-12.04-server-amd64.iso,xvdc:cdrom,r', 'phy:/dev/vg/precise_root,xvda,w', 'phy:/dev/vg/precise_swap,xvdb,w']
disk    = ['phy:/dev/vg/precise_root,xvda,w', 'phy:/dev/vg/precise_swap,xvdb,w']
# root    = "/dev/xvdc"
vfb     = ['type=vnc,vnclisten=0.0.0.0,vncunused=1']
vcpus   = 2
boot    = "d"


vnclisten = "0.0.0.0"


# on_reboot = 'restart'
# on_crash  = 'restart'

```


When i type "xl create precise.cfg", the domU started and simply get crashed.


and try to boot domU as hvm


```

builder = "hvm"

```


the iso booted very well, but report i686 cpu detected.


I'm running on an Intel Core 2 E7500 CPU , and VT-x is turned on.


I'm confused.


Someone could help me out, thanks!

---

### Post by tgalati4 on 2013-10-09
Perhaps there is an incompatibility between using gentoo as dom0.  Why can't you use Ubuntu 12.04 as dom0?

---

### Post by aleiphoenix on 2013-10-10
> **tgalati4 said:**
> Perhaps there is an incompatibility between using gentoo as dom0. Why can't you use Ubuntu 12.04 as dom0?

I doubt that :<

I've found same situation here[1], and tried with vmlinuz from 13.04 , it worked. So I assume that the 12.04 kernel file has something not compatible with xen PV domU?


[1]: [http://www.gossamer-threads.com/lists/xen/users/291715](http://www.gossamer-threads.com/lists/xen/users/291715)

---

### Post by tgalati4 on 2013-10-10
Understand that Xen has undergone a lot of development between  the release periods of 12.04 and 13.04.  The whole PV space has changed a lot in terms of basic framework and interaction between the kernel and virtual machines.  So, I'm not surprised that it doesn't work.

Xen 4.3 was released in July of 2013, so I presume it was built using later kernels than what is in 12.04.  [http://wiki.xenproject.org/wiki/Xen_4.3_Release_Notes](http://wiki.xenproject.org/wiki/Xen_4.3_Release_Notes)

There is a trend to push for support for ARM processors and that is happening with the latest kernels.

Also, some 32-bit hypervisor support was dropped according to the release notes.  That may account for the i686 hardware confusion and the fact that it doesn't work.

If you need to stick to 12.04 and gentoo, then try an earlier version of Xen (4.1.x or 4.2.x).  Sometimes you have to downshift to get things to work on older hardware.  The kernel images were from the April 2012 timeframe, so find a Xen image built around that time.  If that works, then keep loading newer Xen images until something breaks.  Then check the release notes and bug reports for that image to see what changed.  That might provide a clue.  It might be a simple fix to get 4.3 to work, or it may be a major framework change that will force you to run a newer kernel to get 4.3 to work.

[http://www.xenproject.org/downloads/xen-archives.html](http://www.xenproject.org/downloads/xen-archives.html)

Unfortunately, I've only dabbled with Xen 3.4 images on my server, so I can't really help beyond that.  (And that is ancient history now!  But at least it has a decent support community.)

---

