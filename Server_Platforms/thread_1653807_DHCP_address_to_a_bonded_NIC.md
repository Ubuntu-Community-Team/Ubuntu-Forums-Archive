---
title: "DHCP address to a bonded NIC"
date: 2010-12-27
forum: Server Platforms
---

### Post by vortmax on 2010-12-27
I am attempting to get a bonded nic to take an address over dhcp.  I can get it to work fine on the command line, but not automatically.

here is my interfaces file:

```


# The loopback network interface
auto lo
iface lo inet loopback

#The bonded interface
auto bond0
iface bond0 inet dhcp
  pre-up modprobe bonding
  up    ifenslave bond0 eth0 eth1
  post-up dhclient bond0
  pre-down ifenslave -d bond0 eth0 eth1
  post-down rmmod bonding

```

the bonding alias is:
```

alias bond0 bonding
options bond0 mode=6 miimon=100

```

When the service starts, it brings up the bond and immediately runs dhclient to obtain an address.  The problem is that ifenslave has not run yet, so the bond still has the 00:00:00:00:00:00 mac address causing the dhcp discovery to fail.

However, if I change the ifenslave command to pre-up, then it errors out because the bond has to be up before being enslaved.  The workaround I found was to just call dhclient manually after forming the bond, but this causes the network to take a while to come back up, as it has to wait for the first instance of dhclient to time out.

So, is there a way to run a command between bringing up the interface and running dhclient?

---

