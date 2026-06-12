---
title: "Ubuntu server UFW strange behavior"
date: 2022-02-25
forum: Security
---

### Post by johndid on 2022-02-25
Hi,
I'm anything but a linux expert, so I know that what may sound strange to me could make perfectly sense to you.
Anyway.
My Ubuntu server 20.04 LTS runs a few docker containers like Plex Media server which is in a docker host network.
I can access my docker plex server from my smartphone if I connect to my home router's wifi  (a mikrotik device),
 BUT if my smartphone is connected to another switch/AP (placed in a different room of my home) plugged to a different port on my mikrotik I can't access Plex anymore.
 Even my smart tv connected to the same switch can't access the plex server.
I found out that if I disable UFW everything go back to work flawlessly, but I can't make sense of it since my ubuntu server, my tv, my smartphone and my switch/AP are in the same subnet.
There is still something I'm missing apparently.
Could you help figure this out please?

Thanks

---

### Post by TheFu on 2022-02-25
Did you setup a port forward for all plex ports from the docker host?

What are the firewall rules?  Just because something is on the LAN, that doesn't provide special access to docker.  I'm not a docker person. I use a different container and place my containers on the same LAN as all other systems in that network zone. I won't be able to help with any docker specific stuff, sorry.

---

### Post by johndid on 2022-02-26
> **TheFu said:**
> Did you setup a port forward for all plex ports from the docker host?

What are the firewall rules?  Just because something is on the LAN, that doesn't provide special access to docker.  I'm not a docker person. I use a different container and place my containers on the same LAN as all other systems in that network zone. I won't be able to help with any docker specific stuff, sorry.

You can set different types of networks for containers, i.g. host, bridge, and macvlan basically. I used the host one for my Plex Media server which "removes network isolation between the container and the Docker host, and use the host&#8217;s networking directly". No problem for my containers running in a bridge network. That's the reason why I thought that it might be some issues with linux firewall. Anyway, I think you're right, I must probably work harder on port forward for all plex ports.
I thought that these two rules would be enough to grant my two devices complete access to my Plex server on linux:

Anywhere                   ALLOW       192.168.3.100
Anywhere                   ALLOW       192.168.3.18



Out of curiosity, as for your linux containers, did any of your LXCs get its own IP address in the same LAN subnet from your dhcp server?

Thanks

---

### Post by TheFu on 2022-02-26
> **johndid said:**
>  
Out of curiosity, as for your linux containers, did any of your LXCs get its own IP address in the same LAN subnet from your dhcp server?

My networking spans multiple subnets and I only use DHCP for guests, never for real servers, so my situation is nothing like yours.  I treat my lxd containers just like any other system on the same subnet. Containers don't support iptables without breaking container security, so I don't have any firewall rules configured inside the containers.  I have a LAN router that manages access between different systems on different subnets.  Subnets are physically separated using different physical ethernet connections.  I don't trust vlans for security.

---

### Post by johndid on 2022-02-26
> **TheFu said:**
> My networking spans multiple subnets and I only use DHCP for guests, never for real servers, so my situation is nothing like yours.  I treat my lxd containers just like any other system on the same subnet. Containers don't support iptables without breaking container security, so I don't have any firewall rules configured inside the containers.  I have a LAN router that manages access between different systems on different subnets.  Subnets are physically separated using different physical ethernet connections.  I don't trust vlans for security.

ok, so LXDs get their own IP like any other physical devices in your LAN. Got it right?
I guess that it is how LXDs work by default.
It is what I wanted to know. 

 Docker containers need macvlan driver for that. 

Thanks

---

### Post by TheFu on 2022-02-26
> **johndid said:**
> ok, so LXDs get their own IP like any other physical devices in your LAN. Got it right?
I guess that it is how LXDs work by default.
It is what I wanted to know. 

 Docker containers need macvlan driver for that. 

Thanks

I modified lots of defaults in LXD. I told it to use a specific bridge and it did. I don't know what the default network setup does. I also set a static IP for the container. I seldom use DHCP and consider it an abomination.

---

### Post by DuckHook on 2022-02-26
> **johndid said:**
> ok, so LXDs get their own IP like any other physical devices in your LAN. Got it right?
I guess that it is how LXDs work by default.
It is what I wanted to know. 
LXD sets up a local bridged connection by default. To change it to a physical connection, it must be custom configured as physical.
> Docker containers need macvlan driver for that.
LXD container networking can be configured in a number of different ways, including macvlan, which is another custom configuration. The use case dictates the network methodology.

TheFu has stated that he doesn't use vlans, but this does not imply that he uses physical network as an alternative. He may simply use only bridged connections and restrict his LXD usage to apps that do not need to advertise their services externally.

I use LXD for a number of use cases and here's how mine is set up:

[LIST=1]
[*]I added a second physical NIC to my server
[*]Assigned the second NIC to my LXD instance as a physical connection
[*]This takes the second NIC out of play at the kernel level and binds it to the LXD container
[*]By isolating the second NIC in this way, it does not see the host and gets its IP from the LAN's DHCP server
[*]For added security, this LAN is a separate LAN from my important one. It is on its own LAN which I treat as a quasi DMZ
[*]Unlike TheFu, I do use vlans, but the vlan is terminated at the switch. What gets passed through to the physical NIC are untagged packets.
[*]Like Docker, it is possible to pass tagged packets through to an LXD instance that has been set up with macvlan, but this breaks LAN security.
[/LIST]
In your case, the diagnoses/proposed solution would be as follows:

[LIST=1]
[*]If disabling UFW allows you to access your Plex container, then the problem is clearly in your firewall ruleset
[*]But if your firewall was set up properly, then disabling UFW would be a bad solution since it will compromise your security
[*]Therefore, consider doing what I've done and purchase a second NIC to bind to your Docker Plex instance
[*]That way, you will have a properly contained Plex server directly accessible to clients on the LAN without compromising your host firewall
[/LIST]

---

### Post by johndid on 2022-02-27
ok, thank you for the explanation

---

