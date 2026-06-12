---
title: "Unable to create KVM guest"
date: 2009-05-30
forum: Server Platforms
---

### Post by satimis on 2009-05-30
Hi folks,

I was following;
[http://howtoforge.com/virtualization-with-kvm-on-ubuntu-9.04](http://howtoforge.com/virtualization-with-kvm-on-ubuntu-9.04)

to create a KVM virtual machine running Ubuntu 9.04 32bit but failed creating guest.

# vmbuilder kvm ubuntu --suite=intrepid --flavour=virtual --arch=i386 --mirror=http://192.168.0.10:9999/ubuntu -o --libvirt=qemu:///system --tmpfs=- --ip=192.168.0.11 --part=vmbuilder.partition --templates=mytemplates --user=admin --name=Admin --pass=apassword --addpkg=vim-nox --addpkg=unattended-upgrades --addpkg=acpid --firstboot=boot.sh --mem=256 --hostname=vm1 --bridge=br0```

.......
2009-05-30 17:31:28,302 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-05-30 17:31:28,523 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-05-30 17:31:28,554 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-05-30 17:31:33,813 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-05-30 17:31:35,302 INFO     addgroup: The group `admin' already exists and is not a system group. Exiting.
2009-05-30 17:31:35,303 INFO     Cleaning up
Traceback (most recent call last):
  File "/usr/bin/vmbuilder", line 29, in <module>
    VMBuilder.run()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/__init__.py", line 66, in run
    frontend.run()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/plugins/cli/__init__.py", line 67, in run
    vm.create()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/vm.py", line 469, in create
    raise e
VMBuilder.exception.VMBuilderException: Process (['chroot', '/tmp/vmbuilderJ0sb_H/root', 'addgroup', '--system', 'admin']) returned 1. stdout: , stderr: addgroup: The group `admin' already exists and is not a system group. Exiting.

```

root@server1:~/vm1# ls -l /etc/libvirt/qemu/```

total 4
drwxr-xr-x 3 root root 4096 2009-05-28 19:12 networks

```

root@server1:/home/satimis# virsh list```

Connecting to uri: qemu:///system
 Id Name                 State
----------------------------------

```

Not guest created.

This seems a bug;
[http://ubuntuforums.org/archive/index.php/t-1056124.html](http://ubuntuforums.org/archive/index.php/t-1056124.html)

Is there a solution?  Please advise.  TIA

B.R.
satimis

---

