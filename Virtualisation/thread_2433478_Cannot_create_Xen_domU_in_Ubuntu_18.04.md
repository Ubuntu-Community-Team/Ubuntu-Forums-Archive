---
title: "Cannot create Xen domU in Ubuntu 18.04"
date: 2019-12-19
forum: Virtualisation
---

### Post by Mikael_Niemel on 2019-12-19
Okay, so I tried Xen with my NAS box, and I got this error when trying to create a DomU:

```
root@foo:/etc/xen# xl create -c ubuntu18.cfgParsing config from ubuntu18.cfg
libxl: error: libxl_create.c:554:libxl__domain_make: domain creation fail: Operation not permitted
libxl: error: libxl_create.c:923:initiate_domain_create: cannot make domain: -3

```

Both the host and would be guest are Ubuntu 18.04. Any idea what could be causing this? Here's my config file:

```
# Guest namename = "Ubuntu 18LTS"
arch = "x86"
type = "pv"


# Kernel image to boot
kernel = "/var/lib/xen/images/ubuntu-netboot/bionic18LTS/vmlinuz"


# Ramdisk (optional)
ramdisk = "/var/lib/xen/images/ubuntu-netboot/bionic18LTS/initrd.gz"


# Kernel command line options
extra = "root=/dev/xvda1"


# Initial memory allocation (MB)
memory = 1024


# Maximum memory (MB)
# If this is greater than `memory' then the slack will start ballooned
# (this assumes guest kernel support for ballooning)
maxmem = 1024


# Number of VCPUS
vcpus = 1


# Network devices
# A list of 'vifspec' entries as described in
# docs/misc/xl-network-configuration.markdown
vif = [ 'bridge=xenbr0' ]


# Disk Devices
# A list of `diskspec' entries as described in
# docs/misc/xl-disk-configuration.txt
disk = [ '/dev/zvol/data/testvol,raw,xvda,rw' ]



```

---

### Post by Mikael_Niemel on 2020-01-01
Turns out it was caused by this: [https://lists.xen.org/archives/html/xen-announce/2012-06/msg00002.html](https://lists.xen.org/archives/html/xen-announce/2012-06/msg00002.html)

---

