---
title: "Permission denied to read images on KVM"
date: 2012-05-23
forum: Server Platforms
---

### Post by josir on 2012-05-23
Hi folks,

I am trying to run KVM machines with a new server with 12.04 and I got the following error:

error: internal error process exited while connecting to monitor: qemu-system-x86_64: -drive file=/srv/Linux14.qcow2,if=none,id=drive-ide0-0-0,format=qcow2: could not open disk image /srv/Linux14.qcow2: Permission denied

Using the same machine with Ubuntu 11, it works perfectly. Is there any limitation or new policies that I should configure with 12.04 ?

Ubuntu 12.04 Server 64bits.
Compiled against library: libvir 0.9.8
Using library: libvir 0.9.8
Using API: QEMU 0.9.8
Running hypervisor: QEMU 1.0.0

---

### Post by josir on 2012-05-23
I just got the answer but how can I add a permission to my custom directory (in fact, it's another partition ?

[http://superuser.com/questions/298426/kvm-image-failed-to-start-with-virsh-permission-denied?answertab=active#tab-top](http://superuser.com/questions/298426/kvm-image-failed-to-start-with-virsh-permission-denied?answertab=active#tab-top)

---

### Post by josir on 2012-05-23
Just to document to other users using 12.04

You have to update /etc/libvirt/qemu.conf

and uncomment user="root" and group="root"

---

