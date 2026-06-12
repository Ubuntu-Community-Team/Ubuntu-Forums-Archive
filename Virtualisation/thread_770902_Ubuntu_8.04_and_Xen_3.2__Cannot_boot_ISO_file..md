---
title: "Ubuntu 8.04 and Xen 3.2 : Cannot boot ISO file."
date: 2008-04-27
forum: Virtualisation
---

### Post by vblondel on 2008-04-27
I try to install a Windows 2003 xen HVM server on my brand new Ubuntu Hardy installation but I always get the same error message :

Error: Device 5632 (vbd) could not be connected. losetup -r /dev/loop1 /home/iso/windows/w2k3_12.iso failed

Below the w2k3.hvm file.

import os, re
arch = os.uname()[4]
if re.search('64', arch):
    arch_libdir = 'lib64'
else:
    arch_libdir = 'lib'

kernel = "/usr/lib/xen/boot/hvmloader"
builder = "hvm"
memory = "384"
shadow_memory = 8
name = "W2K3"

vif = [ 'type=ioemu, mac=AA:BB:CC:DD:EE:00, bridge=xenbr0' ]

disk=[ 'phy:/dev/vgxen/lv-w2k3,ioemu:hda,w', 'file:/home/iso/windows/w2k3_12.iso,ioemu:hdc:cdrom,r']
device_model = '/usr/' + arch_libdir + '/xen/bin/qemu-dm'
boot = "d"
sdl=1
vnc=1
vncviewer=1
ne2000=0

My server is a Intel Core2Quad with 4Go Ram running last 8.04 amd64 distro. I already googled to find a solution and found :

  *  to replace file:// with tap:aio:// 
  *  moving iso file into /var/lib/xen/images
  * manually mounting the iso file 

but I cannot get it working. I get error message specified below or I cannot boot the iso image with a get 

  CDROM boot failure code : 0003
  Boot from CD-Rom failed 
  FATAL: Could not read the boot disk

can somebody help me making xen working correctly on last Ubuntu version.

thks
Vincent.

---

### Post by JoshCarter on 2008-04-28
Vincent,

There's some problems using file:/ specifications in your config file. See bugs here:

[https://bugs.launchpad.net/ubuntu/+source/xen-3.2/+bug/211726](https://bugs.launchpad.net/ubuntu/+source/xen-3.2/+bug/211726)
[https://bugs.launchpad.net/ubuntu/+source/xen-3.2/+bug/211728](https://bugs.launchpad.net/ubuntu/+source/xen-3.2/+bug/211728)

For the moment, the only way I've found to use CDROM is to manually run losetup to create the /dev/loop[n] device and then use a phy:/ specification in the guest config.

Best regards,
Josh

---

### Post by quad3d@work on 2008-05-02
I thought HVM requires the use of ioemu?

ubuntu-xen-server for Hardy don't have ioemu 3.2.... feisty and others that runs 3.1/0 have ioemu. So it works for you guys?

I would need to install Windows 2003 server soon....


EDIT ( 5-6-2008 )

Xen 3.2 don't need ioemu. Installed Win2K3 standard server and tested for couple a days. Windows admins were quite impressed with it, noting how fast and responsive it is.

---

