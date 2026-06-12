---
title: "two networked internet connections, one needs access to the other"
date: 2007-07-10
forum: Server Platforms
---

### Post by blissend on 2007-07-10
Here's a challenge... at least for me 8D

I have an Ubuntu server setup with two statically assigned IP addresses on each eth card. One is the internal network with access to the internet. The other has different access point to the internet but with special privileges to a website based on that statically assigned IP.

How can I allow the internal network to access that site through the server?

---

### Post by turinglabs on 2007-07-10
Can you clarify your setup? How does your internal network get out to the internet? Via another connection entirely? Or does all LAN traffic get routed first through your server mentioned above (but that would imply it has three interfaces [ two internet and one LAN ], or there wouldn't be an issue).

---

### Post by blissend on 2007-07-10
The internal network has a DHCP server (little laptop with two eth cards). It connects to the internet via a static IP like 70.xxx.xxx.xxx and assigns all machines 10.2.0.xxx whom in return will now have access to the internet.

This is were things get complicated. On a separate setup, a router with a special connection to the internet will allow someone access to a website when the machine directly connected to the router is assigned a certian IP address like 66.xxx.xxx.xxx. How do I setup that machine to act as a gateway to this connection on a preexisting network?

---

### Post by turinglabs on 2007-07-11
It's not clear to me if the latop and router both have interfaces on the LAN, or if the laptop sits in-between the LAN and the router (or are you asking the best way to connect these together?). A diagram might help, but this will work with some tweaking:

On your laptop, you add a static route that sends traffic destined for the special website to your router (if their is no connection between the laptop and router, then each client will need the static route). The router just has to NAT the connections out to the website so they all appear to be coming from a 66.x.x.x address.

On the client or laptop:

```

route add <website IP> gw <internal IP of router>

```

On the router:

```

iptables -t nat -A POSTROUTING -o <external interface name> -s <LAN network> -j SNAT --to-source 66.x.x.x

```

Finally, depending on how this is all connected together, you may need a static network route on the router that sends traffic destined for the LAN back to the laptop. This will ensure that return traffic from the website gets back to the LAN network. This is not needed if the router has an interface on the LAN.

The best way to do this when you have two internet connections is to have a 'choke router' that sits in-between the LAN and your two internet routers, it can route traffic to the right connection depending on the destination. The two internet routers then just have to have a route for LAN traffic that points back to the choke router. The choke router just has to be a simple router, so it can be something inexpensive.

```


[NAT 66.x.x.x]                  [your laptop]
router1                             router2
   |                                           |
   |-------------choke-----------|
                      router
                           |
                         LAN

```

You can replace the choke router with a switch, but then you end up adding the static route to each LAN client (as I mentioned above).

---

### Post by blissend on 2007-07-11
Thanks turinglabs, I figured out what I needed to do. I just needed to setup my routing tables correctly using the route command. Should have known that 8(

In case anybody wants to know and to better explain things, here is what I did.

cablebox1 70.xxx.xxx.xxx (internet connection via this static IP)
cablebox2 66.xxx.xxx.xxx (another internet connection via this static IP)

localnetwork 10.2.0.xxx

ubuntuserver1 10.2.0.1 (router) - This is just a laptop with two eth cards. 
[INDENT]Card eth1 is statically assigned 70.xxx.xxx.xxx to connect to the internet on the cablebox1. The other card eth0 is statically assigned 10.2.0.1 and is plugged into a switch. All other computers connect to that switch and will be assigned an IP address from this router and then will have internet access.[/INDENT]

ubuntuserver2 10.2.0.xxx (another router) - A laptop with two eth cards again.
[INDENT]Card eth1 is statically assigned 66.xxx.xxx.xxx to connect to the internet on the cablebox2. The other card eth0 is statically assigned 10.2.0.xxx and is plugged into the switch.[/INDENT]

On ubuntuserver2, I simply looked at the route tables (netstat -r) and modified it. I used the route command to add a default route to 66.xxx.xxx.xxx. This made all connections from this server to go and use cablebox2 instead of the other.

On ubuntuserver1, I looked at the route tables again and modified it. I added a route from a IP range to go and use ubuntuserver2 internet connection instead. 

This allows me to accomplish my goal. When a certian site is accessed, they go off on a better internet connection. sweet 8)

---

