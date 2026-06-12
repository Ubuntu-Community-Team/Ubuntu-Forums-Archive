---
title: "Getting Ubuntu to forward ports behind a router"
date: 2013-11-28
forum: Server Platforms
---

### Post by brentdur on 2013-11-28
My network configuration is as follows:

Modem -> Router -> Ubuntu -> Computer
69.X    -> 192.168.1.1 -> 192.168.1.2/192.168.2.2 -> 192.168.2.10

The computer is only connected to the router through ubuntu and can access the internet.  I am trying to forward a port from the router through ubuntu to the computer.  From the router I have the ports forwarded to 192.168.1.2 one of ubuntu's NIC's.  I then have the nat tables set in ubuntu to: 
```
sudo iptables -t nat -A PREROUTING -j DNAT --to-destination 192.168.2.10 -p udp -m multiport --ports <Port to Forward> -m comment --comment <what's being forwarded>
```

Despite this, the ports do not seem to act as forwarded.  Does anyone have any suggestions?

(packet forwarding is enabled)

---

### Post by Doug S on 2013-11-28
Hi and Welcome to Ubuntu forums,

You need return path that does NAT. You need:```
sudo iptables -t nat -A POSTROUTING -o $EXTIF -j SNAT --to 192.168.1.2
```Substitute your actual upwards facing interface name (the one that goes to your Router) for $EXTIF. Note also, that a lot of people use MASQUERADE instead of SNAT, but I prefer SNAT. I also think the you should specify an input interface on your PREROUTING rule.

---

### Post by brentdur on 2013-11-28
When trying to specify an input on the prerouting chain it gave me a message saying that the "-o" option was not available.  I added in your exception to the postrouting chain but it did not fix the problem.  I also would like to point out that I have the source 192.168.2.0/24 MASQUERADE to any destination in the postrouting already.  Any further hints?

---

### Post by Doug S on 2013-11-28
> **brentdur said:**
> When trying to specify an input on the prerouting chain it gave me a message saying that the "-o" option was not available. yes, "-o" doesn't work, it has to be "-i".
> I also would like to point out that I have the source 192.168.2.0/24  MASQUERADE to any destination in the postrouting already.  Any further  hints?Please post your rule, and any other rules you have.

---

### Post by brentdur on 2013-11-29
I have several rules like this for port forwarding
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo iptables -t nat -A PREROUTING -j DNAT --to-destination 192.168.2.10 -p udp -m multiport --ports <Port to Forward> -m comment --comment <what's being forwarded>[/FONT][/COLOR]
```

I then have added this rule before those:
```
sudo iptables -t nat -I PREROUTING 1 -i eth1 -j DNAT --to-destination 192.168.2.10
```
This was in an attempt to redirect all traffic to this computer.  I have been using a web based port checker to test them

Under the Postrouting chain I have the following two rules
```
sudo iptables -t nat -A POSTROUTING -o eth1 -j SNAT --to 192.168.1.2 
```
```
sudo iptables -t nat -A POSTROUTING -j MASQUERADE -s 192.168.2.0/24
```

On my router I have several ports forwarded to 192.168.1.2 (the outside facing nic of the server(eth1))
The entire server is also running on a Virtual Machine, but this shouldn't pose a problem.

---

### Post by Doug S on 2013-11-29
For POSTROUTING just use one or the other of the commands, not both. I suggest the SNAT one.
If you want to forward everything, then don't bother with the individual port.
For the individual port I would suggest similar to this:```
sudo iptables -t nat -A PREROUTING -p tcp -i $EXTIF --dport 80 -j DNAT --to 192.168.2.10:80
```

---

### Post by brentdur on 2013-11-29
Ok, I flushed the entire nat table and rewrote it, throwing in a few ports and using the SNAT for Post.  It seems to be working as long as there is an application on my computer ready to receive it.

I have one more question though.  My router supports UPnP for automatic port mapping and many applications support it.  Is there a way to forward the UPnP port mapping requests that the computer makes through the ubuntu server so that the router will auto map ports?  Is there a way to implement that into the ubuntu server too so I don't have to go in it everytime I need to map a port?

---

