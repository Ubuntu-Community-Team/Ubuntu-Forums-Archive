---
title: "Virtual Machine Does not Recognise USB Port"
date: 2009-05-10
forum: Virtualisation
---

### Post by yazidarezki on 2009-05-10
Hello guys,
 
I have installed ubuntu version 9.04 and used KVM to get my VM. I have installed windows server 2008 and now the virtual machine does not ecognise the USB port. It always thinks that there is nothing there even when I insert an external hard drive. The ubuntu machine does but the VM, any ide why?
 
TIA
Yaz

---

### Post by albinootje on 2009-05-10
Afaik KVM is using (a modified ?) Qemu, see here what Qemu's help on the commandline shows :
```

$ qemu --help|grep usb
-usb            enable the USB driver (will be the default soon)
-usbdevice name add the host or guest USB device 'name'
----
QEMU PC emulator version 0.9.1, Copyright (c) 2003-2008 Fabrice Bellard [-> Using Ubuntu Hardy/8.04]

```
Could that be the reason ? Are you using a KVM GUI like virtmanager ? Does that GUI have settings for usb ?

---

### Post by yazidarezki on 2009-05-11
Yes, I am using KVM virtmanager GUI

---

