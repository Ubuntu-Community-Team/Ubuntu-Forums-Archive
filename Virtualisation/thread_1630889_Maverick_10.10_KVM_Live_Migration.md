---
title: "Maverick 10.10 KVM Live Migration"
date: 2010-11-25
forum: Virtualisation
---

### Post by adun153 on 2010-11-25
I'm trying to get live migration functioning on two test servers.
I've installed 10.10 amd64 server on both of them, and have followed the instructions in [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM) . The VM images are stored on one server, and the other server has the images on the same path via NFS. I just can't get it to work.
```

virsh # migrate --live UPLBV32 qemu+ssh://10.0.100.70/system
root@10.0.100.70's password: 
error: operation failed: migration to 'tcp:virtual2.local:49153' failed: migration failed

```that's what I get.
I've even disabled ufw on both servers, just to see if it was a firewall problem, but no luck there either.

Has anyone gotten live migration to work?
What are the instructions (or steps you took)?
Thanks!

---

### Post by TheR on 2010-11-28
Mostly all my live migrations (UBUNTU 10.04) that do not succeed are due to device (usually) cd-rom that is not available or attached at other node.

You may also look at /var/log/kvm || quemu (sorry I am writing at home) log files. Sometimes they are useful ;-)

by
TheR

---

### Post by adun153 on 2010-11-30
This is the /var/log/libvirt/qemu/UPLBV32.log entry the migration destination host creates:

LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/kvm -S -M pc-0.12 -enable-kvm -m 512 -smp 1,sockets=1,cores=1,threads=1 -name UPLBV32 -uuid fc12ac05-ed7c-8229-adac-100ad6735b6a -nodefaults -chardev socket,id=monitor,path=/var/lib/libvirt/qemu/UPLBV32.monitor,server,nowait -mon chardev=monitor,mode=readline -rtc base=utc -boot c -drive file=/var/lib/libvirt/images/disk1/UPLBVanilla32.img,if=none,id=drive-virtio-disk0,boot=on,format=raw -device virtio-blk-pci,bus=pci.0,addr=0x4,drive=drive-virtio-disk0,id=virtio-disk0 -device rtl8139,vlan=0,id=net0,mac=52:54:00:b6:1d:8d,bus=pci.0,addr=0x3 -net tap,fd=55,vlan=0,name=hostnet0 -chardev pty,id=serial0 -device isa-serial,chardev=serial0 -usb -vnc 127.0.0.1:0 -k en-us -vga cirrus -incoming tcp:0.0.0.0:49152 -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x5 
char device redirected to /dev/pts/1

It does not seem to indicate an error, but the migration source indicates that there was an error.

I just thought of something - Do you run your VMs and/or virsh as root?

---

### Post by TheR on 2010-12-03
Yes I do. It's a habit. 

by
TheR

---

### Post by adun153 on 2010-12-06
Can anybody else help? :)

---

