---
title: "iptables-persistent"
date: 2013-12-30
forum: Server Platforms
---

### Post by ACagliano on 2013-12-30
I have just installed the iptables-persistent package, to make it a little easier to preserve iptables rules across reboots.
However, my system also uses PortSentry and the firewall rules may change if a host attacks my server. Id like these changes preserved.

I've seen that there is a config file for iptables-persistent that allows this, but I've looked everywhere that I've read it should be and it doesn't exist on my machine. I'm running Ubuntu Server 13.

I am open to modifying the iptables-persistent script itself if i need to, and creating the config file also if i must. the main perk i', having in doing that, however, is that iptables persistent creates a save for IPv4 and a save for IPv6, and must reload them the same way. How do I, work with that?

---

### Post by ACagliano on 2013-12-31
sorry to double post, but I found a solution: create a cron job with the following command:

/etc/init.d/iptables-persistent save
##depends on iptables-persistent installed. WebRep


currentVote


noRating
noWeight

---

