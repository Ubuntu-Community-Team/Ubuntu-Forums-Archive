---
title: "Disk/physical size more than virtual size - qcow2 image"
date: 2012-07-15
forum: Virtualisation
---

### Post by toshko3 on 2012-07-15
Hi I have a problem with qcow2 image files.
When the guest OS writes files it is all OK and the file disk size is increasing. When I delete something, the disk size is not decreasing (which I wrote is by design, for now). But, obviously, when I write again something it takes new "bytes" in the disk size. So after some time the result of the root image file of the virtual machine is like this:

```
qemu-img info ubuntu-pdc-vda.img 
image: ubuntu-pdc-vda.img
file format: qcow2
virtual size: 10G (10737418240 bytes)
disk size: 14G
cluster_size: 65536
```
and a confirmation:
```
du -sh ubuntu-pdc-vda.img 
15G     ubuntu-pdc-vda.img
```

It is the same with other images, too. I have big problems with "out of space" on the host machine, because their maximum sizes are meant to be what I have set in "virtual size". But they just rise and rise with no limit over time. I suspect a major bug here. Please, help! :(

---

### Post by Dedoimedo on 2012-07-17
How did you create the virtual disk file?
Dedoimedo

---

### Post by toshko3 on 2012-07-17
Hi and thanks for answering!
I have made some progress on the issue and in order to not duplicate it, you can see it here:
[http://www.linuxquestions.org/questions/linux-virtualization-90/disk-physical-size-more-than-virtual-size-qcow2-image-4175416848/#post4730524](http://www.linuxquestions.org/questions/linux-virtualization-90/disk-physical-size-more-than-virtual-size-qcow2-image-4175416848/#post4730524)
or here:
[https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/1025244](https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/1025244)

Thank you for any ideas!

---

