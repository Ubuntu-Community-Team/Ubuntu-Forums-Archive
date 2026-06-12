---
title: "&quot;ip route flush table main&quot; doesn't work correctly from rc.local?"
date: 2011-08-02
forum: Server Platforms
---

### Post by gleemer on 2011-08-02
Ubuntu Server 10.10


/etc/rc.local is running a script which starts like this:
```

ip route flush table main # clears any unwanted default routes

```The problem is for whatever reason this does not clear routes for interfaces configured to use DHCP. My first thought was that either the DHCP routes aren't in MAIN, or I was being protected from breaking my route to the DHCP server. However if I log into the machine and type the same flush command manually the routes for the DHCP interfaces do disappear.

The only way this makes sense to me is if rc.local is being executed before those routes are being written to the table. But as I understand things rc.local is among the last things done in the boot process...so that doesn't really make sense. What is going on here?


If it helps this script is for an oddball appliance I am building. In many scenarios the appliance will have two or more interfaces on the same subnet. One interface will act as the gateway and have

```
default via $GW dev $ADMIN_IFACE
SU.BN.ET.IP/24 dev $ADMIN_IFACE  proto kernel  scope link  src $ADMIN_IP
```for its routes. Any other interfaces on that subnet will have only a single route to a single IP address. Whether any of the interfaces are DHCP or static will vary machine to machine and is out of my control.

The rest of the script after, the "ip route flush" command builds the routing table that I need then applies a firewall. An alternate question to the "what is going on here?" is, is there someway for me to control the default routes linux creates so I don't have to flush and build my own every boot?

---

