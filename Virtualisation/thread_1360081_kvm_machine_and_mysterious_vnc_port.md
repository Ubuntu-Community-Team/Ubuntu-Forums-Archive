---
title: "kvm machine and mysterious vnc port"
date: 2009-12-20
forum: Virtualisation
---

### Post by aleb on 2009-12-20
I have a kvm virtual machine. In virt-manager I see that it has the following device: 
```
Virtual Display
Type: VNC server
Address: 127.0.0.1
Port: 2
```

I expect that I can connect to it by running the following command, but it does not work:
```
xtightvncviewer 127.0.0.1:2
```
(ps aux | grep kvm) shows the following:
```
... /usr/bin/kvm ... -vnc 127.0.0.1:-5898 -vga cirrus
```

I also tried to connect like this, but it still does not work:
```
xtightvncviewer 127.0.0.1::5898
```

Why is it using "-5898" instead of "2"?
And what exactly does the - in front of 5898 mean?

EDIT: This one works: xtightvncviewer 127.0.0.1::2

---

