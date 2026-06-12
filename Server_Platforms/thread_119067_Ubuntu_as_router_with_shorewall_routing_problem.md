---
title: "Ubuntu as router with shorewall routing problem"
date: 2006-01-18
forum: Server Platforms
---

### Post by mtlife on 2006-01-18
I have setup as a router ubuntu now, with shorewall and bind9 works like a charm. Except one little thing.. I cant seem to go to access my outside ip from the local network. In my case I cant access [http://145.99.157.xx](http://145.99.157.xx) but I can access the local ip ([http://192.168.1.xx)](http://192.168.1.xx)). Is there anyone that knows how to setup shorewall in a way I can access the outside ip? 

I found a tutorial on shorewall.net that involves bind9 and alot of config. But that doesnt seem to make sense to me. 

If anyone could help out, i'd really appreciate it.

---

### Post by MJN on 2006-01-18
I've not personally had any experience with Shorewall, however the Shorewall FAQ makes up for this... ;)

Check out [http://www.shorewall.net/FAQ.htm#faq2]("http://www.shorewall.net/FAQ.htm#faq2") - '*(FAQ 2) I port forward www requests to [www.mydomain.com](www.mydomain.com) (IP 130.151.100.69) to system 192.168.1.5 in my local network. External clients can browse [http://www.mydomain.com](http://www.mydomain.com) but internal clients can't.*'

Ignore any mention of BIND views etc - you're not concerned with names, merely IP addresses yet the principles are the same.

Mathew

---

### Post by mtlife on 2006-01-19
tried that now, doesnt really work for me.. I have no idea why, but my guess is that that works for shorewall 3.x while ubuntu has shorewall 2.x..
And i'm not thinking of upgrading to 3.x yet :) this version just works, but i'd like to see the routeback work too.

---

### Post by mtlife on 2006-01-20
*bump* there is someone who knows this, c'mon

edit: ok after a bit of trying i found this out:
add this rule to your /etc/shorewall/masq:
whereas eth1 is your local network
eth1              eth1           192.168.1.1 #this is your firewall ip

and that is all, the faq on shorewall relates to 3.x

edit2: this doesnt solve the problem completely, i can still not access the outside ip on the ubuntu box :(
maybe someone can help with that?

---

### Post by Rick Z on 2007-12-03
I am trying to setup shorewall as router/gateway as well, but I wasn't able to.  I had the same problem as mtlife.  I am able to login to the router from my internal network.  once the other pc login to the router, I am not able to access internet.

anyone figure this out?  Please help...Thanks.

---

### Post by gubemton on 2007-12-03
> **Rick Z said:**
> I am trying to setup shorewall as router/gateway as well, but I wasn't able to.  I had the same problem as mtlife.  I am able to login to the router from my internal network.  once the other pc login to the router, I am not able to access internet.

anyone figure this out?  Please help...Thanks.

Do you have line "IP_FORWARDING=On" in your /etc/shorewall/shorewall.conf?
Here are some of critical parts from my other configs. They are from Debian Etch but read the manual for the differences.

interfaces:```

#ZONE   INTERFACE       BROADCAST       OPTIONS
net     eth1            detect          dhcp,tcpflags,norfc1918,routefilter,nosmurfs,logmartians
loc     eth0            detect          dhcp,tcpflags,detectnets,nosmurfs

```
zones:```

#ZONE   TYPE    OPTIONS                 IN                      OUT
#                                       OPTIONS                 OPTIONS
fw      firewall
net     ipv4
loc     ipv4

```
masq:
```
#INTERFACE              SUBNET          ADDRESS         PROTO   PORT(S) IPSEC
eth1                    eth0


```policy:```

#SOURCE         DEST            POLICY          LOG LEVEL       LIMIT:BURST

#
# Note about policies and logging:
#       This file contains an explicit policy for every combination of
#       zones defined in this sample.  This is solely for the purpose of
#       providing more specific messages in the logs.  This is not
#       necessary for correct operation of the firewall, but greatly
#       assists in diagnosing problems.
#

#
# Policies for traffic originating from the local LAN (loc)
#
# If you want to force clients to access the Internet via a proxy server
# on your firewall, change the loc to net policy to REJECT info.
loc             net             ACCEPT
loc             $FW             ACCEPT
loc             all             REJECT          info

#
# Policies for traffic originating from the firewall ($FW)
#
# If you want open access to the Internet from your firewall, change the
# $FW to net policy to ACCEPT and remove the 'info' LOG LEVEL.
# This may be useful if you run a proxy server on the firewall.
$FW             net             ACCEPT
$FW             loc             REJECT          info
$FW             all             REJECT          info

#
# Policies for traffic originating from the Internet zone (net)
#
net             $FW             DROP
net             loc             DROP            info
net             all             DROP            info

# THE FOLLOWING POLICY MUST BE LAST
all             all             REJECT          info
```

/usr/share/doc/shorewall/examples/two-interfaces/ has configuration example for everything else except shorewall.conf where you probably have to enable IP forwarding.

---

### Post by Rick Z on 2007-12-06
I got it to work now...  :)  I follow up by reading all the good documentation from Shorewall Website.  I saved my current shorewall configuration by the following command.

#shorewall save

Thank you for pointing out for me.

Rick

---

