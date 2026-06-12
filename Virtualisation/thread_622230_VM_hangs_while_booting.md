---
title: "VM hangs while booting"
date: 2007-11-24
forum: Virtualisation
---

### Post by snaileater on 2007-11-24
My Hardware: Asus P5E mit Core Duo 2 und 2 GB Ram

I installed gutsy from the alternate-CD, then I installed xen using apt-get  install ubuntu-xen-server.

My xend-config.sxp looks like this:

```

# -*- sh -*-
(xend-relocation-server yes)
(xend-relocation-hosts-allow '^localhost$ ^localhost\\.localdomain$')
(network-script network-bridge)
(vif-script vif-bridge)
(dom0-min-mem 196)
(dom0-cpus 0)
(vncpasswd '')

```

Next I used xen-tools to create a VM. The resulting .cfg file:

```

kernel      = '/boot/vmlinuz-2.6.22-14-xen'
ramdisk     = '/boot/initrd.img-2.6.22-14-xen'
memory      = '128'
root        = '/dev/hda1 ro'
disk        = [ 'file:/var/xen-images/xLx-1.cfg-disk,hda1,w', 'file:/var/xen-images/xLx-1.cfg-swap,hda2,w' ]
#disk        = [ 'phy:lx5/xLx-1.cfg-disk,hda1,w', 'phy:lx5/xLx-1.cfg-swap,hda2,w' ]
name        = 'xLx-1.cfg'
vif         = [ 'ip=172.30.5.25' ]
vif         = [ 'bridge=xenbr0' ]
on_poweroff = 'destroy'
on_reboot   = 'restart'
on_crash    = 'restart'

```

The VM starts - no matter, if it uses file- or lvm-disks, but boot always hangs after short time. The last messages are:

```

[ 3274.824736] fuse init (API version 7.8)
[ 3274.829181] Failure registering capabilities with primary security module.
[ 3274.860491] thermal: Unknown symbol acpi_processor_set_thermal_limit
[ 3274.869629] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[ 3275.297529] kjournald starting.  Commit interval 5 seconds
[ 3275.297544] EXT3-fs: mounted filesystem with ordered data mode.

```

Any idea how to fix it?

---

### Post by afowler on 2007-11-25
Same problem... anybody?

---

### Post by frenzel on 2007-11-26
Hi,

i had the same problem with the same distribution too and spend hours on it. After digging in /etc/xen-tools/xen-tools.conf, looking around in the guestfilesystem, trying to mount it as ext2 and so on i just tested the kernelversion 2.6.19-4 and it worked out of the box. I even tried different guestsystems before without luck. So it seems to depend on the kernel version running on dom0. Maybe a bug?

So please boot the grubentry  looking like this one (/boot/grub/menu.lst) .

title           Xen 3.1 / Ubuntu 7.10, kernel 2.6.19-4-generic-amd64
root            (hd0,0)
kernel          /boot/xen-3.1.gz
module          /boot/vmlinuz-2.6.19-4-generic-amd64 root=UUID=847966de-6757-421c-b655-4e26914279a7 ro console=tty0
module          /boot/initrd.img-2.6.19-4-generic-amd64
#quiet

After that give xen-tools another chance. 

regards,

Jörn

---

### Post by afowler on 2007-11-26
Hi,

Thanks for the help...

I don't enough about Linux to create the correct syntax for a Grub file.  


Here is what I have now: (in dom0/baremetal)

[...SNIP...]
title           Xen 3.1 / Ubuntu 7.10, kernel 2.6.22-14-xen
root            (hd0,0)
kernel          /boot/xen-3.1.gz
module          /boot/vmlinuz-2.6.22-14-xen root=UUID=01fbe140-a127-46a9-8915-588b18ab5e46 ro console=tty0
module          /boot/initrd.img-2.6.22-14-xen
quiet

[...SNIP...]

I don't see any other files in /boot that use different version numbers. (cpu is a P3 1.0GHz)

Not sure what to try next.

---

### Post by snaileater on 2007-11-28
Hi Jörn,

my processor is an Intel Core Duo 2. Is it OK to use itle the "Xen 3.1 / Ubuntu 7.10, kernel 2.6.19-4-generic-amd64" kernel for it?

---

