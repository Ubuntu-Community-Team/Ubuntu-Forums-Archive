---
title: "apache block url and only allow approved."
date: 2013-02-18
forum: Server Platforms
---

### Post by erikustwo on 2013-02-18
Apache issue and need help running ubuntu server 12.04.

We have to few WAN IP's so we have several hostnames pointed to the same WAN IP in the DNS.
ex. mrbig.domain.com and whoat.domain.com. In the firewall we have rules that NAT to different internal servers.

ex..(mrbig) 12.123.123.23:3000 -> 192.168.1.100:3000 and 
(whoat)12.123.123.23:3001 > 192.168.1.200:3001.

So what I  want mrbig.domain.com with WAN IP 12.123.123.23  only accept port 3000 and whoat.domain.com only accept port 3001 in apache.

I have tried iptables and ufw with rules.
iptables -I INPUT 1 -p tcp --dport 3001 -m string --string "mrbig.domain.com" --algo kmp -j DROP

Have tried using [authz_host ]("http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html")

---

### Post by GordThompson on 2013-02-18
There is a ServerFault article [here]("http://serverfault.com/questions/409917/how-to-modify-the-port-apache2-is-running-on-for-each-virtualhost-using-namedvir") that describes something similar to what (I think) you're trying to do.

---

### Post by koenn on 2013-02-18
```
ex..(mrbig) 12.123.123.23:3000 -> 192.168.1.100:3000 and
(whoat)12.123.123.23:3001 > 192.168.1.200:3001.

So what I want mrbig.domain.com with WAN IP 12.123.123.23 only accept port 3000 and whoat.domain.com only accept port 3001 in apache.
```

If I understand this correctly, you shouldn't have any apache on 12.123.123.23, because that 's just NAted/routed to the 192.168.1.n servers.

Secondly, as you are NATing ports 3000 and 3001 on your internal servers, the apache on those servers should be configured to be listening on 3000 and 30001 respectively, right ? 

Lastly, your "drop' rules don't make sense - if no services are listening, no connection is possible so you don't need to go through all that trouble of dropping connection attempts that would get rejected automatically already.
 If you really want to, you can make a default DROP policy, and ALLOW -p tcp -dport 3000 or so,   but you're gonna think this trough - e.g. depending n where you run the iptables, you're gonna need INPUT and/or FORWARD rules.


but start with making sure apache listens on the adresses and ports you want to use.

---

