---
title: "Ubuntu Server KVM error - CPU does not support"
date: 2020-03-25
forum: Virtualisation
---

### Post by kevincook01 on 2020-03-25
Hi Everyone,

I'm hoping someone can help a complete rookie here.  Stuck working from home so I'm trying to learn something completely new.

I'm trying to setup Ubuntu Server 18.04.4 on my Windows 10 machine.

I have managed to install 18.04.4 on a virtualbox machine and can access the server within the console.  Trying to use multipass to setup a couple of vm's on the server but get an error saying my CPU does not support KVM extensions.

I have a Aorus Master X570 motherboard, AMD 3700X CPU, 64GB RAM.  I went into the BIOS and enabled SVM.

Am I out of luck or just not smart enough to figure this out?

Thanks,
Kevin

---

### Post by kevincook01 on 2020-03-25
A couple of BIOS screenshots in case that helps.

---

### Post by deadflowr on 2020-03-25
You're running into the same or similar issue as this user: [https://ubuntuforums.org/showthread.php?t=2439106]("https://ubuntuforums.org/showthread.php?t=2439106")
The same rules of nested virtualization should apply.

---

### Post by Doug S on 2020-03-25
It used to be trivial to nest KVM/QEMU vm's. Then it got harder, but still relatively easy a few years ago, as one had to remember to set `/sys/module/kvm_intel/parameters/nested` in the VM.
However, now I can't seem to figure it out (my test server computers are 20.04 development already), as things seem to have changed yet again and `/sys/module/kvm_intel/parameters/nested` doesn't even exist on my VM.

However, I observe that the VM's default CPU has changed, and seems to now be pathetic ("kvm-ok" says no). So I changed it to "host-passthrough" and now everything seems to be fine (("kvm-ok" says yes) and:

```
doug@serv-ff:~$ cat /sys/module/kvm_intel/parameters/nested
Y

``` 
Although I have yet to actually try to install a VM within that VM.

By the way, I used "virsh edit" and changed this:

```
  <cpu mode='custom' match='exact' check='partial'>
    <model fallback='allow'>Westmere-IBRS</model>
  </cpu>

``` to this:
```
  <cpu mode='host-passthrough' check='none'/>
```
EDIT: I installed a 20.04 server VM quest on my 20.04 server VM quest on my 20.04 server host.

---

