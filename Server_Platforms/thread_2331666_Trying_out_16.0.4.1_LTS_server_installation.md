---
title: "Trying out 16.0.4.1 LTS server installation"
date: 2016-07-24
forum: Server Platforms
---

### Post by MakOwner on 2016-07-24
Loading up 16.04.1 on a headless test server to try out before using it for anything critical:

```

0000:05:00.0 enp5s0: renamed from eth0

```

Really?  Is there really any technical advantage in renaming an interface?

The second interface on this box gets renamed to enp6s0.

Placing this in /etc/network/interfaces should enable the second interface on the specified static address.

```

# The backup network interface
auto enp6s0
iface enp6s0 inet static
address 192.168.25.6
network 192.168.25.0
netmask 255.255.255.0
broadcast 192.168.25.255

```

It does not.


mdadm bootdegraded is borked - I see that someone posted a fix for this that involves replacing stuff that was left out from upstream.


Anyway to overcome the network feature?

---

### Post by howefield on 2016-07-24
Moved to the "*Server Platforms*" forum.

---

### Post by Bashing-om on 2016-07-24
MakOwner; Hello;

See:
[https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)
for the rational for the naming change convention.

As to your config file, is not the dns-nameserves line also required ? :
for example:
> 
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
#auto enp6s0
#iface  enp6s0 inet dhcp
auto enp6s0
iface eth0 inet static
	address 192.168.1.99
	netmask 255.255.255.0
	gateway 192.168.1.1
	dns-nameservers 8.8.8.8 192.168.1.1


[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

### Post by darkod on 2016-07-24
Double check the interface names with:
```
sudo lshw -short | grep network
```

After you have the correct, your setup in /etc/network/interfaces should work. You don't need to use the 'network' and 'broadcast' parameters, I never use them. They are calculated automatically from the address/netmask combination. Further more, I've seen people making an error or typo in network/broadcast and that's why it didn't work.

In your case what you posted is correct and should work. Just double check the interface name.

---

### Post by MakOwner on 2016-07-24
> **howefield said:**
> Moved to the "*Server Platforms*" forum.

Thank you for moving the thread.

---

### Post by MakOwner on 2016-07-24
> **Bashing-om said:**
> MakOwner; Hello;

See:
[https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)
for the rational for the naming change convention.

As to your config file, is not the dns-nameserves line also required ? :
for example:


[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

DNS is supplied on the primary interface -- the interface in question is a physically segregated backup-traffic only network and won't have access to a DNS server.
Would that line still be required?

---

### Post by darkod on 2016-07-24
No, it wouldn't. For additional interfaces usually address and netmask are enough. Assuming you get the interface name correctly, you set the correct IP and netmask, and the cable connections are working, that's all you need...

---

### Post by MakOwner on 2016-07-25
> **darkod said:**
> No, it wouldn't. For additional interfaces usually address and netmask are enough. Assuming you get the interface name correctly, you set the correct IP and netmask, and the cable connections are working, that's all you need...

```

0000:05:00.0 enp5s0: renamed from eth0
0000:06:00.0 enp6s0: renamed from eth1

```

eth0 is renamed enp5s0 comes up at boot.
eth1 is renamed enp6s0.  

Everything for eth0 and eth1 look identical right up to the point where enp6s0 is just never enabled.

It's like the /etc/network/interfaces file is ignored.



Another bit of information:
if-up.d/upstart ends with this if statement:

```

if all_interfaces_up "${MARK_DEV_PREFIX}" &&
	mkdir "${MARK_STATIC_NETWORK_EMITTED}" 2>/dev/null; then
	initctl emit --no-wait static-network-up
fi

```


If i try to execute this as root I get this:
```

root@PE850-04:/etc/network# initctl emit --no-wait static-network-up
The program 'initctl' is currently not installed. You can install it by typing:
apt install upstart

```

Granted the environment may not be the same as at startup, but if initctl is a valid program or script.

initctl is installed and available to root on an LTS 14.04.4 server with the same configuration as this one...

---

### Post by darkod on 2016-07-26
Where did you actually get the image? I am asking because you say 16.04.1 which is not released yet. It should be in august. I think only 16.04 has been released so far, not the first .1 release.
If you downloaded a development iso it mightbe a bug but I also doubt that because it works ok on 16.04. I have tried it.
Can you post the full /etc/network/interfaces file?
And this is the server release with no gui installed right?

---

### Post by MakOwner on 2016-07-26
> **darkod said:**
> Where did you actually get the image? I am asking because you say 16.04.1 which is not released yet. It should be in august. I think only 16.04 has been released so far, not the first .1 release.
If you downloaded a development iso it mightbe a bug but I also doubt that because it works ok on 16.04. I have tried it.
Can you post the full /etc/network/interfaces file?
And this is the server release with no gui installed right?

I got it from the Ubuntu download page, server image link.  I'll go look for the exact link.
It is a server image install with no GUI - just the standard utilities and ssh server selected on software options form.
It does report 16.0.4.1 on the login banner

```

Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 4.4.0-31-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

0 packages can be updated.
0 updates are security updates.

```


Here is the link to the server image download - it's offering 16.04.1 as the default image:
[http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server)



And, just for everyone's edification, the interface is functional - I can manually start it, it just doesn't come up during boot:

```

# ethtool enp6s0
Settings for enp6s0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: Symmetric
	Advertised auto-negotiation: Yes
	Speed: Unknown!
	Duplex: Unknown! (255)
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: g
	Wake-on: d
	Current message level: 0x000000ff (255)
			       drv probe link timer ifdown ifup rx_err tx_err
	Link detected: no

```

---

### Post by darkod on 2016-07-26
My bad, it really is released. Past years it was in August so I took it for granted that this year too.

I have the 16.04 on few test machines and my network setup works as expected. Not sure what could be wrong with yours unfortunately. I actually have second interface on couple of those test machines and it works fine. Just like you have it set up...

---

