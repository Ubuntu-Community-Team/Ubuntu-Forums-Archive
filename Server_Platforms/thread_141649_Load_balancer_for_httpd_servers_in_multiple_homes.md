---
title: "Load balancer for httpd servers in multiple homes"
date: 2006-03-08
forum: Server Platforms
---

### Post by evuraan on 2006-03-08
**Greetings**, elites..!! 

I've some web pages hosted on my Ubuntu @ home -- a [blogroll]("http://malayalam.homelinux.net/malayalam/work/head.html"), which is catering to readers from round the world. 

Lately, I've found volunteers with high speed residential internet access, running  httpd, willing (or rather bold enough?) to take part in a **Load balancing** scenario.

An incoming http request to the said page should be diverted to the best participating host. Best means, OSPF or weighted, or purely round-robin. 

I've been researching into this, read about [LVS]("http://www.linuxvirtualserver.org/"), [balance]("http://www.inlab.de/balance.html"), [pound ]("http://www.apsis.ch/pound/")etc. Guess it's been due time to take this question before you all. 

What would be the best way to do this...? 

The participating servers are in the internet, not in my private LAN. 

Many thanks in advance...!!

---

### Post by peterbrowne on 2006-03-08
i'd like to know how to do this as my website will have servers across Canada and i'll need to do this

---

### Post by 11hjpphty76lkjj on 2006-03-08
I'd like to know how to do this as well.  (I'm just adding this so I'm on the thread.)

Aaron

---

### Post by kmi on 2006-03-09
If I have correctly understood your needs, there seem to be different options to do this, they're all listed [there]("http://httpd.apache.org/docs/2.0/rewrite/rewrite_guide_advanced.html").

Well... maybe not the wonderful how-to you expected, but seems to do the trick... :)

(But that's probably not what you were looking for... you certainly would have found it a long time ago :/ )

---

### Post by robert_pectol on 2006-03-10
If you were to set up a nameserver that is authoritative for your domain, that you control, then you could round-robin it's responses.  Bind9 has this capability as I recall.  That way, each IP listed in the pool will get returned in the A record response, while rotating the IP list one-by-one in succession, to the incoming queries for your domain.  From the nameserver's point of view, each IP in the pool will receive equal referrals.  In practicality however, some of the IP's might see a little more/less actual traffic than others due to other factors such as number of nameservers in the chain that handled the particular query for your domain, cache expiry within each nameserver, etc.  But generally speaking, it should spread the load fairly equally among the IPs in your pool.

This option may present some challenges if you are offering other services on your domain such as FTP, SSH, etc. and you want to be able to reliably connect to a particular host.  In this case, using the specific host's IP instead of the domain name would be a work-around.  Mail for your domain shouldn't be a problem since your zone's MX records would remain the same across all queries (if your domain even handles mail, that is).  Anyway, good luck.

---

### Post by diebels on 2006-03-10
[QUOTE=robert_pectol]If you were to set up a nameserver that is authoritative for your domain, that you control, then you could round-robin it's responses.  Bind9 has this capability as I recall.  That way, each IP listed in the pool will get returned in the A record response, while rotating the IP list one-by-one in succession, to the incoming queries for your domain.  From the nameserver's point of view, each IP in the pool will receive equal referrals.  In practicality however, some of the IP's might see a little more/less actual traffic than others due to other factors such as number of nameservers in the chain that handled the particular query for your domain, cache expiry within each nameserver, etc.  But generally speaking, it should spread the load fairly equally among the IPs in your pool.[/QUOTE]Wouldn't that screw up php sessions and cookies?

~$ host google.com
google.com has address 64.233.167.99
google.com has address 72.14.207.99
google.com has address 64.233.187.99

How does google do it?

---

### Post by robert_pectol on 2006-03-10
[QUOTE=diebels]Wouldn't that screw up php sessions and cookies?

~$ host google.com
google.com has address 64.233.167.99
google.com has address 72.14.207.99
google.com has address 64.233.187.99

How does google do it?[/QUOTE]
Only for sessions which outlast the the DNS cache timeout, possibly.  However, this is usually hours or days.  For cookies that are designed to be particularly lengthy or persistant over a long time, couldn't you, as the developer of your Website, code them such that they allow for all known IP addresses in your pool?  I'm not a Web developer so we're entering unfamiliar waters!  :)

---

