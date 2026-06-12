---
title: "Web Proxy server and DHCP Server on ubuntu 12.04"
date: 2013-06-18
forum: Server Platforms
---

### Post by neil1188 on 2013-06-18
Hi Guys,

I would like to seek for your help regarding to my project. My boss ask me to upgrade our network to put somethin that can us. Then he tells me that I need to create a DHCP,Web proxy,cache server and also a firewall using the ubuntu.

I know that the proxy and cache server is for squid3.

Now how can i setup everything on our network?

ISP -> Modem -> router1 -> servers? -> switch -> lans

is it correct? im only new on this field so im totally no idea, Ive already read some ebooks but im still having problem on implementing and setting up everything.

I hope you can give me some idea or Help me to finish this project.

---

### Post by Irihapeti on 2013-06-18
*Thread moved to **Server Platforms**.*

---

### Post by romeroc24 on 2013-06-18
Hello, I think you can do this.

ISP -> Modem -> router1 -> Server (Proxy, DHCP, DNS) -> Switch -> LAN

Put the server between router and switch, the server can contain 3 servers:

-DNS (bind9).
-DHCP (dhcp3).
-Proxy (squid3).

Try it!

---

### Post by Lars Noodén on 2013-06-18
Bind is probably not necessary unless special tricks with DNS are needed.  

ISC dhcpd is easy enough to set up, but dnsmasq is even easier.  dnsmasq can also do DNS caching if that was on the list, too.

Squid3 is easy enough to set up, if you are able to point your web clients to it.  If you are trying to set up transparent proxying, it is now called intercept mode and most of the documentation online is now out of date since it  refers to the old way of doing it.

About the firewall, you'll probably have to look at iptables directly.  Graphical tools like GUFW are mostly set up to affect an individual host, not a network.

---

### Post by neil1188 on 2013-06-19
> **Lars Noodén said:**
> Bind is probably not necessary unless special tricks with DNS are needed.  

ISC dhcpd is easy enough to set up, but dnsmasq is even easier.  dnsmasq can also do DNS caching if that was on the list, too.

Squid3 is easy enough to set up, if you are able to point your web clients to it.  If you are trying to set up transparent proxying, it is now called intercept mode and most of the documentation online is now out of date since it  refers to the old way of doing it.

About the firewall, you'll probably have to look at iptables directly.  Graphical tools like GUFW are mostly set up to affect an individual host, not a network.




thanks for the ideas :)

I just want to ask again regarding on the squid3. I already setup the squid3 on my ubuntu server 12.04 and successfully run it, but Im having a hard time blocking the proxy sites that employees accessing. Do you have any suggestions how to block the proxy sites?

thanks in advance

---

### Post by neil1188 on 2013-06-19
Do I need to setup as well a Dns server and dhcp server? so that the intercept mode of squid3 will work?

---

### Post by neil1188 on 2013-06-19
> **romeroc24 said:**
> Hello, I think you can do this.

ISP -> Modem -> router1 -> Server (Proxy, DHCP, DNS) -> Switch -> LAN

Put the server between router and switch, the server can contain 3 servers:

-DNS (bind9).
-DHCP (dhcp3).
-Proxy (squid3).

Try it!


what if i will have different physical server on then? is that ok?
and how can i block the proxy website using the squid? having a hard time on that

---

### Post by Lars Noodén on 2013-06-19
If there are not too many to be blocked, I would probably just add them to iptables rules.  Otherwise, there is also Dansguardian, which I have read about but never used.  I presume it still works with squid3.

---

### Post by SeijiSensei on 2013-06-19
You cannot block the proxy sites in squid since your users are sending their traffic to a remote IP and port.

You could do this with iptables, but you'll need to know the IP and port for every proxy in use.  If you have a clue who is doing this, you can add an iptables logging rule to track his traffic, then write an iptables rule to deny access to the IP/port being used.  I'd put the logging rules at the bottom of the ruleset so they pick up only those requests that don't already match some other rule.  If the proxy user is on 192.168.1.1, you can add this to the bottom of the ruleset (but above any sort of default deny rule):

```
/sbin/iptables -A INPUT -p tcp -s 192.168.1.1 -j LOG
```

The results will appear in /var/log/syslog.  If you log other activity in iptables, you can use the "--log-prefix" option to assign a label just to packets matching this rule.

---

### Post by neil1188 on 2013-06-19
I've tried this acl on the squid and **acl fb dstdomain .proxysite.com, **i guess it works for now since ive tried it and use the https:// to break through but still block. 

can i join the dns and dhcp server on the same physical server? including also the squid3? and i only have 2 lan card on it.

---

### Post by SeijiSensei on 2013-06-20
> **neil1188 said:**
> I've tried this acl on the squid and **acl fb dstdomain .proxysite.com, **i guess it works for now since ive tried it and use the https:// to break through but still block. 

can i join the dns and dhcp server on the same physical server? including also the squid3? and i only have 2 lan card on it.

Yes. Just make sure you specify the LAN-facing interface in /etc/default/dhcp3-server.

---

### Post by neil1188 on 2013-06-20
I have my dns and dhcp server installed and configured but when i connect my other computer it doesnt get an ip from dhcp server. the computer is connected directly on the server for testing.

what should be the problem?

---

### Post by neil1188 on 2013-06-21
guys ive already configure all of the servers that i've wanted ;

DNS 
DHCP
Squid

the only problem is how can i use the squid on dhcp server?. 
I made a script and make it executable.

#!/bin/sh  # Squid server IP SQUID_SERVER="10.0.0.1"  # Interface connected to Internet INTERNET="eth0"  # Address connected to LAN LOCAL="10.0.0.0/24"  # Squid port SQUID_PORT="3128"  # Clean old firewall iptables -F iptables -X iptables -t nat -F iptables -t nat -X iptables -t mangle -F iptables -t mangle -X  # Enable Forwarding echo 1 > /proc/sys/net/ipv4/ip_forward  # Setting default filter policy iptables -P INPUT DROP iptables -P OUTPUT ACCEPT  # Unlimited access to loop back iptables -A INPUT -i lo -j ACCEPT iptables -A OUTPUT -o lo -j ACCEPT  # Allow UDP, DNS and Passive FTP iptables -A INPUT -i $INTERNET -m state --state ESTABLISHED,RELATED -j ACCEPT  # set this system as a router for Rest of LAN iptables -t nat -A POSTROUTING -o $INTERNET -j MASQUERADE iptables -A FORWARD -s $LOCAL -j ACCEPT  # unlimited access to LAN iptables -A INPUT -s $LOCAL -j ACCEPT iptables -A OUTPUT -s $LOCAL -j ACCEPT  # DNAT port 80 request comming from LAN systems to squid 3128 ($SQUID_PORT) aka transparent proxy iptables -t nat -A PREROUTING -s $LOCAL -p tcp --dport 80 -j DNAT --to $SQUID_SERVER:$SQUID_PORT  # if it is same system iptables -t nat -A PREROUTING -i $INTERNET -p tcp --dport 80 -j REDIRECT --to-port $SQUID_PORT  #open everything iptables -A INPUT -i $INTERNET -j ACCEPT iptables -A OUTPUT -o $INTERNET  -j ACCEPT  # DROP everything and Log it iptables -A INPUT -j LOG iptables -A INPUT -j DROP



They say that this will finish the deal. But still failed
I can still access the facebook

thanks in advance guys

---

### Post by newbie-user on 2013-06-23
You can block facebook using regular expressions in squid. Basically, squid checks the request to see if facebook appears, and if it does, it blocks the request. Read here [http://wiki.squid-cache.org/SquidFaq/SquidAcl](http://wiki.squid-cache.org/SquidFaq/SquidAcl) in the section "How do I implement an ACL ban list?" and "How can I block access to porn sites?"

As for the script, I'm having a hard time reading it. Anyway, I would suggest creating a ruleset for iptables and saving it somewhere. First set up the rules, then create a save file, the reload the save file every time the server starts:
```

#save your iptables config
iptables-save > /path/to/iptables/save/file

#to reload iptables save file
iptables-restore < /path/to/iptables/save/file

```
To autoload iptables during booting, create an executable script in /etc/network/if-pre-up.d/ as shown below:
```

#!/bin/bash
iptables -F
iptables-restore < /path/to/iptables/save/file
exit 0

```

---

### Post by neil1188 on 2013-06-23
thanks all !!! I'ts already working specially to sensei for sticking on me and have a lots of patience :D thanks all

---

### Post by neil1188 on 2013-06-23
oh oh.. the https is open again :(

---

### Post by newbie-user on 2013-06-24
Did you try to block port 443 with iptables?

---

### Post by SeijiSensei on 2013-06-25
I don't see any rule in that mess of text that refers to HTTPS traffic.  Blocking that is a whole other ball game since trying to do it with squid will generate complaints about "man-in-the-middle" attacks.  You have to either disable HTTPS entirely by blocking requests to port 443, or [blocking requests to selected remote sites]("http://ubuntuforums.org/showthread.php?t=2155259&p=12696710&viewfull=1#post12696710").

---

