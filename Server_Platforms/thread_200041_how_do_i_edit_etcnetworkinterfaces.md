---
title: "how do i edit /etc/network/interfaces:"
date: 2006-06-19
forum: Server Platforms
---

### Post by konacoffeeguy on 2006-06-19
Hey, 
  I need to edit /etc/network/interfaces:    so I can add a static IP addresss to my server. I am trying to set my server up so I can just edit/login/configure things from my regular desktop. How do I edit this and is this what i should be editing? aslo, I don't like the vim editor, is there another better editor? 
 
Thanks, 
 Konacoffeeguy

---

### Post by icheyne on 2006-06-19
I like nano as a simple text editor.

---

### Post by henrikwidth on 2006-06-20
Hi

Try

```
sudo nano /etc/network/interfaces
```

edit what you need and then press ctrl+x, y then enter to save.

you can search with ctrl+w
you can save without quitting with ctrl+o
you can see on what line your cursor is with ctrl+c

dhcp example:
```

auto eth0
  iface eth0 inet dhcp
```

static ip example
```
auto eth0
  iface eth0 inet static
    address 192.168.0.1
    netmask 255.255.255.0
    broadcast 192.168.0.254
    gateway 192.168.0.10
```

good luck!

Best regards

Henrik

---

### Post by dac0nv1ct on 2006-07-18
Looking for which editor to use allso,thanks i'll try nano allso:)

---

