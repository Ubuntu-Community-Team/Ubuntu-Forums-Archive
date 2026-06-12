---
title: "ubuntu as router"
date: 2012-03-21
forum: Server Platforms
---

### Post by kuda on 2012-03-21
**Hello world,**

I am struggling with following setup:

[HTML]Internet -- 77.53.117.128/26 -- Linux router (77.53.117.130) -- DMZ
                                   |                         PUBLIC IPs
                                   |                    (77.53.117.132/30)
                                   |
                                   |
                                   +------ private IP range (10.10/16)[/HTML]


"router" is setup to do a NAT and works ok for private IP range but I am not able to ](*,)](*,)](*,) contact hosts on DMZ segment from Internet (and reversely)

I need to split further the range I got from ISP but I am not sure about routing and such, can anyone point me right direction?? Is it possible to achieve what I am trying to do when the "router" is in NAT mode? thank you very much in advance!


```
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 77.53.117.130
	netmask	255.255.255.128
	gateway 77.53.117.129

#auto eth1
#iface eth1 inet static
#	address 10.11.0.1
#	netmask 255.255.0.0
#	gateway 10.10.0.1

auto eth1.11
iface eth1.11 inet static
  address 10.11.0.1
  netmask 255.255.0.0
  vlan_raw_device eth1

auto eth1.78
iface eth1.78 inet static
  address 77.53.117.133
  netmask 255.255.255.252
  vlan_raw_device eth1
#  gateway 77.53.117.133

```

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
77.53.117.132   0.0.0.0         255.255.255.252 U     0      0        0 eth1.78
77.53.117.128   0.0.0.0         255.255.255.128 U     0      0        0 eth0
10.11.0.0       0.0.0.0         255.255.0.0     U     0      0        0 eth1.11
0.0.0.0         77.53.117.129   0.0.0.0         UG    100    0        0 eth0
```

---

### Post by darkod on 2012-03-21
How many public IPs you have from your ISP exactly? Which ones?

Have you tried the DMZ with IP .131 and gateway .129?

---

### Post by darkod on 2012-03-21
Can this help for configuring a static route from one range to the other (if you indeed have two public ranges allocated):
[http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html](http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html)

---

### Post by kuda on 2012-03-21
> *How many public IPs you have from your ISP exactly? Which ones?*

Thanks for reply, I have the whole range 77.53.117.128/26 routed to my "router", I have been thinking I will create several vlans with various subnets (under 77.53.117.128/26) and reallocate them to those who need public ips on out network ....

> *Have you tried the DMZ with IP .131 and gateway .129?*

Yes, I did, I will try to study the link you sent and we'll see ... it was 3 days ago I started to work on this and still no luck .... it seems to be so simple :-/

---

### Post by darkod on 2012-03-21
In that case I am not sure you can use it with .252 mask. Try using it with the original .128 mask.

Also, what are etc1.11 and eth1.78, like virtual network cards? Could this be your problem?

Can you try adding one more card to your router/server and configuring eth2 to be your DMZ?

---

### Post by SeijiSensei on 2012-03-21
> auto eth1.11

Unless the syntax has changed recently, you designate a virtual interface with a colon, not a dot, like this:

```
eth0:0
```

---

### Post by kuda on 2012-03-21
> In that case I am not sure you can use it with .252 mask. Try using it with the original .128 mask.

Yes, I did this as well (yesterday)

> Also, what are etc1.11 and eth1.78, like virtual network cards? Could this be your problem?

Can you try adding one more card to your router/server and configuring eth2 to be your DMZ?

eth1.11 and eth1.78 are vlans truncated with switch, I have no opportunity to add more physical interfaces but I don't think problem is here since I can ping "DMZ hosts" from "router" (and reversely) and "router" can reach internet (and reversely) .. so the problem should be in the box ("router") somewhere ... I am still not sure how is it with NAT and "public ip forwarding" because this box should stay as "NAT router" and kind of "bridge" at the same time ....

---

### Post by kuda on 2012-03-21
> **SeijiSensei said:**
> Unless the syntax has changed recently, you designate a virtual interface with a colon, not a dot, like this:

```
eth0:0
```
[http://manpages.ubuntu.com/manpages/lucid/man5/vlan-interfaces.5.html]("http://manpages.ubuntu.com/manpages/lucid/man5/vlan-interfaces.5.html")

---

### Post by darkod on 2012-03-21
I think what we are missing is to configure a bridge between your DMZ interface and the external (WAN) interface:
[http://manpages.ubuntu.com/manpages/lucid/en/man5/bridge-utils-interfaces.5.html](http://manpages.ubuntu.com/manpages/lucid/en/man5/bridge-utils-interfaces.5.html)

After the bridge is in place, you simply configure public IPs on your server and you use the same gateway as your ext interface (I think).

---

### Post by kuda on 2012-03-22
Thanks for links and advices, I'll try and come back ASAIG some working solutions ....

---

### Post by darkod on 2012-03-22
Also don't forget to use the same gateway. Your thread got me interested and I started googling the subject, in one place I saw info that you can't simply split your IPs into subnets as you like. It has something to do with the config on the ISP side and if they only gave you one block, you need to use it as one with the same gateway supplied.

Which means you can't divide it in half and use a smaller mask because the second half of the IPs wouldn't even be in the same subnet with the gateway in that case.

Lets see what you come up with.

---

### Post by kuda on 2012-03-24
> Which means you can't divide it in half and use a smaller mask because the second half of the IPs wouldn't even be in the same subnet with the gateway in that case.

^^ This is exacly what I wanted to do, I could then assign these smaller ranges to various VLANs and redistribute it further to end-users.

Nevermind, I hope I got the bridge working somehow but from hp switch which is "behind" the "router" I am still not able to contact the world and reversely. Can anyone check the setup below, please? I am not sure about the bridging between vlan and physical interface (eth0 and eth1.78 in my case) because it's bridging between tagged and untagged interface ...??

```
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual
#	address 77.53.117.130
#	netmask	255.255.255.128
#	gateway	77.53.117.129

#auto eth1.78
iface eth1.78 inet manual
	vlan_raw_device eth1


# Bridge setup
auto br0
iface br0 inet static
        address 77.53.117.131
        netmask 255.255.255.192
[COLOR="Red"][B]## it should be .192 and not .128 mask, I don't know why I used .128
## the range is 77.53.117.128/26[/B][/COLOR]
        gateway 77.53.117.129
	bridge_ports eth0 eth1.78
        bridge_stp on
	bridge_maxwait 10

auto eth1.11
iface eth1.11 inet static
  address 10.11.0.1
  netmask 255.255.0.0
  vlan_raw_device eth1

#auto eth1.78
#iface eth1.78 inet static
#  address 77.53.117.132
#  netmask 255.255.255.128
#  vlan_raw_device eth1
#  gateway 77.53.117.130

```

```
route -n
77.53.117.128   0.0.0.0         255.255.255.192 U     0      0        0 br0
10.11.0.0       0.0.0.0         255.255.0.0     U     0      0        0 eth1.11
0.0.0.0         77.53.117.129   0.0.0.0         UG    100    0        0 br0

```

from the switch's point of view:

```
                       |                                            Proxy ARP 
  VLAN                 | IP Config  IP Address      Subnet Mask     Std  Local
  -------------------- + ---------- --------------- --------------- ----------
  DEFAULT_VLAN         | Disabled 
  VLAN10               | Manual     10.10.0.2       255.255.0.0      No    No
  VLAN11               | Manual     10.11.0.2       255.255.0.0      No    No
  VLAN77               | Disabled 
  VLAN78               | Manual     77.53.117.132   255.255.255.192  No    No

                                IP Route Entries

  Destination        Gateway         VLAN Type      Sub-Type   Metric     Dist.
  ------------------ --------------- ---- --------- ---------- ---------- -----
  10.10.0.0/16       VLAN10          10   connected            1          0    
  10.11.0.0/16       VLAN11          11   connected            1          0    
  77.53.117.128/26   VLAN78          78   connected            1          0    
  127.0.0.0/8        reject               static               0          0    
  127.0.0.1/32       lo0                  connected            1          0  
```


```
ping 77.53.117.131 
77.53.117.131 is alive, time = 1 ms
```

^^ bridge

```
ping 77.53.117.129 
77.53.117.129 is alive, time = 2 ms
```

^^ gateway

but

```
ping 173.194.32.36
The destination address is unreachable.
```

^^ google.com

Thank you again for possible hints.

---

### Post by darkod on 2012-03-24
Why do you have auto eth1.78 commented out? Don't you need that to bring up the interface at boot?

Comment out all other settings for eth1.78 in /etc/network/interfaces because the bridge instructions say not to have any configuration for the interfaces in the bridge.

I don't know what else to touch.

---

### Post by collisionystm on 2012-03-25
Okay..... I have built several ubuntu routers and firewalls.

What you need to do is.....

First edit 

/etc/sysctl.conf

uncomment

net.ipv4.ip_forward=1

This will allow the routing of IP's.

2nd.

You need to enable masquerade. This is required so all of your internal IP's trying to reach the internet appear as the external interface therefore allowing the internet connection.

iptables -t nat -A POSTROUTING -o EXTERNAL.INTERFACE -j MASQUERADE


Point a client PC to your box. ( set its gateway to it ). Try to ping 8.8.8.8 ( google dns servers ). can you?

I also suggest you use UFW.

ufw default deny
ufw allow from local.subnet/mask
ufw enable



You do not need a static address from your ISP unless you need to receive inbound connections from the outside world. I.E. running a web server.

---

### Post by darkod on 2012-03-25
If I may reply in the name of the OP (and because the subject interests me).

The routing is not a problem to set up. But in this case if you need also to have a DMZ port on your router/firewall machine to which you plan to connect computers configured with a public IP also and direct access to the internet through your router.

Do you need additional steps for this or the standard steps you described cover this option too? You simply set up a public IP on the computer connected to your DMZ port and that's it?

Because the OP says the machine in the DMZ doesn't get outside access. Can't test it myself now.

---

### Post by collisionystm on 2012-03-25
> **darkod said:**
> If I may reply in the name of the OP (and because the subject interests me).

The routing is not a problem to set up. But in this case if you need also to have a DMZ port on your router/firewall machine to which you plan to connect computers configured with a public IP also and direct access to the internet through your router.

Do you need additional steps for this or the standard steps you described cover this option too? You simply set up a public IP on the computer connected to your DMZ port and that's it?

Because the OP says the machine in the DMZ doesn't get outside access. Can't test it myself now.


It really depends on the router. For instance if the OP is using an actiontec, the IP cannot reside on the server itself unless the actiontec is set for passthrough.

I just setup one of my sites with ADSL and an actiontech. Just gave the server an internal IP. Set it in the DMZ from the router. Setup ipv4 forward and boom. done. No need to masqerade in that case because the actiontec already took care of it.

I have it using OPENVPN PTP to connect to my other sites. Just setup a port forward in the router.

(made sure to enable UFW) You wouldnt believe the amount of port scans going on. Must have previously been a very active external address.

---

### Post by darkod on 2012-03-25
Doing the routing in a "simple" setup is very easy. Recently I also worked on a firewall/router project and I'm still with the subject.

But my case was very basic, one external and one internal interface. Works great.

What the OP is trying to do is one external, one internal and one DMZ interface. On top of that the internal and the DMZ share the same eth1 only with different VLANs.

What I am still not sure about is whether the standard routing settings take care of the packets from the DMZ towards the ext interface too, or you need some other additional settings. For example something like a simple bridge, etc.

Because in fact, the servers on the DMZ have public IPs anyway, so no real routing is done by the router/firewall device, just passing on the packets from the DMZ towards the ext interface.

This is what we can't make work yet. The computers on the internal work fine, so the routing is set up OK in that aspect. But the DMZ?

---

### Post by kuda on 2012-03-27
> **collisionystm said:**
> It really depends on the router. For instance if the OP is using an actiontec, the IP cannot reside on the server itself unless the actiontec is set for passthrough.


^^ OK, I am OP. What do you mean by that?? I don't use any router, I am TRYING to setup a router! Please check my first post in this thread ... anyway thank you for tips but I think you don't understand what I am trying to do (or my english is worse than bad).

I am still not finished with my issue, but I had to work on something else. It looks like I have a working bridge but I can't get behind the gateway from those dmz hosts. I thought I can have problems with tagged vs. untagged packets as I am bridging directly to VLAN. I tried direct eth0 to eth1 bridge (no VLANs) and from DMZ point of view still the same so the problem must be somewhere else. I will let you know.

---

### Post by bab1 on 2012-03-27
> **kuda said:**
> ^^ OK, I am OP. What do you mean by that?? I don't use any router, I am TRYING to setup a router! Please check my first post in this thread ... anyway thank you for tips but I think you don't understand what I am trying to do (or my english is worse than bad).

I am still not finished with my issue, but I had to work on something else. It looks like I have a working bridge but I can't get behind the gateway from those dmz hosts. I thought I can have problems with tagged vs. untagged packets as I am bridging directly to VLAN. I tried direct eth0 to eth1 bridge (no VLANs) and from DMZ point of view still the same so the problem must be somewhere else. I will let you know.

I don't really want to step to deeply into this other than to say that a true DMZ requires 2 routers.  Like this ```
Internet<--->Router1<--DMZ-->Router2<---->Private Network
```

On router1  you provide only forwarding and specific firewall rules.  Router2 provides the NAT for the private addressing.

I believe this is what @collisionystm is referring to.  The use of bridging is not really a good idea in my mind as you are connecting all the hosts at the link layer (layer 2) with no IP or port based firewall protection.

---

### Post by koenn on 2012-03-27
> **bab1 said:**
> I don't really want to step to deeply into this

me neither


> 
...  a true DMZ requires 2 routers.  Like this ```
Internet<--->Router1<--DMZ-->Router2<---->Private Network
```

not really, you can do it with one, given enough interfaces:
```

            internet
               |
               |
    DMZ --- router ----------- LAN (secure)


```
that gives you 6 sets of rules to define:
inet to lan
lan to inet
inet to dmz
dmz to inet
dmz to lan
lan to dmz

the contents of those rule sets are what makes your dmz a dmz. 
obviously, you can apply NAT/MASQ where appropriate or necessary


But I agree that a lot of people immediately jump to bridging, often without good reason. 
It's not quite clear to me what the OP is trying to accomplish, so this is just an 'in principle' remark.

---

### Post by kuda on 2012-03-30
Ok, I got it. Only routing (withou bridge) doesn't work - neither when used agains tagged interface (VLANs) nor against untagged (physical iface - eth1) .. I don't know why ...?
I still can't get out behind the gateway from the HP switch but when I connect a dmz-host machine to a port (untagged) which is member of the same VLAN on the HP switch, communication works both ways (host->internet, internet->host) 

Here is my working /etc/network/interfaces
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto eth1.78
iface eth1.78 inet manual
	vlan_raw_device eth1

# Bridge setup
auto br0
iface br0 inet static
        address 77.53.117.130
        netmask 255.255.255.192
        gateway 77.53.117.129
	bridge_ports eth0 eth1.78
        bridge_stp off
	bridge_fd 0
	bridge_maxwait 10

auto eth1.11
iface eth1.11 inet static
  address 10.11.0.1
  netmask 255.255.255.0
  vlan_raw_device eth1

```

I am bridring tagged and untagged interface but it works .....

[http://wiki.debian.org/NetworkConfiguration#Howto_use_vlan_.28dot1q.2C_802.1q.2C_trunk.29_.28Etch.2C_Lenny.29]("http://wiki.debian.org/NetworkConfiguration#Howto_use_vlan_.28dot1q.2C_802.1q.2C_trunk.29_.28Etch.2C_Lenny.29")

---

