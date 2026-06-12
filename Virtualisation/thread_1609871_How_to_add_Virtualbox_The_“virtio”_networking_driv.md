---
title: "How to add Virtualbox The “virtio” networking drivers to Ubuntu guest?"
date: 2010-10-30
forum: Virtualisation
---

### Post by samsonluk on 2010-10-30
I am running Ubuntu 10.04 Desktop guest in Virtualbox from a Windows XP host, what procedures are required to add the  “virtio” networking drivers to Ubuntu guest so that I can select “Paravirtualized network adapter (virtio-net)“ for use with the Ubuntu guest machine in Virtualbox so as to improve network transfer performance.  Thanks!

---

### Post by eblume on 2010-11-01
Is it not working out of the box? Using Ubuntu 10.04 AMD64 Server, I *believe* that my virtualized networking device is virtio. I can't recall the command that checks this.

---

### Post by samsonluk on 2010-11-01
I am using desktop, it seems that I need to 'modprobe virtio' then add virtio to /etc/modules in order to get the kernel module reload upon reboot.  It's working now, thanks!

---

