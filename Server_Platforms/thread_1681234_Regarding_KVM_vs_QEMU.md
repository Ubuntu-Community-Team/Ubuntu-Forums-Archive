---
title: "Regarding KVM vs QEMU"
date: 2011-02-03
forum: Server Platforms
---

### Post by brettg on 2011-02-03
Hi, 

I'm playing around with KVM on 10.04 using the guide [here]("https://help.ubuntu.com/community/KVM/Installation").

Everything is going fine but I just have a question.

When I check out the host details in Virtual Machine Manager (libvirt) it says that the hypervisor is qemu. I would have expected it to be KVM.

The machine is a four socket with quad core xeons (16 CPUs) and it supports VT extensions;

```
$ egrep -c '(vmx|svm)' /proc/cpuinfo
16
```

KVM is installed;

```
$ ls -al /dev/kvm
crw-rw---- 1 root kvm 10, 232 2011-02-02 01:20 /dev/kvm
```

I'm not sure whether it is "normal" for qemu to be shown as the hypervisor by libvirt. 

Is there a way on the console to determine whether the system is running in fully paravirtualized mode or not?

I just want to make sure I am do this right (and understand what I am doing)

Cheers, and thanks in advance!

---

### Post by brettg on 2011-02-03
OK, playing around a bit more, it seems that if I look at a virtual machine on its "Overview" page it reports the hypervisor as kvm (/usr/bin/kvm) which is what I am hoping to see.

I'm not sure why it reports qemu on the host details section but I think it can be filed under "just one of those oddities you get in Free software"

---

