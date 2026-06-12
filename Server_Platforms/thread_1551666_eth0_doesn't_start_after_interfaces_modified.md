---
title: "eth0 doesn't start after interfaces modified"
date: 2010-08-12
forum: Server Platforms
---

### Post by peridian on 2010-08-12
Hi,

I have three VMs (VMWare Server 2) all running Ubuntu Server 10.04.  (one I asked to be a samba share from the outset, the others are blank server installs, no pre-config)

I follow the layout in the community documentation regarding setting up firewall rules through iptables. I.e. I create a file called iptables.rules and place it in /etc.  I then modify the /etc/network/interfaces file to look like this:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
  pre-up iptables-restore < /etc/iptables.rules
  post-down iptables-restore < /etc/iptables.rules

```

This works just fine on two of the VMs (the samba and one of the blanks that I installed subversion on).

However this third one I have reinstalled Ubuntu 3 times now, and every time as soon as I modify the /etc/network/interfaces file, eth0 fails to start up (is not visible in ifconfig, only the loopback adapter), and no networking works.

I have tried reducing the iptables.rules file (which is a carbon copy across all machines anyway) to a basic accept all rule, and it still doesn't like it.  As soon as I remove those two extra lines in the interfaces file, the network starts up no problems and eth0 is there.

Anybody know why I might get this behaviour when the setup is identical to the other machines?

Regards,
Rob.

---

### Post by spynappels on 2010-08-13
This going to be a stupid question, but the file exists and there are no typos, either in the file or in the config file?

Also as a slight side point, why are you restoring the same set of rules when the interface goes down?

---

### Post by cdenley on 2010-08-13
Are you sure your virtual NIC is still eth0?
```

ifconfig -a

```
If the MAC address got changed for some reason, it would become eth1.
```

grep -B 1 '^[^#]' /etc/udev/rules.d/70-persistent-net.rules

```

---

