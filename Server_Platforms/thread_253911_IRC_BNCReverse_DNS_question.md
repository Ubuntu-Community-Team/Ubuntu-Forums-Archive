---
title: "IRC BNC/Reverse DNS question"
date: 2006-09-09
forum: Server Platforms
---

### Post by Kurt` on 2006-09-09
Hi,

I've seen people joining various IRC channels connected via BNCs. They use them to change their hosts, e.g. [email]kurt@is.the.best.net[/email]

I've asked a few people, and they all use psyBNC.

My question is this, if an IP address already has a reverse DNS to a hostname (say, from a hosting provider), how would you setup a BNC to use a "custom" domain name in a manner like that?

Thanks!

---

### Post by Kurt` on 2006-09-12
Nobody on these forums knows how reverse DNS lookups work? :X

I've read all the material I could find ([http://www.dnsstuff.com/info/revdns.htm](http://www.dnsstuff.com/info/revdns.htm), [http://en.wikipedia.org/wiki/Reverse_DNS](http://en.wikipedia.org/wiki/Reverse_DNS), etc.) but I still can't find out how it's possible to have multiple hostnames be the reverse DNS of a given IP. Does this require an extra IP or something?

---

### Post by chrisfay on 2006-09-12
If you want to have a custom reverse record in IRC than you are correct; you will need to use a BNC service. Those services do not actually add a reverse entry for your IP but rather provide a proxy service for your connection to IRC which displays your chosen host name. Keep in mind that these services, unless reputable, have a tendency to use a users info to exploit identities in IRC. 

In contrast to domain names, your ISP is responsible for DNS resolution regarding your reverse DNS entries. In order to obtain a reverse entry other than your generic ISP entry, you either must get your ISP to add one to their DNS server or hope they will allow you're personall DNS server to be authoritatve for your reverse records. If you're not given a static IP, they will most likey deny you due to the possibility for unnotified abuse using their IP's.

---

### Post by Kurt` on 2006-09-12
Ok, so I have a dedicated server with 2 IP addresses. Each IP has a reverse DNS entry already.

If I wanted to run a service with a custom reverse DNS (not necessarily a BNC), I would simply configure BIND9 to have an authoritative record for the reverse lookup?

---

### Post by chrisfay on 2006-09-12
> would simply configure BIND9 to have an authoritative record for the reverse lookup?

No...

In order to obtain a reverse entry other than your generic ISP entry, you either must get your ISP to add one to their DNS server or hope they will allow you're personall DNS server to be authoritatve for your reverse records.

In either case, you must contact them to find out what they will allow you to do regarding reverse entries.

---

### Post by Kurt` on 2006-09-12
Awesome, thanks for the replies!

---

### Post by chrisfay on 2006-09-12
NP :mrgreen:

---

### Post by Kurt` on 2006-09-14
Another question for you guys:

I requested delegation of my dedicated server's IPs from my host. They complied, and said it would take a while to take effect.

Now when I run this command (where w.x.y.z = one of my IPs): # host w.x.y.z

I see: z.y.x.w.in-addr.arpa domain name pointer ns1.my-domain.com.

This means my nameserver has full authoritative rights for setting the reverse DNS of my IPs, correct? (If that's the correct terminology)

If so, I may be looking at a bind9 configuration issue then...

Thanks in advance! :)

---

### Post by Kurt` on 2006-09-18
Any ideas? I'm not too confident with DNS yet. :(

---

### Post by madmonk3y on 2007-06-12
> **Kurt` said:**
> I've asked a few people, and they all use psyBNC.

A warning about PsyBNC ... because even if you get psybnc compiled, it probably won't run as expected:

[http://ubuntuforums.org/showpost.php?p=2829953&postcount=1](http://ubuntuforums.org/showpost.php?p=2829953&postcount=1)

Try the above link.  If you still want to install PsyBNC knowing that and why it won't work correctly, here's the packages you need to be able to make menuconfig and have the compile complete (with warnings and future instability):

[http://ubuntuforums.org/showpost.php?p=2830116&postcount=5](http://ubuntuforums.org/showpost.php?p=2830116&postcount=5)

---

