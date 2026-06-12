---
title: "KVM Switch Error"
date: 2009-01-02
forum: Server Platforms
---

### Post by trentscott4 on 2009-01-02
I'm running Server 8.10 (linux-2.6.27) on two separate boxes connected via a 2-port USB KVM switch and receive the following error on boot:


[ 55.498350 ] /build/buildd/linux-2.6.27/drivers/hid/usbhid/hid-core.c: couldn't find an input interrupt endpoint

[ 86.458358 ] /build/buildd/linux-2.6.27/drivers/hid/usbhid/hid-core.c: couldn't find an input interrupt endpoint

Here's the Launchpad post: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213895](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213895)

So far this issue is unresolved, any thoughts?

---

### Post by gwachtel on 2009-02-17
I get the same error messages when connecting with a usb kvm switch, but aside from that everything seems to work.

---

### Post by linux_tech on 2009-02-17
does kvm use a power adapter?

---

### Post by haddog on 2009-02-17
No issues with a 'standard' 4 port belkin switch. By standard I mean each output has mouse/keyboard/monitor. KVM has it's own ps.

---

### Post by mikeabout on 2009-07-28
Confirming that this still happens in server 9.04 (linux 2.6.28-13-server) with a TRENDnet TK-207K 2 port USB KVM.  This particular KVM does not have a power adapter.  

This doesn't seem to cause any other problems, but...

[80580.380072] generic-usb 0003:10D5:55A2.001B: input,hidraw2: USB HID v1.10 Keyboard [No brand 2Port KVMSwicther] on usb-0000:00:1d.1-1.3/input0

[80580.385896] usbhid 3-1.3:1.1: couldn't find an input interrupt endpoint

---

### Post by vpadro on 2009-07-28
I've got the same messages since Ubuntu 7.04, even in Debian/CentOS occurs the same, I haven't had any uncomfortable issues though.

---

