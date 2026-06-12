---
title: "KVM - reboot VM problem"
date: 2011-10-26
forum: Server Platforms
---

### Post by Pechy on 2011-10-26
Hi,
I have problem with KVM - when I try to reboot virtual machine, it doesn´t boot again, only thing that help is to log on the host server, kill the kvm process for this VM and start it using virsh again.
I´m using
```
Linux 2.6.38-8-server #42-Ubuntu SMP Mon Apr 11 03:49:04 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```
I´ve figured out, that when I try reboot, on the host machine it logs
```
kernel: [6870320.348829] kvm: 6176: cpu0 unhandled rdmsr: 0xc0010001
```.
Have anabody here similar experience? And is there somebody who knows how to fix it?

Thanks.

---

