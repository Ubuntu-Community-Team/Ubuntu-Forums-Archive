---
title: "ubuntu-vm-builder destination issues"
date: 2010-11-16
forum: Virtualisation
---

### Post by connect404 on 2010-11-16
I'm moving a production server from xen to kvm and getting to grips with the ubuntu-vm-builder package/tools. Its all working really well, libvirtd & virt-manager is really slick. just having an issue realting to the destination that the the vm builder uses to dump the fresh vm. 

Read man pages, ubuntu wiki, and googled the crap out of it and still am not sure what is going on.

So heres the command I'm running (with r.img already existing):

[email]dsmith@cleveland.ed.xxxxxxx.net[/email]:~$ sudo ubuntu-vm-builder kvm lucid --debug -v -o \
--flavour=virtual -d=/var/lib/libvirt/images/vm/r.img --rootsize=4096 --swapsize=1024 \
--arch=amd64 --hostname=fatty.ed.xxxxxxx.net --rootpass=setup100 \
--iso=/var/lib/libvirt/images/iso/Ubuntu_10.04.1_amd64_Server.iso \
--ip=10.11.12.50 --net=255.255.255.0 --gw=10.11.12.254 --dns=10.11.12.4 --bridge=br0 \
--mem=512 --libvirt qemu:///system \
--firstboot=/home/dsmith/boot.sh --firstlogin=/home/dsmith/login.sh

This runs smoothly, creates the image but when it unmounts it errors out as below. If I cp /tmp/tmp1juUeQ and then use virsh to start it the image is fine, but it just bombs out when copying it across, plus it is never added to libvirt.

Tried with & without the -o

```
2010-11-15 19:01:02,255 DEBUG   : No such method
2010-11-15 19:01:02,255 DEBUG   : Calling unmount_partitions method in VMBuilder.plugins.libvirt plugin.
2010-11-15 19:01:02,256 DEBUG   : No such method
2010-11-15 19:01:02,256 DEBUG   : Calling unmount_partitions method in VMBuilder.plugins.ubuntu.distro plugin.
2010-11-15 19:01:02,256 DEBUG   : No such method
2010-11-15 19:01:02,256 DEBUG   : Calling unmount_partitions method in context plugin VMBuilder.plugins.kvm.vm.
2010-11-15 19:01:02,256 INFO    : Unmounting target filesystem
2010-11-15 19:01:02,256 DEBUG   : Unmounting /tmp/tmpDeCfr7/
2010-11-15 19:01:02,256 DEBUG   : ['umount', '/tmp/tmpDeCfr7/']
2010-11-15 19:01:06,364 DEBUG   : ['kpartx', '-d', '/tmp/tmp1juUeQ']
2010-11-15 19:01:06,493 DEBUG   : loop deleted : /dev/loop5
2010-11-15 19:01:06,494 DEBUG   : ['kpartx', '-d', '/tmp/tmp1juUeQ']
Traceback (most recent call last):
  File "/usr/bin/ubuntu-vm-builder", line 24, in <module>
    uvb.main()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/contrib/cli.py", line 119, in main
    os.mkdir(destdir)
OSError: [Errno 2] No such file or directory: '=/var/lib/libvirt/images/vm/r.img'
```


So if I use -d=/var/lib/libvirt/images/vm/
It complains that it already exists and wont cp the image over

If I use -d=/var/lib/libvirt/images/vm/test.img
It makes a folder called test.img and then dumps the "tmp1juUe" file in that

If I dont use -d it creates ubuntu-vm-$SUITE-$ARCH/tmp1juUe in $PWD

What Im after is a way to specify a path and .img name to keep all my images in the same location with an understandable naming convention... Otherwise its a pain to edit the xml for each image after the fact.

Also, seems the images are all raw format, any ideas how to default to qcow2? Cant seem to find a modifier for this either. KVM server is lucid amd64 btw.


Any advice would be appreciated :)

---

