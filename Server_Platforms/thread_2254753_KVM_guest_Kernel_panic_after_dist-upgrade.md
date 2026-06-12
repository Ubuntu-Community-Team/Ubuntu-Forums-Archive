---
title: "KVM guest Kernel panic after dist-upgrade"
date: 2014-11-29
forum: Server Platforms
---

### Post by Dreadslayer on 2014-11-29
Hi there

I'm using Ubuntu Server 12.04.5 and KVM for hosting several guest systems. Recently after dist-upgrading and restarting all guests, one of them didn't come up again with this error:

[IMG]http://oi58.tinypic.com/14ccopu.jpg[/IMG]

I created this guest using this vmbuilder command:
```
sudo vmbuilder kvm ubuntu --suite precise --flavour virtual --arch amd64 -o --libvirt qemu:///system --ip 10.5.5.9 --hostname vm-ub-04 --mask 255.255.255.0 --net 10.5.5.0 --bcast 10.5.5.255 --gw 10.5.5.1 --dns 8.8.8.8 8.8.4.4 --bridge br0 --part vmbuilder.partition --user morrow --name Morrow --pass default --addpkg acpid --addpkg vim --addpkg openssh-server
```

Any help on what I could do to solve this issue would be much appreciated since I have no clue...

---

### Post by newbie-user on 2014-12-01
You might have created a container instead of a full virtual machine for that guest. A container relies on the host's kernel to run, so if you dist-upgraded your host kernel, you may have borked your guest, which is looking for the previous kernel version.

---

### Post by Dreadslayer on 2014-12-01
Thanks for your answer. I dist-upgraded the guest, sorry I didn't clarify that. This has worked for the other guests which I created the same way. Dist-upgrading the host hasn't been a problem so far.

---

