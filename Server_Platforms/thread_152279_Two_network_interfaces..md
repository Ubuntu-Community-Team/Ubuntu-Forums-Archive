---
title: "Two network interfaces."
date: 2006-03-29
forum: Server Platforms
---

### Post by arkopII on 2006-03-29
Hello,

I have two network interfaces, both are connected to different networks so in /etc/networking/interfaces I specified a static ip, netmask and gateway for every one. I have eth0 and eth1. 
If I ifup them separately both work perfectly, but if I try to ifup both eth0 stops to reply to ping and any service.

Suppossing I start with both of them down:

ifup eth0     ---> eth0 replies to ping perfectly.
ifup eth1     ---> eth1 works fine but eth0 stops to reply.
ifdown eth1 ---> eth0 starts to reply to ping again.
ifdown eth0
ifup eth1     ---> eth1 replies to ping.
ifup eth0     ---> eth1 goes on replying fine but eth0 says nothing.
ifup eth0     ---> Says that eth0 is already up

I confirmed with ifconfig that after every step the interfaces were up or down correctly.

Can anyone helpme?

Thank you very much.

---

### Post by diebels on 2006-03-29
Output of:
ifup eth0; ifup eth1; ifconfig; route; cat /etc/networking/interfaces

---

### Post by arkopII on 2006-03-31
[QUOTE=diebels]Output of:
ifup eth0; ifup eth1; ifconfig; route; cat /etc/networking/interfaces[/QUOTE]

Hi, thanks for replying.
This is the output, where aa.bb.ccc.ddd is an external ip. I'm not sure if I should publish the ip here, that's why I modified it.

```

root@localhost:~# ifup eth0
ifup: interface eth0 already configured
root@localhost:~# ifup eth1
root@localhost:~ # ifconfig
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:aa.bb.ccc.ddd  Bcast:aa.255.255.255  Mask:255.255.240.0
          inet6 addr: xxx::202:xx:xx:xx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40689 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3759785 (3.5 MiB)  TX bytes:40379329 (38.5 MiB)
          Interrupt:18 Base address:0xb800 

eth1      Link encap:Ethernet  HWaddr 00:13:8F:1F:56:D8  
          inet addr:10.134.192.60  Bcast:10.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fe1f:56d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:358791 (350.3 KiB)  TX bytes:191700 (187.2 KiB)
          Interrupt:23 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:909457 (888.1 KiB)  TX bytes:909457 (888.1 KiB)
root@seguirilla:~ # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.134.192.0    *               255.255.255.0   U     0      0        0 eth1
aa.bb.224.0     *               255.255.240.0   U     0      0        0 eth0
default         10.134.192.254  0.0.0.0         UG    0      0        0 eth1
default         aa-bb-ccc-eee.i 0.0.0.0         UG    0      0        0 eth0
root@seguirilla:~ # cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface eth1 inet static
address 10.134.192.60
netmask 255.255.255.0
gateway 10.134.192.254

iface eth0 inet static
address aa.bb.ccc.ddd
netmask 255.255.240.0
gateway aa.bb.ccc.eee

auto eth0

```

In this state ping to 10.134.192.60 works fine but not ping to aa.bb.ccc.ddd.
If now I do ifdown eth1, aa.bb.ccc.ddd starts to reply to ping correctly.

This is the output of ifdown followed by ifup for both interfaces:

```

root@localhost:~# ifdown eth0
root@localhost:~# ifdown eth1
root@localhost:~# ifup eth0
root@localhost:~# ifup eth1

```

Any idea?

Thank you very much.

---

### Post by diebels on 2006-04-01
[QUOTE=arkopII]
```

root@seguirilla:~ # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.134.192.0    *               255.255.255.0   U     0      0        0 eth1
aa.bb.224.0     *               255.255.240.0   U     0      0        0 eth0
default         10.134.192.254  0.0.0.0         UG    0      0        0 eth1
default         aa-bb-ccc-eee.i 0.0.0.0         UG    0      0        0 eth0
root@seguirilla:~ # cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface eth1 inet static
address 10.134.192.60
netmask 255.255.255.0
gateway 10.134.192.254

iface eth0 inet static
address aa.bb.ccc.ddd
netmask 255.255.240.0
gateway aa.bb.ccc.eee

auto eth0

```
[/QUOTE]
Not sure about this but the routing looks a bit special.
Looks like you want the private network to not be connected to the internet. That's something I've never tried, so doing a bit of guessing here.

Anyway. You run 'ping 10.134.192.60' from a machine on your private 10.134.192.0 network and 'ping aa.bb.ccc.ddd' from the internet simultaniously, and only one replies? That's strange. If pinging from local machine, maybe you need to run 'ping -I'?

If your intention is to get it connected, here's an example of my routing, where I have a two interfaces gateway that routes a lan to the internet.

```

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
aaa.b.ccc.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         aaa.b.ccc.62    0.0.0.0         UG    0      0        0 eth1

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth1 inet static
address aaa.b.ccc.29 # my internet interface
netmask 255.255.255.0
gateway aaa.b.ccc.62 # my sdsl modem

auto eth1

iface eth0 inet static
address 192.168.0.1 # my lan interface
netmask 255.255.255.0
gateway aaa.b.ccc.29 # my internet interface

auto eth0

```

---

### Post by gruepig on 2006-04-02
Is your goal to route traffic from the private subnet (on eth1) out to the public one (on eth0)?  If so ....

Bring down the interfaces.  Then edit /etc/network/interfaces:
Remove the gateway line from the eth1 stanza.  (You should only have one gateway.)
Add the lines
up iptables -A -t nat POSTROUTING -o eth1 -j MASQUERADE
pre-down iptables -D -t nat POSTROUTING -o eth1 -j MASQUERADE
(Private IPs get masqueraded.)

Then edit /etc/network/options:
Set ip_forward to yes. (Enable forwarding between the two interfaces.)

Restart networking wtih 'sudo /etc/init.d/networking restart'. 

(This is from memory so it may not be exactly correct.)

Also, are you sure your netmask is correct for eth0?  255.255.240.0 seems a bit large.

---

### Post by arkopII on 2006-04-02
Hello again,

My aim is not to route from private to public subnet, I only want to use them to provide different services, samba for private subnet and apache for public subnet. But the problem is that when I ifup eth1, eth0 stops replying to any request, ping or whatever.

However ifconfig shows them up everytime, althougth eth0 doesn't reply.

Any idea?

Thank you.

---

### Post by gruepig on 2006-04-02
Then just remove the gateway line for the private subnet.

---

### Post by rapha on 2006-04-03
Hi all!

Joining in the discussion here since we're experiencing the _exact_ same problem. However, just removing one of the interfaces' gateway line as gruepig suggested does not help us by any means :-(

Would be really grateful if somebody had a solution for this! (My guess is something with the routing table is wrong).

Here's our configuration (I've no idea as to why the second interface is called eth2 instead of eth1, but we've another server where it is eth1, same problem)...

/etc/network/interfaces:
```
iface eth2 inet static
address aa.bb.cc.dd
netmask 255.255.255.0
gateway aa.bb.cc.254

auto eth2

iface eth0 inet static
address 172.27.222.122
netmask 255.255.0.0

auto eth0

```

route output:
```
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
212.184.80.0    *               255.255.255.0   U     0      0        0 eth2
172.27.0.0      *               255.255.0.0     U     0      0        0 eth0
default         212.184.80.254  0.0.0.0         UG    0      0        0 eth2

```

The desired behaviour is just as arkopII's: respond to requests on both IPs, in our case we've different virtual hosts in Apache.

Best regards from Germany,
Raphael

---

### Post by arkopII on 2006-04-03
Removing gateway line didn't work for me either, and I can't see what's wrong in route table. Do you see something strange?

Thank you.

---

### Post by gruepig on 2006-04-04
Alright, removing the gateway won't work if you aren't forwarding packets between the two interfaces (and want hosts on non-local subnets to connect).

Run '/etc/init.d/networking' to restart networking and bring both interfaces up.

From your linux box, try to ping a host on the same subnet as eth0; on the same subnet as eth2; on a third non-local subnet.
From a test machine on the same subnet as eth0, try to ping/traceroute to the IP assigned to eth0.
From a test machine on the same subnet as eth0, try to ping/traceroute to the IP assigned to eth2.
From a test machine on the same subnet as eth2, try to ping/traceroute to the IP assigned to eth2.
From a test machine on the same subnet as eth2, try to ping/traceroute to the IP assigned to eth0.
If possible try to ping the IPs of both interfaces from a third machine not on    either local subnet.
In all cases, if ping fails use traceroute to determine where the ping is failing.

Include a summary of the results as well as the output of 'ifconfig -a' and 'sudo iptables -L'.

---

### Post by rapha on 2006-04-04
Okay, for us this has been resolved now.

Apparently, our sysadmins forgot to allow HTTP (and ICMP) to the box's external IP address in the firewall. Since it's Linux, they blamed me. That's fixed now and I can access both internal and external IP from within our network and of course the external IP from anywhere in the web.

Do make sure though, that if you have a firewall between the internet and your server like we do, to enable masquerading there. Otherwise, requests from an internal computer to the server's external IP address won't be replied through the router but directly through the local network to the internal IP address of the requesting computer, which will have no clue what to do with these packets.

Best regards,
Raphael

---

