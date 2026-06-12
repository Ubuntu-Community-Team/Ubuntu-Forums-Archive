---
title: "KVM Error - Could not find an installable distribution"
date: 2011-02-16
forum: Virtualisation
---

### Post by linbox289 on 2011-02-16
I tried installing Virtual machine using KVM as per the instructions [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)  while creating guest 

ubox@ubox:~$ sudo virt-install --connect qemu:///system --name vmbox1 --ram 512 --file=/VM/1/disk1.img --file-size=8 --network=bridge:br0 --vnc --os-type=linux --os-variant=ubuntulucid --location=/tmp/ubuntu-10.04.1-server-amd64_2.iso

Starting install...
ERROR    Could not find an installable distribution at '/tmp/ubuntu-10.04.1-server-amd64_2.iso'
Domain installation does not appear to have been successful.  If it was, you can restart your domain by running 'virsh start vmbox1'; otherwise, please restart your installation.
ERROR    Could not find an installable distribution at '/tmp/ubuntu-10.04.1-server-amd64_2.iso'
Traceback (most recent call last):
  File "/usr/bin/virt-install", line 1033, in <module> main()
  File "/usr/bin/virt-install", line 915, in main start_time, guest.start_install) 
  File "/usr/bin/virt-install", line 957, in do_install dom = install_func(conscb, progresscb, wait=(not wait))
  File "/usr/lib/pymodules/python2.6/virtinst/Guest.py", line 971, in start_install self._prepare_install(meter)
  File "/usr/lib/pymodules/python2.6/virtinst/Guest.py", line 772, in _prepare_install meter = meter)
  File "/usr/lib/pymodules/python2.6/virtinst/DistroInstaller.py", line 249, in prepare self._prepare_kernel_and_initrd(guest, distro, meter)
  File "/usr/lib/pymodules/python2.6/virtinst/DistroInstaller.py", line 194, in _prepare_kernel_and_initrd type=self.os_type, distro=distro)
  File "/usr/lib/pymodules/python2.6/virtinst/OSDistro.py", line 144, in acquireKernel scratchdir, type, distro)
  File "/usr/lib/pymodules/python2.6/virtinst/OSDistro.py", line 124, in _acquireMedia scratchdir=scratchdir, arch=arch)
  File "/usr/lib/pymodules/python2.6/virtinst/OSDistro.py", line 110, in _storeForDistro baseuri)
ValueError: Could not find an installable distribution at '/tmp/ubuntu-10.04.1-server-amd64_2.iso'

I have placed the ISO image under /tmp I am not sure whether I messed up with something, please guide. 

Ubuntu version : Ubuntu Desktop Edition 10.04 LTS

Thanks
~harry

---

### Post by linbox289 on 2011-02-17
I moved the ISO file to /cdrom and it worked. But could not figure out why it cant pull the file when its been under /tmp :(

thanks

---

