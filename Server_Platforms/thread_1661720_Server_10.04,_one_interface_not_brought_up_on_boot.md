---
title: "Server 10.04, one interface not brought up on boot"
date: 2011-01-07
forum: Server Platforms
---

### Post by NIT006.5 on 2011-01-07
Hi all,

I'm having an odd problem with Server 10.04. I have two interfaces but only one interface is brought up on boot - and it's not always the same interface. Usually eth0 fails and eth1 comes up fine, but sometimes eth1 fails and eth0 comes up. I'm using the same config that was previously used on Server 8.04, but never had this problem on 8.04. 

/etc/network/interfaces:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The LAN interface
auto eth0
iface eth0 inet static
	address 10.0.0.1
	netmask 255.255.255.0
	network 10.0.0.0
	# gateway
	pre-up iptables-restore < /etc/iptables.save

# The public network interface
auto eth1
iface eth1 inet static
	address 192.168.0.100
	netmask 255.255.255.0
	network 192.168.0.0
	gateway 192.168.0.1
	pre-up iptables-restore < /etc/iptables.save

```

(At the moment its running in a test environment, so both interfaces are "internal" networks)

ifconfig -a

```

eth0      Link encap:Ethernet  HWaddr f4:ce:46:e6:65:68  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::f6ce:46ff:fee6:6568/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1615 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2864 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:154002 (154.0 KB)  TX bytes:286195 (286.1 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 1c:af:f7:08:22:c2  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:615455 (615.4 KB)  TX bytes:615455 (615.4 KB)

```

Once the system has booted, if I run /etc/init.d/networking restart, then both interfaces come up fine. However, having read that this is now an upstart, I also tried service networking restart, but get:

```

restart: Unknown instance:

```

Don't know if that's significant or not.

Cannot find a single problem with networking reported in log files, other than bound services failing to start as a result of the interface not being up (dansguardian, squid, dhcp which are all bound to eth0, and therefore fail when eth0 doesn't come up. And when eth1 doesn't come up, the only process that fails to run is clamav-freshclam). Although at one point I did see something about interfaces being renamed which seemed a little odd.

I could just have networking restarted automatically once booted, but this obviously isn't a solution to whatever is causing the problem. There is quite a bit running on the server: Samba/LDAP domain controller with roaming profiles, squid & dansguardian with LDAP auth, postfix & dovecot with LDAP auth, mailscanner, dhcp & ddns, strict iptables policy with nat... so I'm not sure if any of those could have any bearing on interfaces?

Any help appreciated.

---

### Post by NIT006.5 on 2011-01-07
Solved. For some reason this was being caused by the firewall being loaded for each interface. If I only load the firewall for one interface, no problem. However, while the immediate problem is solved, this only raises more questions in my mind.

---

