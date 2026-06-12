---
title: "External usb hard drive...Grrr"
date: 2008-02-06
forum: United Kingdom Team
---

### Post by g7mjv on 2008-02-06
Hi people

could some kind soul desipher the following dmesg output for me please. it's a drive that XP recognises ok

[11024.141532] Inbound IN=eth0 OUT= MAC=00:01:6c:e2:58:25:00:11:5b:ff:5e:b1:08:0                                           0 SRC=192.168.1.5 DST=192.168.1.4 LEN=90 TOS=0x00 PREC=0x00 TTL=128 ID=40127 PRO                                           TO=UDP SPT=137 DPT=32774 LEN=70
[11226.398993] usb 2-3: new full speed USB device using ohci_hcd and address 18
[11226.578921] usb 2-3: device descriptor read/64, error -62
[11226.862848] usb 2-3: device descriptor read/64, error -62
[11227.142763] usb 2-3: new full speed USB device using ohci_hcd and address 19
[11227.322706] usb 2-3: device descriptor read/64, error -62
[11227.606619] usb 2-3: device descriptor read/64, error -62
[11227.886534] usb 2-3: new full speed USB device using ohci_hcd and address 20
[11228.294392] usb 2-3: device not accepting address 20, error -62
[11228.470354] usb 2-3: new full speed USB device using ohci_hcd and address 21
[11228.878213] usb 2-3: device not accepting address 21, error -62
[11229.182136] usb 2-3: new full speed USB device using ohci_hcd and address 22
[11229.362080] usb 2-3: device descriptor read/64, error -62
[11229.645982] usb 2-3: device descriptor read/64, error -62
[11229.925890] usb 2-3: new full speed USB device using ohci_hcd and address 23
[11230.105851] usb 2-3: device descriptor read/64, error -62
[11230.389770] usb 2-3: device descriptor read/64, error -62
[11230.669676] usb 2-3: new full speed USB device using ohci_hcd and address 24
[11231.077533] usb 2-3: device not accepting address 24, error -62
[11231.253484] usb 2-3: new full speed USB device using ohci_hcd and address 25
[11231.661356] usb 2-3: device not accepting address 25, error -62
andy@:~$

---

### Post by pedro_orange on 2008-02-07
Hello fellow Salisbury-lite! 

Did a little bit of a search for you, came up with this launchpad bug report.

[https://answers.launchpad.net/ubuntu/+question/4272](https://answers.launchpad.net/ubuntu/+question/4272)

Try listing ur USB ports (lusb) to see if they're actually recognised by your system. Also, try all the ports.
A few people suggest things in this bug report, I don't know if any of them will work for you. But it may be a driver that has yet to be written for Ubuntu. 

To combat this, you could write your own driver (it's not as hard as it sounds) & there are plenty of tutorials online. Good luck!

---

### Post by g7mjv on 2008-02-07
Hi there, thanks ever so much for looking into the problem..

l eventually installed the storage device manager pysdm and managed to mount the usb lappy drive... Success :)

Andy - Salisbury, UK

---

