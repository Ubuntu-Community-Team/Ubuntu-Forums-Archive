---
title: "Static IP KVM Guest"
date: 2011-01-03
forum: Server Platforms
---

### Post by Valrox on 2011-01-03
Heya everyone!

I installed Ubuntu Server (10.10) and configured it for Bridged networking together with KVM. Everything works just fine network related. When I install a virtual machine with 'virt-install' and want to use it as a template for my yet-to-clone virtual machines, I'll be facing 1 problem: All of the Static IP's will be the same.

Is there a way, to assign an IP address to the guest system FROM the host system? I need console/vnc into the guest and change it manually. I hope there's a way to just 'set' a static ip address from the host itself without SSHing/VNC/Consoling into the guest system.

I hope you guys can help me out! Thanks in advance!

Gz. Valrox

PS.: Yes I googeled. No 'real' results other than people complaining their python-vm-builder script isn't working or broken/old links.

---

### Post by bvidinli on 2011-11-12
this is what I am searching for too, now. will try to post here result if I find one.

---

### Post by bvidinli on 2011-11-12
I found this solution:

as described in [http://equivocation.org/node/107](http://equivocation.org/node/107) , mount img file.
edit etc/network/interfaces file inside mount point, to reflect required ip changes.
unmount the file.

if you use new file with kvm / virtual machine, the new machine will have new ip, that you edited above. 

now, I will automate this task, just like your purpose, "to use an img file as a template for new vm's"

---

