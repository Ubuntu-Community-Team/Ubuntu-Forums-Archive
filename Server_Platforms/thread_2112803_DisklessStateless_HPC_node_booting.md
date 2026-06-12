---
title: "Diskless/Stateless HPC node booting"
date: 2013-02-05
forum: Server Platforms
---

### Post by Knight0wl on 2013-02-05
I'm working on that right now for a 50 node HPC using CentOs (looking at switching to Ubuntu) but I'm having real problems with getting a boot image -- well, booting.

Does anyone have some experience on a diskless/stateless boot solution with Ubuntu?

My objective is to install an image to a RAMdrive and run it from there. Since no data needd to be stored or kept, rebooting the system would be the same as a brand new system. Most of the literature I've been working with require an NFS or HTTP server to serve up a root FS. I'm looking to avoid that if possible - I was hoping to serve up the image as one big initramfs.img stuffed into RAM.

Here's my current detail:
Main system installed and working well: CentOS (2.6.32-279.19.1.el6.x86_64) but I'd use Ubu 12.10 or 12.04 if there's a recommendation either way)
PXEboot working well with tftp-server (0.49-7.el6)
DHCP is serving the PXE boot server information and the client is getting the menus and downloading the vmlinuz and whatever image file named.
dracut-kernel and -network installed (004-284.el6_3.1)

Here's my PXE detail:
kernel Node/vmlinuz
append initrd=Node/initramfs.img root=/dev/ram0 ramdisk_size=524288 rw ip=dhcp

The problem I'm hitting is that the root filesystem isn't mounting properly. I get following errors:
dracut warning: No root device "block:/dev/ram0" found.
or (depending on PXE variables)
RAMDISK: Couldn't find valid RAM disk image starting at 0
or
No filesystem could mount root

This has been driving me nuts! Does anyone have any advice? Is PXE/RAMdisk a pretty straight-forward thing with Ubuntu?

---

### Post by agb007 on 2013-03-20
I can tell you, how to do it for CentOS 5 and 6, but I would like to know how to do it in ubuntu.

In the Centos/RHEL/Fedora you can use the tool set: livecd-creator program from livecd-tools rpm.
You would need to create a whatever.ks kickstart file which will specify repos, rpms to install/include, network config, ...

then you execute:

LANG=C livecd-creator --config=/pathto/whatever.ks --fslabel=whatever --cache=/pathto/cache --tmpdir=/pathto/tmp

The result will be /pathto/whatever.iso

Then you do
livecd-iso-to-pxeboot /pathto/whatever.iso

As a result you will get in directory: /pathto/tftpboot/

the following set of file:

initrd0.img
pxelinux.0
pxelinux.cfg
vmlinuz0

The main ones you need to PXE boot are vmlinuz (kernel) and root fs (initrd0.img) 

I can give you a sample of the ks file, if you don't know what should be there, but if you google centos livecd-creator, you'll get one.

Then you configure the PXE server for network boot of the centos (pxelinux, dhcp, tftp, http,...) as usual.

---

### Post by cariboo on 2013-03-21
You want to have a look at [LSTP]("http://ltsp.org/"), it should do everything you need.

---

