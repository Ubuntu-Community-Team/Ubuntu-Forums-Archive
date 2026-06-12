---
title: "SQUID - how do I ban *ALL* but one website?"
date: 2009-11-30
forum: Security
---

### Post by youbuntu on 2009-11-30
Hi people!. My friend wants an Ubuntu LTSP setup, where Firefox will *only* allow browsing to his site, and no other site. I know how to setup LTSP, but I need advice about how to setup SQUID to ban ALL sites except his (some kind of acl rule, I understand?).

Thanks

---

### Post by EJeanmaire on 2009-11-30
> **glossywhite said:**
> Hi people!. My friend wants an Ubuntu LTSP setup, where Firefox will *only* allow browsing to his site, and no other site. I know how to setup LTSP, but I need advice about how to setup SQUID to ban ALL sites except his (some kind of acl rule, I understand?).

Thanks

sudo nano /etc/hosts.deny

then at the bottom put:

ALL EXCEPT: thatonewebsite.com

---

### Post by youbuntu on 2009-11-30
Genius!. Thanks! :D

---

### Post by __p1n__ on 2009-11-30
> **EJeanmaire said:**
> sudo nano /etc/hosts.deny

then at the bottom put:

ALL EXCEPT: thatonewebsite.com

That's overkill EJeanmaire since the OP only wanted the restriction to web browsing via squid-proxy.

The actual squid acl to do what you want is:

acl his_site dst IPADDRESS
http_access allow his_site
http_access deny all

where IPADDRESS is the numerical octet of your buddy's site address.

Note that this binds the rule to a specific IP address.  This is good however you'll have to update the rule when/if your buddy's site address changes.

An alternative weaker form is:

acl his_site url_regex ^HTTP: //WWW.ABC.COM$
http_access allow his_site
http_access deny all

where HTTP: //WWW.ABC.COM is your buddy's website url.

This will work regardless of your buddy's website IP address but it can be faked out if your crafty users add an /etc/hosts entry mapping www .abc.com to an ip address corresponding to their actual desired website.  This will in turn likely fail if the user-desired website is on a webserver that's hosting multiple domains but that's another issue.

---

### Post by youbuntu on 2009-11-30
> **__p1n__ said:**
> That's overkill EJeanmaire since the OP only wanted the restriction to web browsing via squid-proxy.

The actual squid acl to do what you want is:

acl his_site dst IPADDRESS
http_access allow his_site
http_access deny all

where IPADDRESS is the numerical octet of your buddy's site address.

Note that this binds the rule to a specific IP address.  This is good however you'll have to update the rule when/if your buddy's site address changes.

An alternative weaker form is:

acl his_site url_regex ^HTTP: //WWW.ABC.COM$
http_access allow his_site
http_access deny all

where HTTP: //WWW.ABC.COM is your buddy's website url.

This will work regardless of your buddy's website IP address but it can be faked out if your crafty users add an /etc/hosts entry mapping www .abc.com to an ip address corresponding to their actual desired website.  This will in turn likely fail if the user-desired website is on a webserver that's hosting multiple domains but that's another issue.

uhmm... what? :?

Oh, and the previous solution - doesn't even work!!

---

### Post by __p1n__ on 2009-11-30
> **glossywhite said:**
> uhmm... what? :?


Put either of the 3-line entries into the squid.conf file.

Specifically either:

acl his_site dst IPADDRESS
http_access allow his_site
http_access deny all

or:

acl his_site url_regex ^http://www.abc.com$
http_access allow his_site
http_access deny all

where IPADDRESS is something like 192.168.0.1 and http ://www.abc.com is replaced with the url to your buddy's site.  The first example is better from an enforcement perspective but you'll need to update the rule if your buddy's IP address ever changes.

---

### Post by lykwydchykyn on 2009-11-30
I typically don't even bother with squid for something like this.  I just add a firewall rule to drop all outgoing port 80 traffic for the user in question (in my case, typically a kiosk user), then add another rule allowing it for the one site's ip.

Of course, if you only want to allow a specific site on the server, that doesn't work.

I'd give you the iptables commands for this, but I just cheat an use webmin to do it.

---

### Post by bodhi.zazen on 2009-11-30
+1 for using iptables for this.

Allow first (allow out to server_ip port 80 ) , then deny all other outbound traffic headed for port 80.

You can do this quite easily with ufw or gufw (or iptables directly).

---

### Post by youbuntu on 2009-11-30
> **__p1n__ said:**
> Put either of the 3-line entries into the squid.conf file.

Specifically either:

acl his_site dst IPADDRESS
http_access allow his_site
http_access deny all

or:

acl his_site url_regex ^http://www.abc.com$
http_access allow his_site
http_access deny all

where IPADDRESS is something like 192.168.0.1 and http ://www.abc.com is replaced with the url to your buddy's site.  The first example is better from an enforcement perspective but you'll need to update the rule if your buddy's IP address ever changes.

Nope, that doesn't work at all. Added to squid.conf, rebooted and it STILL allows ALL sites.

---

### Post by sobol_rz on 2009-11-30
squid+squidguard ..(or maybe only squid will be all you need;] ). don't make black list ... make white list
squid - transparenty > move http to go throu proxy(iptables) 
make page on server and tell traffic to go to this page:)

regards

---

### Post by bodhi.zazen on 2009-11-30
I Can't stand to watch any more !!!

Let us assume your friend's server is at 192.168.0.100 :

```
# Allow http traffic to your server
sudo iptables -A OUTPUT -d 192.168.0.100 -p tcp --dport 80 -j ACCEPT

# Allow traffic for root, needed to update (apt-get update, apt-get install, etc).
# Block all other traffic
sudo iptables -A OUTPUT -m owner ! --uid-owner 0 -j DROP
```Just change "192.168.0.100" to your friends server. Note : This will block all http traffic by the user.

Now those rules are tight, you can relax them if you wish.

No need for squid ;)

---

### Post by sobol_rz on 2009-11-30
> **I need advice about how to setup SQUID to ban ALL sites except his (some kind of acl rule, I understand?).**
bodhi.zazen he wanted squid :P

---

### Post by bodhi.zazen on 2009-11-30
Aye, but squid is overkill, why set up a server (squid) and proxy http requests from all clients, one by one, when a few iptables rules will do ?

---

### Post by sobol_rz on 2009-11-30
maybe because one day his friend will be have two sites (vhost) dropping sites by ip - I think it's not a good idea.. maybe for few days ...

---

### Post by bodhi.zazen on 2009-11-30
LOL, add another rule for iptables if necessary. Still easier then configuring squid, IMO.

Why the avoidance of iptables ?

Using squid seems to be fitting a square peg through a round hole.

---

### Post by sobol_rz on 2009-11-30
another rule?
for vhost ... Two sited on same ip and you want next rule??? 
fox exemple ip 192.168.100.25
addresses [www.website.org]("http://www.website.org")
                [www.2website.org]("http://www.2website.org")

How you want to disallow to go on [www.2website.org]("http://www.2website.org") but allow to [www.website.org]("http://www.website.org") ??

---

### Post by bodhi.zazen on 2009-11-30
use /etc/hosts, lol

This debate is senseless, use squid if you must. There is more then one way to skein the cat and you still yet have the OP to assists.

---

