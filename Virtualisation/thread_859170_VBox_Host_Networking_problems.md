---
title: "VBox Host Networking problems"
date: 2008-07-14
forum: Virtualisation
---

### Post by astabeno on 2008-07-14
I have been using Virtual Box with Host networking almost flawlessly on Ubuntu with for around 6 months.  I have Ubuntu 8.04 as my host and Windows XP as my guest.  Last week I switched my computer to a static IP to test some stuff on another network and when I switched back I had to had to change my interfaces file back to a generic killing all bridged networking, reboot, and then rebuild the interfaces file with the bridged networking and then restart networking.  Then I ran the VBoxAddIF commands to rebuild the VirtualBox adapters and everything worked fine.  Not a problem for one time, but now every time I reboot my host internet does not work until I repeat the steps above.  The guest networking works fine. Below is the contents of my /etc/network/interfaces.  Please tell me what I have done wrong.

```

auto lo
iface lo inet loopback

auto eth0

auto br0
iface br0 inet dhcp
	bridge_ports eth0

```

---

