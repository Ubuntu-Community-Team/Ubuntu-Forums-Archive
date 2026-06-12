---
title: "Xen on 8.04"
date: 2008-04-26
forum: Server Platforms
---

### Post by venzen on 2008-04-26
When I create a DomU with xen-tools via xen-create-image and then try to run it I get the following error:

```
Error: Device 769 (vbd) could not be connected. losetup /dev/loop0 /mnt/xenimages/domains/linux1/swap.img failed
```

Anybody else found this? I have been using Xen since Dapper and this is the first time I get this error. Even Google does not yield any results with the above error. losetup works if run manually but never with 

xm create linux1.cfg -c 

(or any other DomU for that matter) under Hardy 8.04

Any help would be appreciated.

venzen

---

### Post by fava on 2008-04-27
In your config file linux1.cfg try replacing the text 
   file:/mnt/xenimages/... 
with
   tap:aio:/mnt/xenimages/... 

Don't ask me why.

fava

---

### Post by venzen on 2008-04-27
fava, thanks for that. It works! always a quirk isn't there?

regards,
venzen

---

### Post by venzen on 2008-04-27
Well, now I can get DomU's to boot but both fedora core 7 and debian domU's hang when the rcX.d scripts are executed. Is there any known issue with Xen on Hardy 8.04 ?

here is an example domU config file (linux2.cfg):
```
kernel      = '/boot/vmlinuz-2.6.24-16-xen'
ramdisk     = '/boot/initrd.img-2.6.24-16-xen'
memory      = '128'
root        = '/dev/hda2 ro'
disk        = [
                  'tap:aio:/mnt/xenimages/domains/linux2/swap.img,hda1,w',
                  'tap:aio:/mnt/xenimages/domains/linux2/disk.img,hda2,w',
              ]
name        = 'linux2'
vif         = [ 'ip=192.168.2.42,mac=00:16:3E:11:11:42' ]
on_poweroff = 'destroy'
on_reboot   = 'restart'
on_crash    = 'restart'

extra = '2 console=xvc0'
```

I am running xend without any changes to its config file. Does it matter if I use bridged or routed networking with the above domU ?

---

### Post by venzen on 2008-04-28
Well, seems there are some bugs with Xen 3.2 on Ubuntu 8.04 as outlined here:

[https://bugs.launchpad.net/ubuntu/+source/xen-3.2/+bug/204010](https://bugs.launchpad.net/ubuntu/+source/xen-3.2/+bug/204010)

The solution proposed in the discussion above is that users install a patched kernel by Hirano Takahito at:

[http://www.il.is.s.u-tokyo.ac.jp/~hiranotaka/linux-image-2.6.24-16-xen_2.6.24-16.30zng1_i386.deb](http://www.il.is.s.u-tokyo.ac.jp/~hiranotaka/linux-image-2.6.24-16-xen_2.6.24-16.30zng1_i386.deb)

Many users report success with this patched kernel. Just download it and install using dpkg. Thanks Hirano!

It works for me with bridged networking in Xen 3.2 on Ubuntu 8.04 Hardy. Not sure if it is still necessary to specify tap:aio: in place of file: in the DomU config file, but doing so leaves me with a networked Xen environment.

Oh yes, I had to specify

```
1:2345:respawn:/sbin/mingetty xvc0
```

in the Fedora Core 7 /etc/inittab to get a login prompt for this DomU after issuing xm create -c linux1. The linux1 DomU configuration file in /etc/xen also had to include this declaration in the 'extra' parameters (as in the cfg file quoted in the previous post).

You might have success getting Xen routed networking running by using the ethtool utility in your DomU /etc/network/interfaces as outlined in the above bug report and also as per Tom Eastep's excellent setup at [http://www.shorewall.net/XenMyWay-Routed.html](http://www.shorewall.net/XenMyWay-Routed.html)

Hope this helps Ubuntu Xen users.

---

