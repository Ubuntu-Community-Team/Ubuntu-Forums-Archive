---
title: "Two Network Interfaces, 10.4"
date: 2011-06-03
forum: Server Platforms
---

### Post by cpressland on 2011-06-03
Hi all,

Run into a bit of a weird issue on a new Ubuntu Sever 10.4 install. Setup the Network Interfaces file as follows:

[HTML]auto eth0
iface eth0 inet static
address 87.224.80.196
netmask 255.255.255.248
gateway 87.224.80.193

auto eth1
iface eth1 inet static
address 192.168.20.20
netmask 255.255.255.0
gateway 192.168.20.254
[/HTML]

Then rebooted the server, both interfaces are configured properly but I can only run one at a time. If both are running I cannot access anything but if I 'ifdown eth1' then eth0 functions properly, ditto for eth0 being down.

Any ideas?

Thanks

Chris

---

### Post by SeijiSensei on 2011-06-03
Remove the "gateway" directive for eth1.  That tells the OS where to send packets that don't match any local network addresses.  This traffic goes over eth0 to the ISP's router.  Packets for the 192.168.20.0/24 subnet will be handled by local broadcasts over the Ethernet.

While you're at it, make sure that the "net.ipv4.ip_forward" directive in /etc/sysctl.conf is set to one.  By default, forwarding across interfaces is disabled, so machines on the 192.168.20.0/24 subnet won't be able to access the Internet even if you have iptables correctly configured to masquerade your internal network.

You can test whether forwarding is enabled by typing "cat /proc/sys/net/ipv4/ip_forward".  If it returns zero, you can temporarily enable forwarding with "cat '1' > /proc/sys/net/ipv4/ip_forward", but that won't survive a reboot.  For that, you'll need to enable forwarding in /etc/sysctl.conf.

---

### Post by cpressland on 2011-06-03
Perfect, that seams to have done the job nicely. Server has come back online nicely and everything is working.

Last thing, running openssh over both nics. How'd I do that?

Change the 'listenaddress' in the sshd_config file to * or add two entires for both IPs?

Thanks in advance.

---

### Post by SeijiSensei on 2011-06-04
From "man sshd_config": The default is to listen on all local addresses.

Looking at the file, the default is equivalent to

```
ListenAddress 0.0.0.0
```

---

