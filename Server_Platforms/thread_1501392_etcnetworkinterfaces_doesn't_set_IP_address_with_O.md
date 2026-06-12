---
title: "/etc/network/interfaces doesn't set IP address with OpenVZ on hardy"
date: 2010-06-04
forum: Server Platforms
---

### Post by gnutered on 2010-06-04
I'm building up a server based on 8.04 LTS.  It's using OpenVZ, and as part of that it creates a virtual network interface venet0.  I add a stanza to /etc/network/interfaces that looks like this:

```

allow-hotplug venet0
iface venet0 inet static
	address 10.53.35.1
	netmask 255.255.255.0

```

It's similar to what sets the static addressing for eth0.  But it doesn't stick.  When I reboot the machine, venet0 is there, but no IP address is set:

```

$ ip addr list
...
3: venet0: <BROADCAST,POINTOPOINT,NOARP,UP,LOWER_UP> mtu 1500 qdisc noqueue 
    link/void 

```

To get it working, I can run:

```

ifup venet0

```

But until I do this, there is no virtual networking, and therefore my OpenVZ guests cannot use networking.

Any clues as to what's up?  I have other machines running on Debian (lenny) and this is not a problem.

Looking further, I note that /etc/init.d/networking is not symlinked into anything other than the rcS.d directory.  It's been a while since I've been tinkering at this level, but I understand that there should be a symlink from rc2.d/Sxxnetworking into ../etc/init.d/networking.  So I wonder where eth0 is getting configured.

Any help appreciated.

Tony

---

### Post by Iowan on 2010-06-04
I'm not familiar with OpenVZ, but try adding "auto venet0" to */etc/network/interfaces *.

---

### Post by YorYor on 2010-06-19
Why aren't you assigning IP addresses to the individual guests/containers? Once you assign IP(s), and net.forwarding is on, the guests/containers will then have networking.

---

