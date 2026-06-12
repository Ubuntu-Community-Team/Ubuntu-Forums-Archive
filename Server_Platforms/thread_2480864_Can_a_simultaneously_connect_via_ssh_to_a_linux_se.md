---
title: "Can a simultaneously connect via ssh to a linux server running two network adapters e"
date: 2022-11-12
forum: Server Platforms
---

### Post by kevdog on 2022-11-12
I'm not new to linux but I'm not well versed in networking.

I have one linux VM which uses systemd-networkd to assign interface names and static IP addresses.

Attached to the VM are two separate virtualized Networking Cards - which represent to different VLANS. One networking card is within 10.0.40.0/255 (VLAN 40) and the other within 10.0.1.0/255 (untagged VLAN 1). 

I can initially assign each networking card a static address via systemd network files:

Network card 

```

[Match]
MACAddress=02:c0:1f:2b:12:8d

[Network]
Address=10.0.40.115/24
DNS=10.0.40.1

[Route]
Destination=0.0.0.0/0
Metric=1025

```

Network card eth1

```

[Match]
MACAddress=ee:95:e5:28:21:4c

[Network]
Address=10.0.1.117/24
DNS=10.0.1.1

[Route]
Destination=0.0.0.0/0
Gateway=10.0.1.1
Metric=1024

```

The routing table is as follows:
 ```

ip route show
default via 10.0.1.1 dev eth1 proto static metric 1024
default dev eth0 proto static scope link metric 1025
10.0.1.0/24 dev eth1 proto kernel scope link src 10.0.1.117
10.0.40.0/24 dev eth0 proto kernel scope link src 10.0.40.115

```

Initially when rebooting I can access the computer via ssh at 10.0.40.115 and 10.0.1.117, however after about 30 seconds the 10.0.40.115 connection I receive [B]client_loop: send disconnect: Broken pipe
[/B]
I'm likely doing something I shouldn't be doing however I'm just wondering if this setup is even possible. I'm assuming packets get sent from the ssh host back to the client get lost since they don't know what interface to pass back out of.

Thanks for any insight on the issue

---

### Post by &amp;KyT$0P# on 2022-11-12
Not sure whether this could help your case or not, but in case it does: I use systemd-networkd on a (non-Ubuntu) VM with 3 network adapters, and I had to put this for the non-Internet-facing interface to get networking working -
```
[Route]
Scope=link
```

---

### Post by darkod on 2022-11-13
The issue you have does not correspond to the title of your thread.

To answer the title: yes you can, if ssh is listening on both (all) adapters.

The issue you have is probably related to how you are reaching the secondary IP from your source PC. The secondary IP will be able to communicate to all devices within the same 10.0.40.0/24 subnet (the same VLAN). But if you try to reach it from a device outside of that subnet, then correct routing and maybe even NAT has to be in place so that the traffic knows how to reach your destination and how to come back to the source.

---

### Post by kevdog on 2022-11-13
@Darkod

So what you're saying makes sense since the connection on the other VLAN is usually the interface that looses the connection. 

In terms of ssh listening on all interfaces -- yes it does:

```

# ss -l | grep ssh
tcp   LISTEN 0      128                                             0.0.0.0:ssh                        0.0.0.0:*
tcp   LISTEN 0      128                                                [::]:ssh                           [::]:*

```

In terms of routing, could be an issue however I'm obviously creating some race condition, because for like the first 30-45 seconds establishing a connection to the 1 and 40 networks, both connections are up and active, Only after about 40-45 seconds does the cross VLAN traffic drop --- I don't know what I should be looking for to debug this error.

---

### Post by darkod on 2022-11-13
Giving you exact commands/advice is impossible not knowing your exact network and routing setup.

Think in terms of how traffic is travelling from source to destination and back to source. It is common a connection to "work in first seconds" but then to stop related to wrong networking setup.

For example, if you try continuous ping from the same source to destination, does it work? Can ping work for 5mins for example without lost packets? If it doesn't, that confirms you all packets are not reaching your source back.

So you have to start reviewing each hop the traffic makes. Like, which device does the routing between subnets 10.0.40.0/24 and 10.0.1.0/24?

---

### Post by mIk3_08 on 2022-11-15
> **kevdog said:**
> [B]send disconnect: Broken pipe
[/B]
I've experienced this broken pipes too in server connections. Its kinda  slow internet connections from me to server I think. What I did is once  I'm connected to the server I surely that all the jobs that I have to be  done is already prepared so that, when I'm connected to the server, Its  the time to work simultaneously because once you will be stop working there I encounter broken pipe and  I'm pretty sure you'll be back to log-in stage again because its  automatic that when losing the connection to the server, you'll be back  to log-in you're credentials again. I think this is for security  purposes. The re-alignment of connection should be secured to prevent  bad people from sneaking your connections. Regards and cheers.

---

