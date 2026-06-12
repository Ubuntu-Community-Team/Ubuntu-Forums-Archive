---
title: "KVM problem"
date: 2011-06-01
forum: Server Platforms
---

### Post by guitarman9182 on 2011-06-01
Hello,

I am having a small problem with running kvm guests Ubuntu server 11.04. When i attempt to start up a virtual machine, I get this error:

kvm_create_vm: Device or resource busy
Could not initialize KVM, will disable KVM support
kvm_set_phys_mem: error unregistering overlapping slot: Invalid argument

and this appears in dmesg:

[151414.211222] kvm: enabling virtualization on CPU0 failed

Now I have already check that the virtualization option in the bios is enabled and my cpu does support it as well so I am not sure what is the problem. If it helps I am running an AMD Phenom 2 processor. Let me know if more information is needed

---

### Post by sueng66 on 2011-06-22
got the same problem I am using quad core phenom, but working well with Intel processor, any suggestion ?

---

### Post by guitarman9182 on 2011-06-22
I kind of gave up on it since I couldn't find any information anywhere. But one of the last things I tried was removing all of the kvm drivers using rmmod and trying something else. I put virtualbox on just to try and whenever I started a guest, it complained that kvm was still running and thus couldn't start any 64 bit vm's. 

I got frustrated so I backed up my data and reinstalled the OS just to fix the problem. I didn't put kvm back on lol.

---

### Post by sueng66 on 2011-06-23
you're right , i've just relaized that virtualbox could not use AMD-V anymore , It's working when I used older kernel 2.32.x

---

