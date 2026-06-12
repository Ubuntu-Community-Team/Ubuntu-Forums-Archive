---
title: "[KVM] Vista Fails on Boot"
date: 2008-04-05
forum: Virtualisation
---

### Post by ph8 on 2008-04-05
Hey all,

I've installed vista successfully using kvm on a remote server

On boot however it gets pass the bootloader and is about to start the main OS, when the whole VM dies - i have VNC'ed in but, amusingly enough, i can find no way of keeping the vnc window open when the connection dies - maybe there's an error displayed, but I don't know!

Does this sound familiar to anyone? Can anyone help me get vista booting?

Here's my runline:

kvm -m 1024 -daemonize -boot c -vnc 85.234.136.16:1 -net nic,vlan=0,macaddr=00:16:3e:69:00:05 -net tap /home/xen/domains/hades/disk.img

I've also tried readding the install cdrom with -cdrom, but it makes no difference

Cheers,

ph8

---

### Post by aikiwolfie on 2008-04-05
So far as I know only the pants low end versions of Vista can be used in a VM. What version of Vista are you using?

---

