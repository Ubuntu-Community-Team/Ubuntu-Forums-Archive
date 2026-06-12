---
title: "Apache 2 Forward Proxy"
date: 2008-06-12
forum: Server Platforms
---

### Post by ccb00mer on 2008-06-12
Does anyone know how to configure Apache 2 to forward all incoming packets from a fixed IP on one NIC and forward them to a fixed IP out of another NIC.  

This would operate on a machine with two different NIC cards, each with different IP addresses on the same subnet, and should forward all packets, if possible, regardless of type.

All incoming packets would arrive from a fixed IP and would be addressed to only one of the two NICs.

All outgoing packets should go out of the second NIC, and should all be addressed to a second, static IP.

No security would be required, as this would operate on a closed system with no type of external access.

---

### Post by SpaceTeddy on 2008-06-13
what you want to do does not sound like you want an apache proxy, but rather port forwarding. the *simplest* way i can think of is tunrning ip forwarding on, and then loading a dnat rule in iptables - that should fix your problem.

here are the appropriate commands:
```
sudo sysctl -w net.ipv4.ip_forward=1
sudo iptables -A PREROUTING -p tcp --dport 80 -i **eth_in** -o **eth_out** -j DNAT --to-destination **target_ip**
```

Another idea is that you might want to use squid as a proxy.
If you are really bound and *must* use apache, then i'd suggest mod_proxy - but that is serious overkill on the machine !

hope it helps :)

---

### Post by ccb00mer on 2008-06-13
Can you set the port forwarding to work with any port?

---

### Post by SpaceTeddy on 2008-06-14
yes - the -p flag specifies the protocoll to look for, the --dport is the port that the paket is send to. If you change those, you can pretty much forward anything. 

If you leave the --dport out, you will forward a full protocoll, if you leave the protocoll out, you will forward ANYTHING. I must warn you about that one - you can lock yourself out of your system and only restore it by going to the machine itself if you do something like a general forward. 
I'd advise against it.

hope it helps :)

---

