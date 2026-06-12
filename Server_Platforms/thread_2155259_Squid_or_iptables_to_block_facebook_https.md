---
title: "Squid or iptables to block facebook https"
date: 2013-06-17
forum: Server Platforms
---

### Post by romeroc24 on 2013-06-17
Hello guys

My Squid proxy server its working perfectly but I want to block the web access to facebook.com on https, for the clients.

Do you prefer iptables or squid for block connections?

Please tell me how.

Thanks

---

### Post by SeijiSensei on 2013-06-18
You cannot block HTTPS connections via Squid without a lot of configuration both within Squid and on the clients.  The proxy will appear as a "[man-in-the-middle]("http://wiki.squid-cache.org/Features/SslBump")" attacker and the client's browser will complain.

We use iptables to block Facebook via HTTPS.  Facebook uses a large number of IP subnets, so you have to generate mulitple rules.  Here's my current list of Facebook IP subnets that need to be blocked:

```

31.13.24.0/21
31.13.64.0/19
31.13.64.0/24
31.13.65.0/24
31.13.66.0/24
31.13.68.0/24
31.13.69.0/24
31.13.70.0/24
31.13.71.0/24
31.13.72.0/24
31.13.73.0/24
31.13.74.0/24
31.13.75.0/24
31.13.76.0/24
31.13.77.0/24
31.13.78.0/24
31.13.79.0/24
31.13.80.0/24
31.13.81.0/24
31.13.82.0/24
31.13.83.0/24
31.13.84.0/24
31.13.85.0/24
31.13.86.0/24
31.13.96.0/19
66.220.144.0/21
66.220.152.0/21
69.63.176.0/21
69.63.176.0/24
69.63.184.0/21
69.171.224.0/20
69.171.239.0/24
69.171.240.0/20
69.171.255.0/24
74.119.76.0/22
103.4.96.0/22
173.252.64.0/19
173.252.70.0/24
173.252.96.0/19
204.15.20.0/22

```

I used sandyd's [method]("http://ubuntuforums.org/showthread.php?t=2145355&p=12648923&viewfull=1#post12648923") to generate the list.

Each rule includes one of those subnets like this:
```
/sbin/iptables -A INPUT -p tcp -d 31.13.24.0/21 --dport 443 -j REJECT
```

---

### Post by Lars Noodén on 2013-06-18
If you know the AS number of the network, you can also use whois to generate the list for you:
```

/usr/bin/whois -h whois.radb.net '!gAS32934' | tr ' ' '\n' | sort -n -k1,1 -k2,2 -k3,3 -k4,4

```

When you are building the firewall rules, be sure to [use REJECT instead of DROP](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject) to make life easier.

---

### Post by SeijiSensei on 2013-06-18
The post I linked to from sandyd provides the AS information.

---

### Post by Lars Noodén on 2013-06-18
Yes.  Though sometimes it is a little hard to massage HTML tables into workable lists of text.  Having two alternative methods of getting the networks won't hurt ... much.

---

### Post by romeroc24 on 2013-06-18
Thank you, amazing!

---

### Post by romeroc24 on 2013-06-18
Thank you, very useful!

---

