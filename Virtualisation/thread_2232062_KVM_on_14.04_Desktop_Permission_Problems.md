---
title: "KVM on 14.04 Desktop Permission Problems?"
date: 2014-06-29
forum: Virtualisation
---

### Post by rayj00 on 2014-06-29
Makes more sense to use Server,  but I thought I'd try Desktop.


So I get to step 5 of 5 creating a Win7 Pro VM and gt this error.  Any ideas how to fix this?

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 96, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/create.py", line 1983, in do_install
    guest.start_install(False, meter=meter)
  File "/usr/lib/python2.7/dist-packages/virtinst/Guest.py", line 1246, in start_install
    noboot)
  File "/usr/lib/python2.7/dist-packages/virtinst/Guest.py", line 1314, in _create_guest
    dom = self.conn.createLinux(start_xml or final_xml, 0)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 3199, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: internal error: process exited while connecting to monitor: Could not access KVM kernel module: Permission denied
failed to initialize KVM: Permission denied

---

### Post by rayj00 on 2014-06-29
Now I am getting this error after doing the rmmod kvm
modprobe -a kvm?


Unable to complete install: 'internal error: process exited while connecting to monitor: qemu-system-x86_64: -drive file=/media/ray/HDD 1T/Virtual Machines/Win7Pro,if=none,id=drive-ide0-0-0,format=raw: could not open disk image /media/ray/HDD 1T/Virtual Machines/Win7Pro: Could not open '/media/ray/HDD 1T/Virtual Machines/Win7Pro': Permission denied
'

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 96, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/create.py", line 1983, in do_install
    guest.start_install(False, meter=meter)
  File "/usr/lib/python2.7/dist-packages/virtinst/Guest.py", line 1246, in start_install
    noboot)
  File "/usr/lib/python2.7/dist-packages/virtinst/Guest.py", line 1314, in _create_guest
    dom = self.conn.createLinux(start_xml or final_xml, 0)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 3199, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: internal error: process exited while connecting to monitor: qemu-system-x86_64: -drive file=/media/ray/HDD 1T/Virtual Machines/Win7Pro,if=none,id=drive-ide0-0-0,format=raw: could not open disk image /media/ray/HDD 1T/Virtual Machines/Win7Pro: Could not open '/media/ray/HDD 1T/Virtual Machines/Win7Pro': Permission denied

[B][COLOR="#FF0000"]Here are the permissions:
drwxr-xr-x   3 root root  4096 Jun 29 11:18 media
drwxr-x---+ 5 root root 4096 Jun 29 13:27 ray
drwx------  1 ray ray  4096 Jun 29 10:23 HDD 1T
drwx------ 1 ray ray     144 Jun 29 13:29 Virtual Machines
-rw------- 1 ray ray 107374182400 Jun 29 13:41 Win7Pro

I tried to chmod on Win7Pro but the permissions never changed and I got no warnings.
[/COLOR][/B]

---

