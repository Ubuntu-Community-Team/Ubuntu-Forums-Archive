---
title: "[SOLVED] Would like to use kvm/vmbuilder instead of VirtualBox"
date: 2008-11-15
forum: Virtualisation
---

### Post by Shibata on 2008-11-15
I would like to set up test environment for jaunty/intrepid/hardy on Ubuntu 8.10. In past day, use VirtualBox, but could not use 64bit guest on my environment (hp's ML115G5/Athlon 1640B). So, try to install kvm/python-vm-builder for 64bit guest.

As reference to below links, installation for softwares was successful probably. However I could not find to install guest or connect to guest. Could you tell me my lost in procedure?

Recerences:
 * [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)
 * [https://help.ubuntu.com/community/JeOSVMBuilder](https://help.ubuntu.com/community/JeOSVMBuilder)
 * [http://doc.ubuntu.com/ubuntu/serverguide/C/libvirt.html](http://doc.ubuntu.com/ubuntu/serverguide/C/libvirt.html)

Check environment:
```
$ egrep '(vmx|svm)' /proc/cpuinfo
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr 
pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext 
fxsr_opt rdtscp lm 3dnowext 3dnow up rep_good nopl pni cx16 lahf_lm 
svm extapic cr8_legacy 3dnowprefetch
$ grep ' lm ' /proc/cpuinfo
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr 
pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext 
fxsr_opt rdtscp lm 3dnowext 3dnow up rep_good nopl pni cx16 lahf_lm 
svm extapic cr8_legacy 3dnowprefetch
$ uname -m
x86_64
```

Install:
```
$ sudo apt-get install ubuntu-virt-server ubuntu-virt-mgmt
$ sudo adduser `id -un` libvirtd
```
And reboot.

Python-vm-builder's way:
```
$ sudo vmbuilder kvm ubuntu --suite intrepid --flavour generic --arch amd64  -o --libvirt qemu:///system
Virtual machine was created in ~/ubuntu-kvm/disk0.qcow2. 
$ virsh -c qemu:///system
virsh # start ubuntu
virsh # list
 Id Name                 State
----------------------------------
  4 ubuntu               running
virsh # console ubuntu
No console available for domain
```

How to operate guest os...?


Vm-install's way:
```
$ sudo virt-install -n intrepid_amd64 -r 512 -f ~/VirtualBox/intrepid_amd64.img \
 -s 8 -c qemu:///system --accelerate --connect=qemu:///system \
 --vnc --noautoconsole --cdrom /home/sigma/Download/ubuntu-8.10-desktop-amd64.iso \
 -v --os-type=linux

Traceback (most recent call last):
  File "/usr/bin/virt-install", line 499, in <module>
    main()
  File "/usr/bin/virt-install", line 368, in main
    domain = guest.bestDomainType(options.accelerate)
  File "/usr/lib/python2.5/site-packages/virtinst/CapabilitiesParser.py", line 181, in bestDomainType
    return self.domains[-1]
IndexError: list index out of range
```

---

### Post by rmcewen on 2008-11-17
1. You should be able to administer a running domain using vnc.  You can find the "display" # with the virsh "vncdisplay" command:

```
virsh # list
 Id Name                 State
----------------------------------
  5 dns                  running
  6 mail                 running
  7 www                  running
  8 mysql                running

virsh # vncdisplay dns
:0

virsh # vncdisplay www
:2
```

Then connect to the guest via vnc with something like "vncviewer hostip:2"

2. As for the virt-install command, I don't know if it's your problem but you're using a "-c" argument for the connection whereas "-c" is a shortcut for the cdrom in virt-install.  Here's a sample:

```
virt-install -n debian-etch-master \
-r 1000 \
--vcpus=1 \
-f /var/vm/debian-etch-master/hda.qcow2 \
-w bridge:br0 \
--vnc \
--accelerate \
-c /var/iso/debian-40r4a-amd64-netinst.iso \
--os-type=linux \
--connect qemu:///system

```

---

### Post by bodhi.zazen on 2008-11-17
+1 on KVM.

---

### Post by Shibata on 2008-11-17
Thank you for your reply, rmcewen, bodhi.zazen.

> **rmcewen said:**
> 1. You should be able to administer a running domain using vnc.  You can find the "display" # with the virsh "vncdisplay" command:

```
virsh # list
 Id &#21517;&#21069;               &#29366;&#24907;
----------------------------------
  4 ubuntu               &#23455;&#34892;&#20013;

virsh # vncdisplay ubuntu
127.0.0.1:0
```

I can display console via Vinagre, and virt-manager. And noticed, my virtual machine have not booted correctly. It was in BusyBox with messeage "ALERT! /dev/disk/by-uuid/.... does not exist. Dropping to a shell!!"

However, it progressed boot process with Ctrl+D. And I got login console. Thank you!



> **rmcewen said:**
> 2. As for the virt-install command, I don't know if it's your problem but you're using a "-c" argument for the connection whereas "-c" is a shortcut for the cdrom in virt-install.  Here's a sample:

Sorry, duplication of "-c" opiton is my mistake. However even if delete "-c qemu:///system", same error message was displayed.

Based on your sample, I will continue investigation.

---

