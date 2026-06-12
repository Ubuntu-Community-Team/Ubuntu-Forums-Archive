---
title: "Virt Manager and using remote hosts over SSH - X windows STALL"
date: 2020-03-26
forum: Virtualisation
---

### Post by jakkuk on 2020-03-26
Hey!

I'm using this setup for years:
[LIST]
[*]I have a number of physical hosts with Ubuntu 18.04 and KVM VMs
[*]each KVM VM host hosts about 4 to 8 VMs
[*]my host is ubuntu 19.10
[*]everything updated to the latest pach sets
[*]my host connects through OpenVPN to the network with the VM hosts.
[*]I have a virt-manager setup that uses SSH to connect to these KVM hosts
[*]
[/LIST]

So when I launch virt-manager and it connects to all VM hosts and gets all VM details the X environment of my machine just stalls until virt-manager is done with its thing. Remember the times of Windows 98, single thread CPUs and loading the CDROM? That's exactly that. Once it gets all data from remote hosts, I can work.

What looks like the main problem is that the gnome-shell process starts using all of it's CPU core, when virt-manager builds its UI with data from the remote hosts.

Tried googling for solutions, and people seem to have problems with this, but I found zero solutions. 

I'm using Xorg and nvidia binary drivers.

I understand, that there might be some networking issue that makes the virt-manager wait for something too long, but still this should not stall the X environment.

Any ideas what I can look into?

---

### Post by jakkuk on 2020-03-26
I've found a workaround.

You need to disable the tray icon of virt-manager within its options. This makes the problem go away.

[https://github.com/ubuntu/gnome-shell-extension-appindicator/issues/199](https://github.com/ubuntu/gnome-shell-extension-appindicator/issues/199)

I guess I've used this forum as a rubber ducky. Maybe someone will find this helpfull in the future...

---

