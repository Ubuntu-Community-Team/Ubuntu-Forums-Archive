---
title: "bootable CD using nfs filesystem?"
date: 2007-06-05
forum: The Cafe
---

### Post by qbxk on 2007-06-05
To maintain some machines that need to provide a basic service over a long period of time, we need a (magical) cd that could be used to boot a machine, which would then boot using an image accessible over nfs, or more generally the network.  because of the nature of the network, pxe is sort of out, since i can't set up the dns server and hand out ips the way it needs to.  it's possible i'm not understanding the way pxe works, but it seems to not suit our need.  i'd rather have a dialog at the beginning of the boot process asking me the ip address or host name to acquire it's image from (and possibly various methods besides NFS).  the image it finds we'd like to just use as the filesystem, unionfs seems to be a candidate for this task?  and this image, ideally would be a chrootable filesystem that you could maintain from within using all the normal methods, just as you would if you were customizing a livecd

and, crucial, once we boot the image, the cd must not be required anymore, we want to eject it and use the cd drive in the mission of the machine.  the machines have hard disks in them that we can write to at liberty, going even as far as wiping it on every boot.  we could use as swap space or the writeable branch of the unionfs tree

so i've done a lot of reading, but haven't been able to put together a tool chain that will be fruitful. and i'd like to use ubuntu as the base for the image, because, that would be nice.  if anybody has suggestions, thanks

---

