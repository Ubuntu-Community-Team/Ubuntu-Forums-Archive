---
title: "Can't see server from internet"
date: 2006-09-22
forum: Server Platforms
---

### Post by ryanst on 2006-09-22
Hi all,

This seems mike a pretty basic problem but it has me absolutely stumped.  I got my server set up and all my stuff migrated to my Ubuntu server and everything seems to work fine... or so I thought until I tried to access the server from outside my network.  I"ll explain the behaviour better.

When I'm on my network I can access the server via it's internal IP (192.168.X.X) or throught my dyndns account (xxxxxx.dyndns.org)  or through my domain ([www.xxxxxxxxx.ca)](www.xxxxxxxxx.ca)), no problem, all works well.  I have my router set to forward port 80 to 192.168.x.x (yes, it is static) for my server.  As I mentionned, this all works fine.  However, when I try to access my website from somewhere else I get no response.  I'm totally stumped.  The configuration I just did above is all I ever did for my windows apache server hence why i'm confused.

I was thinking that maybe ubuntu has a software firewall enabled but that should prevent me from accessing the site from inside the network as well.   Unfortunately I have no clue how to check that a) because I'm fairly new to linux and have no idea where to look for that b) because I am completely in text mode.  no GUI installed whatsoever so I find it harder to poke around.

Any ideas?  I'm stumped.

Ryan

---

### Post by fstab on 2006-09-23
Hey Ryan,

It is possible that the firewall on your web server is dropping packets whose source IP address is not on the LAN, but its not likely.

Use this command to list your current firewall rules:

```
sudo iptables -L
```

Sample output:
```
sh-3.1$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

Post your output and I'll have a look.

---

### Post by Tobbera on 2006-09-24
/etc/hosts.allow
/etc/hosts.deny
?

---

### Post by ryanst on 2006-09-24
my output looks identical to what you posed.

Sorry for the delay.  Thanks for the help.

---

### Post by ryanst on 2006-09-24
Also, there are no entries in the hosts.allow and hosts.deny files.

---

### Post by Miademora on 2006-09-24
Did you make sure your dyndns account gets updated with the internet ip adress?

---

### Post by ryanst on 2006-09-24
It updates correctly.  Besides... even if it didnt, my IP only changes around once a year... it hasn't changed in the last 4 months.  The DynDNS is only really there just for good measure.

Thanks.

---

### Post by fstab on 2006-09-26
If your output of iptables -L looks the same as mine, then you don't have any software firewall running, so at least you can eliminate that as a potential source of the problem.

---

### Post by ryanst on 2006-09-26
so where do I look next?

---

### Post by fstab on 2006-09-28
There's a couple things I think it could be.  1) The router isn't forwarding properly - check the setup and ip addresses involved.  2) DNS lookup is failing - try to access your web server from outside your network by entering the IP address of your router instead of the hostname into your web browser.

---

