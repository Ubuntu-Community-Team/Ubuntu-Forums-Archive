---
title: "Routing problems when using PPPoE connection"
date: 2017-02-10
forum: Server Platforms
---

### Post by wombatlbn on 2017-02-10
Hello,

I have home server controlled by Ubuntu 14.04. It has three network interfaces: eth0, eth1 and wlan0. eth0 is considered as external port, as is connected with my ISP router. eth1 and wlan0 are bridged for LAN. Some time ago, I changed my ISP to other and now there is another router and ONT as new connection is optic. ISP router is now pretty much useless and just wasting energy, so i decided to connect ONT directly with my server. After reconfiguration including switching external interface in IPtables from eth0 to ppp0, everything seems to work great. Not really. There are serious connection problems for HTTP traffic from LAN computers. Some websites loads very slowly, other cannot load at all. From server itself, all websites loads perfectly so I guess there is some routing problem not in connection, or maybe not?

More detailed info is here: [http://serverfault.com/questions/828934/http-traffic-slow-or-unreachable-when-using-ppp-connection](http://serverfault.com/questions/828934/http-traffic-slow-or-unreachable-when-using-ppp-connection) - my question, sadly, no answer. Maybe here somebody will know whats wrong?

---

### Post by darkod on 2017-02-10
Are you sure the connection to the ISP is stable as it is? Routers preconfigured by the ISP (plug&play) usually have more settings that are needed for good connection. Not always you can simply disconnect them and connect PPPPOE directly on a computer if you don't have all the details of their setup.

---

### Post by wombatlbn on 2017-02-13
> **darkod said:**
> Are you sure the connection to the ISP is stable as it is?
Yes. From server point, everything is working fine. Even when i connect ONT to completely other PC with linux, configure connection same way as on server, connection is fully functional, all websites are working, pings are low and data transfer is high enough. So, that's why i think there is a routing problem not a connection problem.

---

### Post by darkod on 2017-02-13
Please post the /etc/network/interfaces of the server. And the outputs of:
```
cat /etc/sysctl.conf | grep 'forward'
sudo iptables -L -n -v
sudo iptables -t nat -L -n -v
```

---

### Post by wombatlbn on 2017-02-21
Sorry for late reply, but just had no time to spend on this.
Network interfaces configuration is posted on serverfault, but i will paste it here as well. Interfaces when using ISP router:
```
auto lo
iface lo inet loopback


allow-hotplug eth0        # TO ISP
iface eth0 inet static
address 10.1.2.4
netmask 255.255.255.0
network 10.1.2.0
broadcast 10.1.2.255
gateway 10.1.2.3


allow-hotplug eth1        # CABLE LAN
iface eth1 inet manual


allow-hotplug wlan0       # WiFi LAN
iface wlan0 inet manual   


auto zbr0                 # Bridge Wifi-Cable LAN
iface zbr0 inet static
bridge_ports eth1
address 192.168.1.11
netmask 255.255.255.128
network 192.168.1.0
broadcast 192.168.1.127
dns-nameservers 192.168.1.11
```

And with changes to work with directly connected ONT:
```
auto lo
iface lo inet loopback


allow-hotplug eth0
iface eth0 inet manual


auto eth0.35
iface eth0.35 inet manual
       vlan_raw_device eth0


allow-hotplug eth1
iface eth1 inet manual


allow-hotplug wlan0
iface wlan0 inet manual


auto zbr0
iface zbr0 inet static
bridge_ports eth1
address 192.168.1.11
netmask 255.255.255.128
network 192.168.1.0
broadcast 192.168.1.127
dns-nameservers 192.168.1.11
```

And results of three requested commands in respective order:
```
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1
# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1
```
```
Chain INPUT (policy ACCEPT 16872 packets, 1287K bytes) pkts bytes target     prot opt in     out     source               destination
  283 17914 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
19612 4629K ACCEPT     all  --  eth0   *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
    0     0 ACCEPT     udp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            udp dpt:1199
  196 10344 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:449
 4943  352K DROP       all  --  eth0   *       0.0.0.0/0            0.0.0.0/0


Chain FORWARD (policy ACCEPT 1645K packets, 1635M bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  eth0   eth1    0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
    0     0 ACCEPT     all  --  eth1   eth0    0.0.0.0/0            0.0.0.0/0


Chain OUTPUT (policy ACCEPT 37706 packets, 3977K bytes)
 pkts bytes target     prot opt in     out     source               destination
```

```
Chain PREROUTING (policy ACCEPT 26811 packets, 2806K bytes) pkts bytes target     prot opt in     out     source               destination


Chain INPUT (policy ACCEPT 9938 packets, 662K bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 12315 packets, 831K bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain POSTROUTING (policy ACCEPT 2319 packets, 444K bytes)
 pkts bytes target     prot opt in     out     source               destination
22286 2240K MASQUERADE  all  --  *      eth0    0.0.0.0/0            0.0.0.0/0
```

iptables results are of course for connection via ISP router, but after switching to direct ONT connection im changing them only by switch 'external' interface from eth0 to ppp0. Actually i cannot unfortunately physically switch configurations, so cant post exact iptables dump when using ppp0.

---

### Post by darkod on 2017-02-21
To be honest I'm not sure how should you configure this. You have forwarding enabled in sysctl.conf and the iptables rules are correct, including the MASQUERADE rule. That is enough for linux routing to work.

But on the NIC setup, I am lost between all the interfaces and parameters you have. For example the zbr0 bridge has only eth1 included, so what are you bridging exactly?

Also, I have never used allow-hotplug, is there a reason you prefer this over auto? Can that create issues by dropping your connections?

You seem to have a very complex setup, with many interfaces (not just one external and one internal), and on top of that you are trying replacing the ISP router with your own configuration. It's obvious there is something missing in it. But I wouldn't know what simply by looking at this.

Maybe if you try simpler setup to start with, like only one interface towards ISP and one towards local LAN. If you get that working and stable, you will know the PPPoE part is OK.

After that you can start testing with the other interfaces, and you will see when things stop working so you will have more clues where to look...

---

