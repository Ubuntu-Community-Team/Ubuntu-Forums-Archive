---
title: "IPTable Rules to allow one domain and block all other HTTPS Traffic"
date: 2015-03-10
forum: Security
---

### Post by aamir3 on 2015-03-10
Hi!
I am using two Lans card in my proxy to route and filter traffic. One eth0 is connected to Internet and eth1 connected to internal network.

**I use the following code to block the HTTPS facebook. It's working fine.**
[FONT=Arial]iptables -A FORWARD -i eth1 -s 192.168.1.100 -p tcp --dport 443 -d [www.facebook.com](www.facebook.com) -j DROP[/FONT]
[FONT=Arial]
**I use this rule to block all HTTPS traffic for specific host.**
iptables -A FORWARD -i eth1 -s 192.168.1.100 -p tcp --dport 443 -j DROP

[B]What I want to do to allow only the destination gmail.com or [www.gmail.com](www.gmail.com) and block all other https traffic?
[/B]
Please help, Thanks[/FONT]

---

### Post by SeijiSensei on 2015-03-10
First we need to find the host's IP addresses:
```

$ host www.gmail.com
www.gmail.com is an alias for mail.google.com.
mail.google.com is an alias for googlemail.l.google.com.
googlemail.l.google.com has address 74.125.226.54
googlemail.l.google.com has address 74.125.226.53
googlemail.l.google.com has IPv6 address 2607:f8b0:4006:80e::2005

```
I'd go ahead and permit the entire 74.125.226.0/24 "subnet" in case Google adds more servers to that range in the future.  The rules look like this:
```

/sbin/iptables -A FORWARD -d 74.125.226.0/24 -p tcp --dport 443 -j ACCEPT
/sbin/iptables -A FORWARD -p tcp --dport 443 -j REJECT 

```
The second rule matches all destinations.

You should avoid using hostnames in iptables rules.  Usually the ruleset is loaded before domain name resolution has been set up, so only IP addresses work in that situation.

---

### Post by aamir3 on 2015-03-11
Hi!
Thanks for your reply.
I have tested the code.
```
/sbin/iptables -A FORWARD -i eth1 -s 192.168.10.100 -d 74.125.226.0/24 -p tcp --dport 443 -j ACCEPT
/sbin/iptables -A FORWARD -i eth1 -s 192.168.10.100 -p tcp --dport 443 -j REJECT
``` I am unable to open the gmail and all https traffic blocked. I tried to put the ip address of gmail.com (74.125.226.54) in browser it opens the google.com.

---

### Post by SeijiSensei on 2015-03-11
Well, the fact that you can connect to [https://74.125.226.54/](https://74.125.226.54/) means that the iptables rules are working as advertised.  Maybe you have a DNS problem?  What does the command "host www.gmail.com" return for you?

---

### Post by aamir3 on 2015-03-13
by doing host [www.gmail.com]("http://www.gmail.com"), it replied with details of gmail alias and ip addresses. DNS is working.

It's like same
host [www.gmail.com](www.gmail.com)
[www.gmail.com](www.gmail.com) is an alias for mail.google.com.
mail.google.com is an alias for googlemail.l.google.com.
googlemail.l.google.com has address 74.125.226.54
googlemail.l.google.com has address 74.125.226.53
googlemail.l.google.com has IPv6 address 2607:f8b0:4006:80e::2005

---

