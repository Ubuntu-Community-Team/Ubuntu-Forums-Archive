---
title: "Cannot connect to internet"
date: 2012-02-26
forum: Server Platforms
---

### Post by jdawgvh on 2012-02-26
Aaaah!  Please help.  My Ubuntu server (11.10) has been running for several months.  I decided to do an update on it yesterday and now I regret it.  The update didn't require a restart and I was right in the middle of transferring some files to the server.  The server shuts itself off at night if it detects no network traffic.  This morning when I started the server up from my client (gWakeOnLan) i saw it start up but I could not find it on my network from the client.  It's headless so I had to dig up my monitor and keyboard from the garage and get them hooked up to do some troubleshooting.  During the startup sequence I got a

rpcbind: cannot open '/run/rpcbind/rpcbind.xdr' file for reading, errno 2 (no such file or directory)
rpcbind: cannot open '/run/rpcbind/portmap.xdr' file for reading, errno 2 (no such file or directory)

Then the computer did the no network configuration found thing.  I cannot connect to the internet or to my network.  My /etc/network/interfaces file is fine.  I do use NFS but I figured I could reinstall it if RPCBind was keeping me from connecting so I uninstalled RPCBind.  Still no joy.  When I do an

sudo ifconfig -a

my two network cards both say that they are disabled.  I'm not sure where to go from here or what to do.

---

### Post by zeljkojagust on 2012-02-27
Start with executing the following command:
```
sudo ethtool eth0
```

Check the last line "Link detected", is it saying yes or no. If it's no, check your cables. Also did you have bonding configured on your adapters? Or did you install network-manager when installing last set of updates, it can screw up network connections.

---

### Post by jdawgvh on 2012-03-01
Here is what I've got:

> Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: Symmetric
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: Symmetric Receive-only
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: g
	Current message level: 0x00000007 (7)
			       drv probe link
	Link detected: yes
Settings for eth1:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: Symmetric Receive-only
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: no


The cables are definitely connected for both adapters though.

Here is what I had for /etc/network/interfaces
> auto lo
iface lo inet loopback

auto bond0
iface bond0 inet dhcp
netmask 255.255.255.0
gateway 192.168.1.254
slaves eth0 eth1


I might have installed network-manager but it wasn't on purpose.  I don't know how to check what was installed with each update.

---

