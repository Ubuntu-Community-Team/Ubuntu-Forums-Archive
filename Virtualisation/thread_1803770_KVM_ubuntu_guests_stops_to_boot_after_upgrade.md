---
title: "KVM ubuntu guests stops to boot after upgrade"
date: 2011-07-13
forum: Virtualisation
---

### Post by josir on 2011-07-13
Hi folks, 

I just upgrade my Ubuntu 8.04.3 to 8.04.4 and now all ubuntu guests don't boot anymore. 

Looking at graphical console, machine freezes on "bios" boot.

Digging on /var/log/libvirtd/qemu logs only shows:

LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin /usr/bin/kvm -S -M pc -m 512 -smp 1 -name Linux18 -uuid 929a96b7-1d69-6922-dbeb-c9e60959740b -monitor pty -pidfile /var/run/libvirt/qemu//Linux18.pid -boot c -drive file=/srv/Linux18.img,if=ide,index=0,boot=on -net nic,macaddr=00:16:3e:24:00:0d,vlan=0,model=virtio -net tap,fd=20,script=,vlan=0,ifname=vnet2 -serial pty -parallel none -usb -vnc 127.0.0.1:2
char device redirected to /dev/pts/2
char device redirected to /dev/pts/3
info cpus
* CPU #0: pc=0x00000000000ffff0 thread_id=5120^M
cont

Does somebody have any clue?
Is there any better debug log?

Thanks in advance for any tip.

---

