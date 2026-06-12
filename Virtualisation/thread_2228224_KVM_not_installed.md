---
title: "KVM not installed?"
date: 2014-06-06
forum: Virtualisation
---

### Post by lambdafox on 2014-06-06
When I run virt-manager, and click on the icon to create a new virtual machine, I get an error that KVM is not installed or is not loaded.

I use Ubuntu GNOME 14.04

All qemu packages are version  2.0.0+dfsg-2ubuntu1
qemu-kvm
and
many other qemu packages installed...

libvirt packages: 1.2.2-0ubuntu13.1

libvirt0
libvirt-bin
libvirt-doc
python-libvirt

virt-manager 0.9.5-1ubuntu3

When I open terminal and enter lsmod | grep kvm, I get nothing returned.  No lines showing kvm or kvm_amd and no error of any kind.

Hardware:
Tyan S2877 with dual Opteron 285s
I have the latest bios and don't see any setting in there to turn virtualization on or off.

when i do

sudo apt-get -s install qemu-kvm   
Here are the results:

  Reading package lists... Done Building dependency tree
Reading state information... Done qemu-kvm is already the newest version. The following packages were automatically installed and are no longer required:   kde-l10n-engb libgtk2-gladexml-perl libqt4-test libvncserver0 Use 'apt-get autoremove' to remove them. 0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


The problem seems to be my hardware.  Evidently the Opeteron 285 does not support the kvm extensions:

```
$kvm-ok
INFO: Your CPU does not support KVM extensions
INFO: For more detailed results, you should run this as root
HINT:   sudo /usr/sbin/kvm-ok
$sudo /usr/sbin/kvm-ok
INFO: Your CPU does not support KVM extensions
KVM acceleration can NOT be used
```

---

### Post by TheFu on 2014-06-06
virt-manager can be used to remotely control VM hosts over a network.
If you want it to control a local KVM host, then you need to have kvm kernel modules loaded ... 
```
$ lsmod |grep kvm
kvm_intel             143060  6 
kvm                   451511  1 kvm_intel
```

```
$ dpkg -l |grep kvm
ii  qemu-kvm                              2.0.0+dfsg-2ubuntu1                  amd64        QEMU Full virtualization on x86 hardware (transitional package)

```
Does this work the same on your machine?  

I gave a [KVM how-to presentation]("http://blog.jdpfu.com/ALE/ALE-NW/2014_04-virtualization.html") recently. It has dependencies and how to setup a Linux bridge included. The default bridging doesn't seem as stable to me and others.

---

### Post by lambdafox on 2014-06-06
copied from my terminal:

```
$ dpkg -l |grep kvm
ii  qemu-kvm                                    2.0.0+dfsg-2ubuntu1                                    amd64        QEMU Full virtualization on x86 hardware (transitional package)
```

---

### Post by TheFu on 2014-06-06
Ok ... moving on.
Is your userid in the libvirtd group?

---

### Post by lambdafox on 2014-06-06
as noted above, lsmod | grep kvm returns nothing.  no error, nada.

---

### Post by lambdafox on 2014-06-06
> **TheFu said:**
> Ok ... moving on.
Is your userid in the libvirtd group?

ok... since i have no idea what that means i am hoping this might get me somewhere!  Linux newbie here

---

### Post by TheFu on 2014-06-06
Please run ```
egrep '^flags.*(vmx|svm)' /proc/cpuinfo 
```
If nothing is returned, that means the CPU either cannot run KVM or the BIOS doesn't have it enabled.  Check the CPU capabilities at the AMD website to see if it even supports virtualization.

If that is the case - time to switch to VirtualBox for virtualization ... or buy newer hardware that is AMD-V/VT-x capable.  For stable, server, processes, I would NOT deploy virtualbox.

---

