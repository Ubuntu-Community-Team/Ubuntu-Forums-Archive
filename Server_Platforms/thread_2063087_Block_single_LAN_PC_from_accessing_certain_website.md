---
title: "Block single LAN PC from accessing certain websites while allowing others"
date: 2012-09-26
forum: Server Platforms
---

### Post by Demented ZA on 2012-09-26
I have an Ubuntu server acting as a firewall/gateway to a lan consisting of 30 PC's.
Of these PC's, only some may access the internet.

I now need to allow a single PC to access the internet, but I need to be able to block certain websites such as twitter.com and Facebook and some others (as its proving to be counter-productive).

On the Ubuntu server, I have squid running (not transparent) that allows PC's to browse the net after authenticating.

After setting up some rules in squid, I'm finding that its not blocking the sites I've designated.

Also, how does https factor into this?

Before I post configs and logs and whatnot, I'd like to just get someone's opinion as to whether I'm going about it the right way. Maybe someone can tell me in general how it should be accomplished?

Thanks in advance.

---

### Post by SeijiSensei on 2012-09-26
[Squid]("http://wiki.squid-cache.org/Features/SslBump") cannot intercept HTTPS requests without appearing to the browser that a "man-in-the-middle-attack" is taking place.

For HTTPS requests, you need to block them with iptables.  That means getting the complete list of IP addresses for the sites you wish to block.  Sometimes they fall into a nice IP subnet, but some sites have a variety of servers at different addresses.  My current Facebook SSL list includes:

```

31.13.76.10
31.13.77.42
31.13.77.58
69.171.228.0/25
69.63.190.0/25
66.220.146.0/25
66.220.147.0/25
66.220.149.0/25
66.220.153.0/25
66.220.156.0/25
66.220.158.0/25
69.63.189.0/25
69.63.190.0/25
69.171.224.0/25
69.171.228.0/25
69.171.229.0/25
69.171.234.0/25
69.171.242.0/25
69.171.247.0/25

```

---

### Post by Doug S on 2012-09-26
I wrote and tested some facebook blocking iptables rules a few days ago for another thread, although my list was a little different than Seiji's. Anyway, the code is posted [there.]("http://ubuntuforums.org/showthread.php?t=2060330")

---

### Post by SeijiSensei on 2012-09-26
I tried to be as minimal as possible to avoid false positives.  After compiling a bunch of FB requests from the firewall, I ran ping scans with nmap (e.g., "nmap -sP 69.171.247.0/24") against suspect IP subnets to resolve the addresses back to hostnames.  For some reason, most of FB's addresses reside in the bottom half of a /24 (aka a "class-C"), so I used a /25 mask to block only hosts between 1 and 127 and not hosts from 129-254.

Many sites share address space with other sites so it pays to be careful to verify which addresses you need to block.  Otherwise you end up with "collateral damage" and block sites that should be permitted.

---

### Post by Demented ZA on 2012-09-28
Thank you guys for the response. This was exactly what I needed. I was just asked if its possible to do this during certain times of the day. Given the above implementation, I suppose using a shell script to do and undo the extra iptables rules invoked by a cron job would be the way?

---

### Post by Demented ZA on 2012-10-23
In trying to find a solution to a problem I posted [here]("http://ubuntuforums.org/showthread.php?t=2066690"), I found a way to have squid block URLs, including https urls. My other post covers how to lock a user, or group of users to a single pc, as the objective of this post is to block traffic between some web-servers and a single lan IP. If the user is not restricted to a specific machine, he/she can bypass the restriction, by using a colleague's PC. 

I guess this solution is not a replacement for iptable rules, but it adds another layer of redundancy, and allows the option of directing users to custom error pages.

Regarding SSL, since squid has to decide what to do with ssl, (such as allow direct connection), and log the request, there exists an opportunity for squid to reference access controls and respond accordingly, such as to deny the connection. This got me thinking.

All I did was write an acl to define bad sites:
```
acl Badsites dstdomain "/etc/squid/badsites.acl"
```Current contents of /etc/squid/badsites.acl:
```
.facebook.com
.twitter.com
31.13.76.10
31.13.77.42
31.13.77.58
69.171.228.0/25
69.63.190.0/25
66.220.146.0/25
66.220.147.0/25
66.220.149.0/25
66.220.153.0/25
66.220.156.0/25
66.220.158.0/25
69.63.189.0/25
69.63.190.0/25
69.171.224.0/25
69.171.228.0/25
69.171.229.0/25
69.171.234.0/25
69.171.242.0/25
```I included the IP's I added to IPtables, just incase someone tries to navigate to a site by IP. (Again, even if I didn't add the IP's, my firewall would have blocked it, but redundancy doesn't hurt.)

Then, under my access controls, I define an access restriction reply rule, before anything else:
```
http_reply_access deny Badsites
```

Edit:
Or
```
http_reply_access deny ManagerPC Badsites
``` as I have it along with the example in my other post, in order to only block bad sites on a specific pc, and specific users should you so wish.

---

