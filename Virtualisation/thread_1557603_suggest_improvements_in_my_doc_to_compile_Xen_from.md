---
title: "suggest improvements in my doc to compile Xen from sources"
date: 2010-08-21
forum: Virtualisation
---

### Post by tapas_mishra on 2010-08-21
Hi,
I am writing a small doc for people new to Xen.
to be able to compile Xen from sources on Ubuntu.

Please  suggest some improvements for this how to or mistakes that you
can point out.

Here we begin.
-------------------------------------------------------------------------


There is a technique of virtualization known as Xen and a hypervisor
known as Xen.
Like you have Firefox,Open Office,VLC and other softwares on your
computer similary
there is a software known as Xen.

Technically it is  a hypervisor.Which runs in your computer
and this is what will be able to help you to install Guest Operating
Systems on your computer.

The term Xen is often confusing to newbies since the
technique of virtualization is also known as Xen and the
hypervisor is also known as Xen.



To be able to use Xen you need to have a system which has Linux installed.
Install Xen on it.

1) Understand what is the difference between PVM and HVM.
2) Understand how to create guest operating system on Xen (hypervisor) using the technique of virtualization known as Xen.

This doc is for those people who want to compile the hypervisor Xen
for example you might have ever used vlc media player on your Linux box.

There you install it as

        yum install vlc or
        aptitude install vlc

If you download vlc from videolan website and do some steps as

        ./configure
        make
        make install
        then this is what is known as compiling from sources.

        This doc will describe this procedure.


So to begin with get a Linux computer.

When I began I used a P4 with 256 MB RAM.
Technicall Xen can run in this low configuration but you will
 save a  lot of troubles
if you use a machine with higher RAM.



=======================================================================================
```

sudo apt-get install iproute bridge-utils gcc make gettext
sudo apt-get install libcurl4-openssl-dev è openssl
sudo apt-get install python-dev zlib1g-dev bcc libsdl-dev pciutils-dev
è zlib

```First we will compile latest XEN Hypervisor from source.

Go to [http://www.xen.org/products/xen_source.html](http://www.xen.org/products/xen_source.html) and download the
latest XEN hypervisor from here.

My hardware specifications uname -a
```

Linux tapas-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17
01:57:59 UTC 2009 i686 GNU/Linux

```1. mkdir /home/tapas/xen
2. cd /home/tapas/xen
3. tar -xzf xen-4.0.0
4. cd xen-4.0.0
5. make xen
6. make install-xen
7. make tools
8. make install-tools

Build Vanilla kernel
Now we will build th PV_Ops Kernel. The Vanilla kernel source will be
downloaded from Jeremy's tree. Jeremy's git tree on [kernel.org]("http://kernel.org/")
contains the pv_ops dom0 patches. If we use Jeremy's tree then we do
not any extra patches to bind XEN with kernel source.

1. mkdir /home/tapas/linux
2. cd /home/tapas/linux
3. git clone git://[git.kernel.org/pub/scm/linux/kernel/git/jeremy/xen.git]("http://git.kernel.org/pub/scm/linux/kernel/git/jeremy/xen.git")
4. linux-2.6-xen
5. cd linux-2.6-xen
6. git checkout origin/xen/master -b xen/master
7. make menuconfig [see Note below]
8. make-kpkg clean
9. CONCURRENCY_LEVEL=N fakeroot make-kpkg --initrd
--append-to-version=-custom kernel_image kernel_headers
10. This will make the Ubuntu packages in the parent directory which
you can install

Note: Please choose the following xen specific optiions in kernel configuration.
```

Processor type and features ---> Subarchitecture Type (PC-compatible)
---> (X) Enable Xen compatible kernel
Bus options (PCI etc.) ---> 
[*] PCI support
[*] Xen PCI Frontend
[ ] Xen PCI Frontend
Debugging (NEW)
Device Drivers ---> XEN ---> 
[*] Privileged Guest (domain 0)
<*> Backend driver support (NEW)
<*> Block-device
backend driver (NEW)
<*> Block-device tap
backend driver (NEW)
<*> Network-device
backend driver (NEW)
(8) Maximum
simultaneous transmit requests (as a power of 2) (NEW)
[ ] Pipelined
transmitter (DANGEROUS) (NEW)
< > Network-device
loopback driver (NEW)
<*> PCI-device
backend driver (NEW)
PCI Backend
Mode (Virtual PCI) --->
[ ] PCI
Backend Debugging (NEW)
< >
TPM-device backend driver (NEW)
SCSI backend driver (NEW)
< > TPM-device backend driver (NEW)
SCSI backend driver (NEW)
Block-device frontend driver
Network-device frontend driver
Network-device frontend driver
acceleration for Solarflare NICs (NEW)
SCSI frontend driver (NEW)
<*> User-space granted page access driver (NEW)
<*> Framebuffer-device frontend driver (NEW)
<*> Keyboard-device frontend driver (NEW)
[*] Disable serial port drivers (NEW)
<*> Export Xen attributes in sysfs (NEW)
(256) Number of guest devices (NEW)
Xen version compatibility (4.0.0
and later) --->

```After xen confiuration, please make sure that .config has the
following parameter configuration:
```

* CONFIG_XEN=y
* CONFIG_XEN_MAX_DOMAIN_MEMORY=32
* CONFIG_XEN_SAVE_RESTORE=y
* CONFIG_XEN_DOM0=y
* CONFIG_XEN_PRIVILEGED_GUEST=y
* CONFIG_XEN_PCI=y
* CONFIG_PCI_XEN=y
* CONFIG_XEN_BLKDEV_FRONTEND=m
* CONFIG_NETXEN_NIC=m
* CONFIG_XEN_NETDEV_FRONTEND=m
* CONFIG_XEN_KBDDEV_FRONTEND=m
* CONFIG_HVC_XEN=y
* CONFIG_XEN_FBDEV_FRONTEND=m
* CONFIG_XEN_BALLOON=y
* CONFIG_XEN_SCRUB_PAGES=y
* CONFIG_XEN_DEV_EVTCHN=y
* CONFIG_XEN_BACKEND=y
* CONFIG_XEN_BLKDEV_BACKEND=y
* CONFIG_XEN_NETDEV_BACKEND=y
* CONFIG_XENFS=y

* CONFIG_XEN_NETDEV_BACKEND=y
* CONFIG_XENFS=y
* CONFIG_XEN_COMPAT_XENFS=y
* CONFIG_XEN_XENBUS_FRONTEND=m
Note: Please choose the following xen specific optiions in kernel configuration.

Processor type and features ---> Subarchitecture Type (PC-compatible)
---> (X) Enable Xen compatible kernel
Bus options (PCI etc.) ---> 
[*] PCI support
[*] Xen PCI Frontend
[ ] Xen PCI Frontend
Debugging (NEW)
Device Drivers ---> XEN ---> 
[*] Privileged Guest (domain 0)
<*> Backend driver support (NEW)
<*> Block-device
backend driver (NEW)
<*> Block-device tap
backend driver (NEW)
<*> Network-device
backend driver (NEW)
(8) Maximum
simultaneous transmit requests (as a power of 2) (NEW)
[ ] Pipelined
transmitter (DANGEROUS) (NEW)
< > Network-device
loopback driver (NEW)
<*> PCI-device
backend driver (NEW)
PCI Backend
Mode (Virtual PCI) --->
[ ] PCI
Backend Debugging (NEW)
< >
TPM-device backend driver (NEW)
SCSI backend driver (NEW)
< > TPM-device backend driver (NEW)
SCSI backend driver (NEW)
Block-device frontend driver
Network-device frontend driver
Network-device frontend driver
acceleration for Solarflare NICs (NEW)
SCSI frontend driver (NEW)
<*> User-space granted page access driver (NEW)
<*> Framebuffer-device frontend driver (NEW)
<*> Keyboard-device frontend driver (NEW)
[*] Disable serial port drivers (NEW)
<*> Export Xen attributes in sysfs (NEW)
(256) Number of guest devices (NEW)
Xen version compatibility (4.0.0
and later) --->

```After xen confiuration, please make sure that .config has the
following parameter configuration:
```

* CONFIG_XEN=y
* CONFIG_XEN_MAX_DOMAIN_MEMORY=32
* CONFIG_XEN_SAVE_RESTORE=y
* CONFIG_XEN_DOM0=y
* CONFIG_XEN_PRIVILEGED_GUEST=y
* CONFIG_XEN_PCI=y
* CONFIG_PCI_XEN=y
* CONFIG_XEN_BLKDEV_FRONTEND=m
* CONFIG_NETXEN_NIC=m
* CONFIG_XEN_NETDEV_FRONTEND=m
* CONFIG_XEN_KBDDEV_FRONTEND=m
* CONFIG_HVC_XEN=y
* CONFIG_XEN_FBDEV_FRONTEND=m
* CONFIG_XEN_BALLOON=y
* CONFIG_XEN_SCRUB_PAGES=y
* CONFIG_XEN_DEV_EVTCHN=y
* CONFIG_XEN_BACKEND=y
* CONFIG_XEN_BLKDEV_BACKEND=y
* CONFIG_XEN_NETDEV_BACKEND=y
* CONFIG_XENFS=y

* CONFIG_XEN_NETDEV_BACKEND=y
* CONFIG_XENFS=y
* CONFIG_XEN_COMPAT_XENFS=y
* CONFIG_XEN_XENBUS_FRONTEND=m

```

Please give your feedback about the above doc.

---

