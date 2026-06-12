---
title: "Getting started with Xen in Ubuntu 11.10; question about xm block-attach"
date: 2011-11-18
forum: Virtualisation
---

### Post by dankegel on 2011-11-18
I'm a complete newbie at Xen, just getting started.

I was happy to see that Ubuntu 11.10 includes Xen again,
[http://zulcss.wordpress.com/2011/09/04/xen-4-1-1-on-ubuntu/](http://zulcss.wordpress.com/2011/09/04/xen-4-1-1-on-ubuntu/)
So I installed ubuntu 11.10's precompiled Xen,
and started playing around with it.
I'm not even trying to start another VM at the moment,
just playing around with mounting block devices,
and had trouble with block-attach:

$ dd if=/dev/zero of=foo.img bs=1024k seek=64 count=0
0+0 records in
0+0 records out
0 bytes (0 B) copied, 1.6493e-05 s, 0.0 kB/s
$ sudo xm block-attach 0 file://home/dank/lvmstuff/foo.img /dev/xvda1 w 0
$ sudo xm block-list 0
Vdev BE handle state evt-ch ring-ref BE-path
51713 0 0 1 -1 -1 /local/domain/0/backend/vbd/0/51713
$ sudo mkfs.ntfs /dev/xvda1
Failed to access '/dev/xvda1': No such file or directory
The device doesn't exist; did you specify it correctly?

Was I supposed to create /dev/xvda1 myself? I thought Xen
did that.

Thanks,
Dan

p.s.
The little example script I'm trying to get working is
[http://kegel.com/linux/xen/demo-xen.sh](http://kegel.com/linux/xen/demo-xen.sh)

---

### Post by dankegel on 2011-11-18
Solved!  Needed to do
  sudo modprobe xen-blkfront
in dom0 to be able to attach a block device there.

---

