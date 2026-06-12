---
title: "Multiple NIC Issues"
date: 2009-01-29
forum: Server Platforms
---

### Post by DGortze380 on 2009-01-29
Hey All,

I've got a Virtual Machine running Ubuntu Server 8.04 LTS. It's set up with 2 NICs via host-interface networking.

Side note to anyone good with networking but not virtual machines, as far as the networking issues are concerned it's exactly the same as if I have a separate machine attached to my local subnet with 2 NICs.


So here's my problem. I have one NIC which I want to act access the gateway (eth0). It obtains a DHCP lease and is able to correctly access the internet through the gateway with an ip 10.x.x.x. No issues.

The second NIC has a static IP, different from eth0, 172.16.0.2. It's connected directly to the host which has an ip on eth1 of 172.16.0.1. I am able to access services on the virtual server from the host through this interface. It works correctly, pings correctly, etc.

The Problem:

They won't work at the same time.
If I enable eth0 and not eth1, I can get online correctly.
If I enable eth0 and eth1, I can access the host, but not get online.
If I enable eth1 and not eth0, I can access the host correctly.

I want both interfaces active at the same time. Any traffic going to 172.16.0.1 should utilize eth1, while all other traffic should utilize eth0.

I think I may need a static route??
I tried adding a static route to 172.16.0.1 through 172.16.0.2 (route add -host 172.16.0.1 gw 172.16.0.2) but it didn't help. I think I need a static route for all traffic (except traffic to 172.16.0.1) through eth0 but I don't know how to add that route.

---

### Post by DGortze380 on 2009-02-01
bump ... anyone?

---

### Post by koenn on 2009-02-01
post the output of the following commands, and we'll have a look
```

route
ifconfig
cat /etc/network/interfaces

```

it's probably a routing problem, possibly a default gateway  issue

---

### Post by DGortze380 on 2009-02-01
Condensed Version ;)

```

172.16.0.0     *     255.255.255.252     U 0 0 0 eth1
10.70.22.0     *     255.255.255.0       U 0 0 0 eth0
default      10.20.22.1     0.0.0.0      UG 100 0 0 eth0 
default      172.16.0.0     0.0.0.0      UG 100 0 0 eth1

```

```

eth0 
inet: 10.70.22.127 bcast: 10.70.22.255 mask: 255.255.255.0

eth1
inet: 172.16.0.2 bcast: 172.16.0.3 mask: 255.255.255.252

```

```

# Primary Interface
# Provides Internet Access
# Attached to en1 on Host (Airport)
auto eth0
iface eth0 inet dhcp

# Secondary Interface
# Attached to 172.16.0.1/30 on en0 on host
auto eth1
iface eth1 inet static
addres 172.16.0.2
netmask 255.255.255.252
network 172.16.0.0
broadcast 172.16.0.3
gateway 172.16.0.1

```

---

### Post by koenn on 2009-02-02
when both eth0 and eth1 are up, you have 2 default routes. That probably wont work. 
default routes come from the gateway keyword in network/interfaces. eth0 gets it from dhcp and probably needs it for internet access cause that would be 'any address'.
If you remove gateway 172.16.0.1 from interfaces (eth1) and restart networking, you're probably set. If you need to go through eth1 to reach other networks, you'll have to add these routes by hand/script.

if your output of network/interfaces is a verbatim copy, there's an arror in br**ao**dcast 172.16.0.3 (although ifconfig shows the broadcast address is set they way you want it)

---

### Post by DGortze380 on 2009-02-02
> **koenn said:**
> when both eth0 and eth1 are up, you have 2 default routes. That probably wont work. 
default routes come from the gateway keyword in network/interfaces. eth0 gets it from dhcp and probably needs it for internet access cause that would be 'any address'.
If you remove gateway 172.16.0.1 from interfaces (eth1) and restart networking, you're probably set. If you need to go through eth1 to reach other networks, you'll have to add these routes by hand/script.

if your output of network/interfaces is a verbatim copy, there's an arror in br**ao**dcast 172.16.0.3 (although ifconfig shows the broadcast address is set they way you want it)

Thanks for the tip, I'll try it as soon as I can.
That was my typo, can't copy in paste from the virtual machine.

---

### Post by koenn on 2009-02-02
> **DGortze380 said:**
> That was my typo, can't copy in paste from the virtual machine.
if you install openssh-server on that virtual machine, you can ssh to it from a terminal window on your desktop, and  copy/paste back an forth all you want.

---

### Post by DGortze380 on 2009-02-02
> **koenn said:**
> if you install openssh-server on that virtual machine, you can ssh to it from a terminal window on your desktop, and  copy/paste back an forth all you want.

lmao... it's installed, been doing that all winter, I don't know why it didn't occur to me to do that now. ](*,)

---

### Post by DGortze380 on 2009-02-02
Ok, I think I'm actually all set.

I think I have an authentication issue on the network providing internet access. 

I can access both networks so I think removing the gateway line in interfaces correct the configuration issue on the server.

---

### Post by koenn on 2009-02-02
sounds good.

---

