---
title: "LTSP - Two Labs - Four NICs - How To Configure?"
date: 2011-07-14
forum: Server Platforms
---

### Post by Roasted on 2011-07-14
Hey there. I'm running an LTSP thin client server running Edubuntu 10.04 64 bit on a rather large server. The server has 4 gigabit network ports. Most of our networking gear in our environment is Dell PowerConnect 6248 switches.

What's going to happen is I'm going to host this server as the thin client server for two different labs. I've previously used a server with 1 gigabit port for a lab of 30 systems, so I know it's capable (network wise) of that. Having these different NICs provides more opportunity, however in an area I'm not totally familiar with.

I'm on the fence about a few ideas, so I'd like some insight.

I'm debating on bonding the interfaces. I thought about bonding the interfaces into a total of 2 pairs, and then providing one pair to one lab and another to another lab. That way they have some sort of redundancy throughout the lab. If possible, though, I'd like to keep the IP address the same for the entire server. Wouldn't that require me to have two virtual interfaces (across four physical interfaces) to have the same IP address? 

Also, I've thought about just vlan-ing all of the traffic independently, and letting Ubuntu act as the DHCP server despite us already having a DHCP server. I've done this before and it seemed to work, by putting the server/clients onto one switch and creating a different subnet. Then the clients get an IP through the Ubuntu server and work in their own little LAN, but still access everything on the main network too as far as switches, etc.

What would the easiest route be? I guess I'm a little hesitant about bonding because I have *no* idea which would be best. I've done my fair share of reading but there's a lot of different types of bonding and dozens and dozens of guides on how to do it.

Any pin pointed help would be appreciated!

---

### Post by Roasted on 2011-07-15
up?

---

