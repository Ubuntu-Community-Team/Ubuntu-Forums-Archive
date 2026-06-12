---
title: "(kvm) did not claim interface 1 before use"
date: 2008-12-22
forum: Virtualisation
---

### Post by schoonbee on 2008-12-22
Hi,

I'm trying to pass-thu my iPod touch to my XP kvm using virt-manager:

When I attach to my monitor session I get:
```

(qemu) info usbhost
  Device 7.27, speed 480 Mb/s
    Class 00: USB device 05ac:1291, iPod
..
  Device 3.19, speed 12 Mb/s                                                                                                                      
    Class ef: USB device 0bb4:0b0b, Generic RNDIS                                                                                                 
..
(qemu) usb_add host:3.19                                                                                                                          
(qemu) usb_add host:7.27                                                                                                                          
Could not add USB device 'host:7.27'                                                                                                              
(qemu) 


```


```

sudo tail /var/log/libvirt/qemu/vmxp1.log
[sudo] password for derick: 
/usr/bin/kvm -M pc -m 1024 -smp 1 -monitor pty -localtime -no-acpi -drive file=/home/derick/libvirt/disks/vmxp1.img,if=ide,boot=on -net nic,macaddr=00:16:3e:48:4a:fd,vlan=0 -net tap,fd=11,script=,vlan=0 -usb -usbdevice tablet -vnc 127.0.0.1:0 
char device redirected to /dev/pts/1
usb_linux_update_endp_table: No such file or directory

```

```

tail /var/log/messages
..
Dec 22 17:52:48 derick-laptop kernel: [192686.330512] eth1: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, 80:00:60:0f:e8:00
Dec 22 17:54:53 derick-laptop kernel: [192736.315350] eth1: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
Dec 22 17:55:04 derick-laptop kernel: [192739.712693] usb 7-2: usbfs: process 4467 (kvm) did not claim interface 1 before use
..

```

Thus, does a usb device (eg. 7.2) need to be 'claimed' before used in qemu/kvm? How can I do that?

How come that 3.19 worked and not 7.2? If it is occupied, or loaded some drivers, how can I see which ones and unload... or am I missing something here?

All this, just to get my iPod Touch to sync.... sigh...

---

### Post by schoonbee on 2008-12-23
Ok, so I installed VirtualBox 2.1.0 and iTunes + iPod sync works fine.

So I assume that my kernel as the "potential" to do it ;)

But, I prefer KVM.

Does anyone have some hints, suggestions? Or could this be a bug in the KVM/Qemu code? I've seen some people patching the usb code of qemu/kvm.

---

### Post by schoonbee on 2009-01-21
Ok, did not like Virtual Box, back to kvm. Still the same problem.

Does anyone have any idea where to look? Is it because the host does not load the usb device properly? Or does the kvm process not care when passing through a device?

---

### Post by www.rzr.online.fr on 2009-04-07
Actually it seems that kvm do not support usb2 :

[http://www.mail-archive.com/kvm@vger.kernel.org/msg05534.html](http://www.mail-archive.com/kvm@vger.kernel.org/msg05534.html)

-- 
[http://rzr.online.fr/q/qemu](http://rzr.online.fr/q/qemu)

---

