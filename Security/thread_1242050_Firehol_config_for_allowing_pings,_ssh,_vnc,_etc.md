---
title: "Firehol config for allowing pings, ssh, vnc, etc"
date: 2009-08-16
forum: Security
---

### Post by narnie on 2009-08-16
Hello,

I have firehol (along with tinyproxy) configed for dansguardian for my sis's family. However, after firehol is activated, I can't ping, ssh, vnc, etc.computers on which I have this configuration. If I "sudo /etc/init.d/firehol stop" then I can do whatever I want, but of course this defeats the purpose and my sis is not technosavy enough to easily do this if I need to ssh or vpn to fix stuff.

What do I need to add to my firehol.conf to allow things like pings, ssh, vnc, and whatever else may come up (thinking about freenx) so that these requests are not dropped.

I hope to learn this on my own, but I'm leaving my sisters soon and need a more rapid turn-a-round than my ability to quickly learn iptables can provide.

What exactly below is preventing these requests?

For future reference, any place on the net you recommend to learn more on this topic?

```

#
# $Id: client-all.conf,v 1.2 2002/12/31 15:44:34 ktsaou Exp $
#
# This configuration file will allow all requests originating from the
# local machine to be send through all network interfaces.
#
# No requests are allowed to come from the network. The host will be
# completely stealthed! It will not respond to anything, and it will
# not be pingable, although it will be able to originate anything
# (even pings to other hosts).
#

version 5

# Accept all client traffic on any interface
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

transparent_squid 8080 "root root"

interface any world
policy drop
protection strong
client all accept
server cups accept
#server webcache accept
	client all accept


```

With thanks,
Narnie

---

### Post by narnie on 2009-08-16
I found some info pretty quickly about this actually and didn't need to learn a bunch of iptables rulz. It is actually quite easy.

under the "interface any world" there is a "server cups allow"

This is the area that controls access to servers and can be based on a particular interface like eth0, or in this case, any interface local and internet.

I just needed to change the cups to all, which allows all servers.

You can be more selective and just add what you need like ping, ssh, etc

the line can look like:
```

server "dns ftp samba icmp ping ssh" accept

```

Just do this and you will be able to access needed services on the machine.

Cheerio,
Narnie

---

