---
title: "KVM networking"
date: 2008-02-02
forum: Virtualisation
---

### Post by aBitLater on 2008-02-02
Hello,

I've installed kvm and am installing the guest OS (winxp) as I write this.  I've followed some tutorials on the networking setup, but I'm pretty sure they don't cover my scenario.

my laptop uses DHCP to get an IP address, and my router (DHCP server) assigns the specific IP to the laptop based on the laptop's MAC address (it always uses the same IP address, 192.168.1.105).

1.) how do I avoid having the guest OS trying to get assigned the same IP address from the router?

I had modified these files, per HOWTO's: /etc/network/interfaces and /etc/qemu-ifup but now interfaces is nothing like what I had modified it to be, and qemu-ifup is no longer existing in the /etc directory... dunno what happened there!  

The Howto at [http://www.howtoforge.com/using-kvm-on-ubuntu-gutsy-gibbon](http://www.howtoforge.com/using-kvm-on-ubuntu-gutsy-gibbon) suggested changing these files as such, where I had substituted 
address, netmask, and gateway with my main OS (ubuntu) ip number, netmask, and router as gateway.  But, like I said, these appear to have been over-written somewhere along the line.
 
/etc/network/interfaces
```

auto lo
iface lo inet loopback
auto br0
iface br0 inet static
address xxx.xxx.xxx.xxx
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx
bridge_ports eth0
bridge_stp off
bridge_maxwait 5

```

```

#!/bin/sh
/sbin/ifconfig $1 0.0.0.0 promisc up
/usr/sbin/brctl addif br0 $1
sleep 2

```

This is what my current /etc/network/interfaces file looks like:
```

auto lo
iface lo inet loopback




iface eth0 inet dhcp

auto eth0


```

2.) Can I make the qemu/kvm window bigger? I want it to run full screen, but right now (on install of winxp) it is about 1/4 my screen size.

---

### Post by SuperBOB on 2008-04-08
1.) how do I avoid having the guest OS trying to get assigned the same IP address from the router?


The router will assign a unique address to each device requesting a DHCP pack.  

If you are using another form of DHCP which looks up your MAC address and assigns the same IP each time, then try specifying a MAC address when booting the VM to avoid any chance of a duplication.

It would be easier to help if you state what type of network you are trying to achieve.  Use the Ubuntu KVM page to see the possible ways it could work for you.

2.) Can I make the qemu/kvm window bigger? I want it to run full screen, but right now (on install of winxp) it is about 1/4 my screen size.[/QUOTE]

You can connect and interact with your VM through a few means, which are you using?  If it is through the 'default' method Ctrl+Alt+F should full screen it, then change the resolution in the guest operating system to suit your requirements.

---

