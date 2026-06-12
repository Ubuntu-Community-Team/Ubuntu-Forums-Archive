---
title: "virt-manager --connect qemu+ssh freezes"
date: 2009-03-23
forum: Virtualisation
---

### Post by ericvcard on 2009-03-23
I'm trying to install a KVM guest on a remote (headless) server running Ubuntu Server 8.10 (no Gnome, X...).

For that purpose I installed an Ubuntu Desktop 8.10 on my computer with Gnome and I could install a Fedora 9 guest on the Ubuntu server by running:

This command on the server:
```
sudo virt-install --connect qemu:///system -n $guest etc...
```

And this command on my computer:
```
sudo virt-viewer --connect qemu+ssh://root@xxx.xxx.xxx.xxx:22/system $guest
```

It went okay all the way through.

Now I'm trying to connect to the guest from my computer with this command:
```
sudo virt-manager --connect qemu+ssh://root@xxx.xxx.xxx.xxx:22/system
```

Witch launches the virt-manager, but when I enter the password it just freezes (program is not responding) and I have to do a 'force quit' to exit from it.

Any idea, what should I look for to make it work?

Thank you,
Eric.

---

