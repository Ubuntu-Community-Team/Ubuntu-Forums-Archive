---
title: "Android Studio Virtual Devices not working after upgrade to 17.10"
date: 2018-01-22
forum: Virtualisation
---

### Post by sp40140 on 2018-01-22
I had Android Studio running fine without any issues on Intel C2Q cpu and 8 gigs of ram on Ubuntu Unity 64 bit.
I did in place upgrade to 17.10 Gnome version. 
Now Android studio launches but I can't launch Virtual Devices. (I can launch the Virtual Device Manager).
When I try to launch a device, I get message saying /dev/kvm not found. This is weird.
I see that /dev/kvm is not available, but kvm is installed.
Any ideas?
I googled this and came across this page, but the solution doesn't work for me as you can see below.
[https://askubuntu.com/questions/564910/kvm-is-not-installed-on-this-machine-dev-kvm-is-missing](https://askubuntu.com/questions/564910/kvm-is-not-installed-on-this-machine-dev-kvm-is-missing)

I checked and VMX flag is there in cpuinfo as well.

```

dell@DELL:~/Downloads$ sudo apt-get install qemu-kvm libvirt-bin ubuntu-vm-builder bridge-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bridge-utils is already the newest version (1.5-9ubuntu2).
ubuntu-vm-builder is already the newest version (0.12.4+bzr494-0ubuntu1).
libvirt-bin is already the newest version (3.6.0-1ubuntu6).
qemu-kvm is already the newest version (1:2.10+dfsg-0ubuntu3.1).
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
dell@DELL:~/Downloads$ kvm-ok
INFO: /dev/kvm does not exist
HINT:   sudo modprobe kvm_intel
INFO: For more detailed results, you should run this as root
HINT:   sudo /usr/sbin/kvm-ok
dell@DELL:~/Downloads$ sudo /usr/sbin/kvm-ok
INFO: /dev/kvm does not exist
HINT:   sudo modprobe kvm_intel
INFO: Your CPU supports KVM extensions
KVM acceleration can be used
dell@DELL:~/Downloads$ sudo modprobe kvm_intel
modprobe: ERROR: could not insert 'kvm_intel': Input/output error
dell@DELL:~/Downloads$ 



```

---

### Post by Avamander on 2018-01-23
I have the same problem.

Okay, I have a feeling it's related to this patch, [https://patchwork.kernel.org/patch/9646589/](https://patchwork.kernel.org/patch/9646589/). The last comments seems to be "any update on this? 4.14 is soon out the door, and 4.13 with the breaking change just got released as part of Ubuntu 17.10 / Artful..", so I have no clue if it's going to be fixed with new kernel updates, someone else maybe can chime in?

---

