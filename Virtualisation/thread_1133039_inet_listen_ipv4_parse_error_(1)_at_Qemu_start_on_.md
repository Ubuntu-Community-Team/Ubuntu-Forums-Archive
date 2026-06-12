---
title: "inet_listen: ipv4 parse error (1) at Qemu start on remote server"
date: 2009-04-22
forum: Virtualisation
---

### Post by Weissbier on 2009-04-22
Hi, getting > inet_listen: ipv4 parse error (1) as result when i try to start a virtual image on my remote server with vnc output...

```
root@******:~# qemu-system-x86_64 -m 2048 -vnc 1 -usb -usbdevice tablet -boot c /home/virtualized/winxpsp3.img -net nic,vlan=0,model=virtio -net tap,vlan=0,ifname=tap0,script=no
inet_listen: ipv4 parse error (1)

```

It works on my local Ubuntu 8.04 version, but on the remote server it does not.

I use this command to run it from shell (its a fresh compiled default KVM-85 version btw):
```
qemu-system-x86_64 -m 2048 -vnc 1 -usb -usbdevice tablet -boot c /home/virtualized/winxpsp3.img -net nic,model=virtio -net tap,ifname=tap0,script=no
```

All bridges and tap devices are set-up same as on local computer and are working... also a IP-Tables rule to allow all traffic from Br0 is activated.

---

### Post by Weissbier on 2009-04-23
Problem Solved, instead of "-vnc 1" i should have rather used "-vnc :1" or "-vnc IPADRESS:MONITOR"

---

