---
title: "[SOLVED] Restart USB device WITHOUT unplug ?"
date: 2008-12-11
forum: Virtualisation
---

### Post by VMbuseck on 2008-12-11
Hello !

I have a AVM Fritz! USB ISDN modem connected to my server. Sometimes it happens, that the device is not responding in the VMware. In this case the unplugin and replugin makes it working again. Is it possible to do this with a simple command line call without removing the cable ?  

A first try I did:

```
#! /bin/sh
rmmod -f uhci_hcd
sleep 5s
insmod "/lib/modules/`uname -r`/kernel/drivers/usb/host/uhci-hcd.ko"
```

/var/log/messages (aCanon i455 and the AVM Fritz! ISDN are connected):

```
Dec 11 14:05:23 srvbonn kernel: uhci_hcd 0000:00:07.2: remove, state 1
Dec 11 14:05:23 srvbonn kernel: usb usb1: USB disconnect, address 1
Dec 11 14:05:23 srvbonn kernel: usb 1-1: USB disconnect, address 2
Dec 11 14:05:23 srvbonn kernel: drivers/usb/class/usblp.c: usblp0: removed
Dec 11 14:05:23 srvbonn kernel: usb 1-2: USB disconnect, address 3
Dec 11 14:05:23 srvbonn kernel: uhci_hcd 0000:00:07.2: USB bus 1 deregistered
Dec 11 14:05:28 srvbonn kernel: USB Universal Host Controller Interface driver v3.0
Dec 11 14:05:28 srvbonn kernel: PCI: Enabling device 0000:00:07.2 (0000 -> 0001)
Dec 11 14:05:28 srvbonn kernel: PCI: Found IRQ 10 for device 0000:00:07.2
Dec 11 14:05:28 srvbonn kernel: uhci_hcd 0000:00:07.2: UHCI Host Controller
Dec 11 14:05:28 srvbonn kernel: uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
Dec 11 14:05:28 srvbonn kernel: uhci_hcd 0000:00:07.2: irq 10, io base 0x0000e000
Dec 11 14:05:28 srvbonn kernel: usb usb1: configuration #1 chosen from 1 choice
Dec 11 14:05:28 srvbonn kernel: hub 1-0:1.0: USB hub found
Dec 11 14:05:28 srvbonn kernel: hub 1-0:1.0: 2 ports detected
Dec 11 14:05:28 srvbonn kernel: usb 1-1: new full speed USB device using uhci_hcd and address 2
Dec 11 14:05:29 srvbonn kernel: usb 1-1: configuration #1 chosen from 1 choice
Dec 11 14:05:29 srvbonn kernel: drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04A9 pid
   0x108A
Dec 11 14:05:29 srvbonn kernel: usb 1-2: new full speed USB device using uhci_hcd and address 3
Dec 11 14:05:29 srvbonn kernel: usb 1-2: configuration #1 chosen from 2 choices
```

During unplug und replug:

```
Dec 11 14:10:08 srvbonn kernel: usb 1-2: USB disconnect, address 3
Dec 11 14:10:18 srvbonn kernel: usb 1-2: new full speed USB device using uhci_hcd and address 4
Dec 11 14:10:18 srvbonn kernel: usb 1-2: configuration #1 chosen from 2 choices
```

Why it won`t work with the script ???

Greetings M.

---

### Post by VMbuseck on 2008-12-19
_Update:_ 

The script works in the case, that only **one** device (the Fritz!Card) is connected.

Why not, if there are more devices ?

---

### Post by Dedoimedo on 2008-12-19
Instead of using rmmod, try modprobe -r.
modprobe will also unload all the dependencies for this module.

[http://linux.die.net/man/8/modprobe](http://linux.die.net/man/8/modprobe)

Dedoimedo

---

### Post by VMbuseck on 2008-12-22
> Instead of using rmmod, try modprobe -r.

That solves the problem ! Thanks a lot !

---

### Post by Dedoimedo on 2008-12-22
Glad to be of help.
You can mark the thread as solved.
Dedoimedo

---

