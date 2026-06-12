---
title: "Is testing KVM inside virtualbox possible?"
date: 2010-05-23
forum: Virtualisation
---

### Post by MystaMax on 2010-05-23
My goal was to familiarize myself w/ KVM before installing it on my physical server. I assumed this wasn't going to work, but I wanted to try and then ask for some reassurance.

I've got VirtualBox installed on Ubuntu 9.10 64-bit as host, and I've got Ubuntu 10.04 64-bit server as a guest. I've got VT-x/AMD-V enabled on the guest. I then ran "kvm-ok" from the command line, and received:

> INFO: Your CPU does not support KVM extensions
KVM acceleration can NOT be used

When I run less /proc/cpuinfo, under flags, vmx isn't listed, and I guess thats because its technically a virtual processor. For some reason I thought since VT-x/AMD-V is enabled in the guest, kvm would be possible under virtualbox.

But, I guess I was wrong. Or, am I doing something wrong?

Thanks in advance.

---

### Post by fjgaude on 2010-05-23
I would say no, but others may have another idea.

---

### Post by TheFu on 2010-05-24
In general, only 1 hypervisor can be installed on a physical system. KVM requires VT-x/AMD-V support from the CPU. 

Ok, with that said, it may be possible to run VirtualBox as a client under a KVM host since Vbox doesn't require VT-X/AMD-V support.  I don't know that is true and honestly would not expect it to work.

The certain way to test multiple hypervisors on a single machine is to setup dual-tri-quad booting.

---

### Post by MystaMax on 2010-05-24
Hey guys, thanks for the replies. I think I understand (better) now. I ended up finding a spare PC @ work where I can do my testing.

---

