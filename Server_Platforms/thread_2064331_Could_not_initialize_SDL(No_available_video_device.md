---
title: "Could not initialize SDL(No available video device) - exiting"
date: 2012-09-29
forum: Server Platforms
---

### Post by ankitjayswal on 2012-09-29
Hello guys,
I am working with openstack cloud.
I have done setup for it.

Now i had created disk image by following command,
qemu-img create -f qcow2 vdisk.img 10G

image is created properly

But, now when installing OS into this disk image, i am getting following error.

localadmin1@server2:~$ sudo kvm -hda vdisk.img -cdrom /home/localadmin1/ubuntu-11.10-server-i386.iso -boot d  -m 384
Could not initialize SDL(No available video device) - exiting


I am unable to find solution for it, please help me n replay as soon as possible.

---

