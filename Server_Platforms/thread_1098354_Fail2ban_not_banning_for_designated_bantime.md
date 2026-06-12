---
title: "Fail2ban not banning for designated bantime"
date: 2009-03-16
forum: Server Platforms
---

### Post by mistypotato on 2009-03-16
Hi,

bantime in fail2ban is designated in seconds.

So, a 10 minute ban would be set by setting bantime to 600.

I have Fail2ban set to 259200 seconds for bantime on vsftpd yet it's unbanning after just 26 seconds.

It appears that fail2ban may have a 3 digit limit on bantimes because it it rounding my 3 day bantime (60sec x 60min) = 3600secs/hr x 24 = 86400secs/day x 3days = 259200 seconds

I'll bet this is one of those times I'm doing something so obvious that I cannot see it :P

Anyone with brain cells left wanna help me out here :P

---

### Post by HermanAB on 2009-03-16
The better method is to use a rate limit rule with iptables.  It is just one line and it works:

```
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
```

[http://aeronetworks.ca/firewall-howto.html](http://aeronetworks.ca/firewall-howto.html)

Cheers,

Herman

---

### Post by mistypotato on 2009-03-17
Here's a great link on iptables.

[http://iptables-tutorial.frozentux.net/iptables-tutorial.html]("http://iptables-tutorial.frozentux.net/iptables-tutorial.html")

For me personally, it's overwhelming.

One of the unfortunate things about ubuntu and Linux is that although I would LOVE to read up and learn everything there is to know about computers, networks and all the intricacies, the truth is that I just don't have the time to allocate to that :(    By the time I finish with my hectic and tiring days, there is SO little precious time left.

With that simple fact in mind, I would like to ask......

How could one cut to the chase, and implement this wonderful piece of code (and I think I mean that)?

[COLOR="Blue"]iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT[/COLOR]

I don't even know where it would go?

I checked your site.  Nice information :P

---

### Post by HermanAB on 2009-03-17
First, run it from the command line, to make it take immediate effect, then add the line to /etc/rc.d/rc.local, to make it take effect every time you reboot.

Cheers,

Herman

---

