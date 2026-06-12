---
title: "Squid3 transparent proxy and users behind their own NAT"
date: 2011-02-09
forum: Server Platforms
---

### Post by seizer on 2011-02-09
Hi guys, 
I've  set up , mostly, successful transparent squid on my network. 

Network diagram: 
users<---->server (with squid installed and working)<---->router<---->internet 

Nat is done on server. 

Problem occurs when some of my clients use own wi-fi routers/routers, which do another natting: 
user<---->users_router<---->server (with squid installed and working)<---->router<---->internet 

Of course, ping or other services works fine on those computeres, except port 80 (http). 

My squid config: 
[http://pastebin.com/CrHvSbtT](http://pastebin.com/CrHvSbtT)

Thank you in advance.

---

### Post by wormyblackburny on 2011-02-09
I'm not positive on this one, but the problem has to be in this section. I notice you have the 192.168.0.0 network listed.... Was this your attempt at allowing the IP range a computer would get from an attached router? If so, you might try adding 192.168.1.0/24 network (as this is what the majority of routers use as default IP range (Linksys, Netgear etc..). I'm not sure of your network configuration, so it is tough to tell why attached routers wouldn't be allowed as long as the IP that is assigned to THEM is in the 172 range you listed since the IP's behind the router are NATted anyway. I guess it is worth a try....

# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
#acl localnet src 10.0.0.0/8    # RFC1918 possible internal network
acl localnet src 172.16.0.0/16    # RFC1918 possible internal network
acl localnet src 192.168.0.0/24    # RFC1918 possible internal network
#

---

### Post by seizer on 2011-02-10
I've added new net - 192.168.1.0/24. However, without expected results...
I think it's sth with routing/iptables/nat because, when I was trying to use proxy from net not listed in acl, squid gives me error page - forbidden.

"When Squid is in a DMZ between the router and Internet"
[http://wiki.squid-cache.org/ConfigExamples/Intercept/IptablesPolicyRoute](http://wiki.squid-cache.org/ConfigExamples/Intercept/IptablesPolicyRoute)
Do you think that section maps my problem?

---

### Post by elico on 2011-02-10
well it depends if the routers are using the same lan settings and it seems that many routers do use the 192.168.1.0 or 192.168.0.0 network
so if you can change it to some other network like 192.168.222.0 it might solve some of the problems in nat.

hmm can you please supply a "config only" info in the pastebin?
also i really recommed you to change the http 3128 ...
to http 127.0.0.1:3128 ...
cause if not protected by firewall people can use your proxy..
and you didnt gave us any iptables rules.
it might be from the iptables rules.
and by the way, is this proxy doing some url filtering?(looong rubbish config file).
if you telnet to the server 3128 port do you get something?

---

### Post by seizer on 2011-02-10
Iptables rules:
```
# Transparent Proxy
#iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to 192.168.0.1:3128
#iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128
```
Where, eth1 is my internal interface and eth0 is external

No, I'm not doing any filtering, new config without comments:
[http://pastebin.com/uQxPhznx]("http://pastebin.com/uQxPhznx")

When I've changed http_port directive to 127.0.0.1:3128, no one could connect to proxy, so I've changed to 192.168.0.1:3128, where 192.168.0.1 is address of eth1.

Telneting to proxy shows nothing...

Telenting from server (via  loopback) shows:
```

Trying 192.168.0.1...
Connected to 192.168.0.1.
Escape character is '^]'.
```

---

### Post by elico on 2011-02-10
well if it's a transparent proxy than no one suppose to connect it.
ok so one problem at a time.
use these 
```

http_port 127.0.0.1:3128 transparent
http_port 192.168.0.1:3128 transparent

```

your iptables settings are wrong in a way.
you dont need dnat just a redirect in your case.
```

#iptables -t nat -A PREROUTING -s 192.168.0.0/24 ! -d 192.168.0.0/24 -i eth1 -p tcp -m tcp --dport 80 -j  REDIRECT --to-ports 3128

```

this will do whatever you need.

also for security disable anything you dont need to be enabled.
i recommend these settings cause you dont need the commented ones.
if no one is having problems with the nat than fine.
i recommend you to change your network to none default network such as 192.168.0.0/24 but use a uniqe like network as
192.168.222.0/24 it's not standard.

if the clients on the other lans that are natted second time are getting problem the first thing to check is:
```
ping 192.168.0.1 
```
from one of the natted computers.
also make sure that they are using proper DNS settings and can do a nslookup.
if they can do nslookup and ping to any server on the internet then sure they can surf and some other settings on your server\squid\iptables is wrong.

hope it helped you.
```

#acl localnet src 172.16.0.0/16  # RFC1918 possible internal network
acl localnet src 192.168.0.0/24 # RFC1918 possible internal network
#acl localnet src 192.168.1.0/24
#acl localnet src 172.17.0.0/16
```


in this case of transparent proxy no one should and need to connect directly to your proxy server.
hope you will manage.

---

