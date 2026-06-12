---
title: "Error creating VM in Xen"
date: 2008-03-21
forum: Virtualisation
---

### Post by medha on 2008-03-21
I get this error creating new domain:
medha@apple:/etc/xen$ sudo xm create -c d1-config vmid=1
Using config file "./d1-config".
Error: int argument required

My config file is: /etc/xen/d1-config
kernel = "vmlinuz-2.6.22-14-xen-D1"
ramdisk = "initrd.img-2.6.22-14-xen-D1"
memory = 64
name = "Domain-1"
vif = [ '' ]
disk = [ 'phy:sda5,sda5,w' ]
hostname= "vm%d" % vmid
root = "/dev/sda5 ro"
extra = "4"

Any suggestions?

---

