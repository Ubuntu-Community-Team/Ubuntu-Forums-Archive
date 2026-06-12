---
title: "Cannot get Updates via apt-get update or Ping Outside of Local Network"
date: 2016-10-30
forum: Server Platforms
---

### Post by dbreez3 on 2016-10-30
Fresh Ubuntu Server 16.04.1 LTS using UFW. Cannot get updates and ping won't work. Having an incredibly hard time hunting down a reason for this to be happening...:confused:

**Note:** I can SSH in no problem.

**sudo apt-get update**:
```
0% [Connecting to archive.ubuntu.com (91.189.88.162)] [Connecting to security.ubuntu.com (91.189.88.161)]
```

**cat /etc/network/interfaces**:
```
# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto enp2s0
iface enp2s0 inet dhcp
```

Running **ping -c 4 8.8.8.8**:
```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

--- 8.8.8.8 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3023ms
```

And I can see the ping requests being allowed out in the UFW log.

Results of **sudo lshw -C network**:
```
*-network       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: c0
       serial: 90:2b:34:60:85:89
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=192.168.1.157 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:25 memory:fddc0000-fddfffff ioport:df00(size=128)
```

Any help or pointers would be greatly appreciated, thanks.

---

### Post by darkod on 2016-10-30
First I would confirm if the fault lies with ufw. Disable it and try the ping again. If you are on a private LAN there is not much point running a firewall anyway because the main router on the LAN would have firewall on it.
```
sudo ufw disable
ping -c 4 8.8.8.8
ping -c 4 google.com
```

Depending on the results, you will know what to check further.

Also I see you are using dhcp for your server. It will work, but servers usually tend to have static IPs to make sure it will always have the same IP.

---

### Post by dbreez3 on 2016-10-30
Sorry, I knew I would forget some info to include...

> [COLOR=#000000]First I would confirm if the fault lies with ufw. Disable it and try the ping again.[/COLOR]

Same thing happens with UFW disabled, just thought it might be helpful to include the fact that I was using it.

> [COLOR=#000000]If you are on a private LAN there is not much point running a firewall anyway because the main router on the LAN would have firewall on it.[/COLOR]

True, I guess I don't even need UFW running since the router only forwards the ports I set anyway. It is mostly a personal file server but it is publically accessible.

Also, I'm pretty sure that I have the router set to only hand out the same IP to it anyway but I could be wrong.

Results from what you requested:
```
ping -c 4 8.8.8.8

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.


--- 8.8.8.8 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2999ms
```

```
ping -c 4 google.com

PING google.com (63.117.215.120) 56(84) bytes of data.


--- google.com ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2999ms
```

---

### Post by darkod on 2016-10-30
How about pinging the router then? Check the IP with:
```
ifconfig
```

Depending on your LAN subnet, the router might be 192.168.1.1 or 192.168.0.1 or similar. Try pinging it to check if you can ping the router at all.

Double check cables used, that the connection is plugged in correctly, try changing the ethernet cable for another, etc...

---

### Post by dbreez3 on 2016-10-30
Pinging the router works, anything on LAN works in fact.

The server can also be pinged from another local computer with no problem.

Also SSHing or ping to its public IP address works.

Router is 192.168.1.1

I've tried different cables and ports.

Results of **ifconfig**:
```
enp2s0    Link encap:Ethernet  HWaddr 90:2b:34:60:85:89          inet addr:192.168.1.157  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::922b:34ff:fe60:8589/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:109995 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99770 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:14355010 (14.3 MB)  TX bytes:18430267 (18.4 MB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10657 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:3728725 (3.7 MB)  TX bytes:3728725 (3.7 MB)
```

---

### Post by darkod on 2016-10-30
Weird... Looks like something set up on your router might be actually interfering with traffic from the server... You could try temporarily disabling any port forwarding or DMZ or similar settings you might have configured on the router. Then check again the server connectivity to the outside... Also, if you have specific firewall rules on the router, although by default all outgoing traffic is permitted.

How is the routing table on the server?
```
route -n
```

---

### Post by dbreez3 on 2016-10-30
Found it... The issue is somehow being caused by the Static NAT setting that I had set in the router for the server. Thanks for your help!

---

