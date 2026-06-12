---
title: "KVM nested virtualization on intel"
date: 2011-01-28
forum: Virtualisation
---

### Post by Neocult on 2011-01-28
Hi there,

i want to give nested virtualization a try for developing purposes and  tried this already on a laptop with AMD X2 processor and got it working.

Now I have tried this on my NAS with Intel Core2Duo processor the same way:

I wrote a wrapper kvm.nested
```

#!/bin/bash
exec /usr/bin/kvm -enable-nesting "$@"

```and change the emulator in guest xml

```
<emulator>/usr/bin/kvm.nested</emulator>
```Add two  rules two the apparmor files for libvirt to grant permission to the  script.

The virtual machine starts without any problems, but checking /proc/cpuinfo there is no vmx available.

I already tried to modify the cpu by modifying the wrapper to:
```

exec /usr/bin/kvm -enable-nesting -cpu qemu64,+vmx "$@"
and
exec /usr/bin/kvm -enable-nesting -cpu host "$@"

```But there is still no vmx available in the virtual machine. Any ideas ?

---

### Post by Neocult on 2011-01-29
The answer is easy and sobering. There ist no support for nested virtualization with intel vmx in the current version of kvm in the Ubuntu repositories. With the newest patches for kvm it is possible, but there are still in development . The 29th patch was described at the KVM mailing list two days ago. (January 27th, 2011)

So I let them a bit more time, but the support will come :P

---

### Post by Ubu-Sef on 2011-08-05
Sorry for the kick, but the nested VT-x support is currently in the GIT repo now. It is still early, so expect some issues.

Nevermind, is there a ppa or so with have that deb?

---

### Post by pushb on 2013-04-29
While the system boots...

Go to settings-> processor settings -> Virtualizaition support ->Enable


After installing the VPC in the base server.

[LIST=1]
[*]virt-manager
[/LIST]
    2. open the hypervisor virtual machine, go to Details > Processor

[LIST=1]
[*]unfold the "Configuration"
[*]press the "Copy host CPU configuration" button
[*]unfold the "CPU Features"
[*]verify the "vmx" feature is set to "require" press Apply
[/LIST]


Which this will help you...!  Feel free to reply back if u wont understand.!

---

### Post by wildmanne39 on 2013-05-03
Thread closed. Please do not post in old threads.

---

