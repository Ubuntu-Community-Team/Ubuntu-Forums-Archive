---
title: "Squid ? how and is it nessesary"
date: 2007-11-13
forum: Server Platforms
---

### Post by Helbo15 on 2007-11-13
Hi 

I'm having a ubuntu system with bind9, iptables, dhcpd, samba 3.x and Webmin as my computer there is handling and sharring the internet  and the local net in my house

 however I've been reading that squid can manage much more like caching sites and monitoring and so on 

is it posible 4 me just to install squid on top of that system or do I need to change the old system dramaticaly ?

in the latter case how much do u recon should be changed ?

and in any case is squid just some technically candy I don't need  ?

---

### Post by pete.dawgg on 2007-11-13
squid is a very powerful and flexible software. if you like experimenting with technical stuff you can have a lot of fun and learn many things.
on the other hand, for a home with maybe ten clients it's probably overkill - and even though you can run it with a little config with maybe 50 lines it it not sth. that runs intuitively right out of the box.

i suggest the standard procedure: first think about the goals to reach and then about the software you want to use ;)

squid is definitely not > just candy, but a copmany with 600 clients and a strict internet-policy ist very different from a home with a broadband-conection.
(but if you're into the technical challenge AND the home-lan's superuser, try transparent proxying ;) )

if you just have a couple of users it should be no problem installing squid on top of the existing system, just be careful with its parameters for memory and disk-use. as long as two services don't listen on the same port there should be no interference with the installed services, either.

---

### Post by Helbo15 on 2007-11-13
okay :) sounds interresting 

I think I'll try to install it just one more question I forgot to mention that I have a teamspeak service on it.

it is my understanding from ur statements that squid won't be interferring with that service as long as I use difrents ports am I right ?

and is it posible to have a webserver behind the ubuntu system after squid is installed or will it be interferring with that ?

---

### Post by pete.dawgg on 2007-11-14
as long as your iptables-rules allow it and each application has its own port(s) thats no problem; you can run services on the same box or on a different one as long as the right network-packets get thru (configuration of iptables).
in a security-conscious scenario i would not recomend running squid and the firewall on the same box, but at home there should be no problem.
as long as you keep ports and sockets apart you can run the webserver even on the same machine; for fun and experience it is even possible to run two squids on the same box: one as caching-proxy for the internal net and one as reverse proxy for a webserver in the dmz.
have fun!

---

### Post by crouton on 2007-11-14
From Wikipedia: [Squid_cache]("http://en.wikipedia.org/wiki/Squid_cache")

> 
Squid is a proxy server and web cache daemon. It has a wide variety of uses, from speeding up a web server by caching repeated requests, to caching web, DNS and other computer network lookups for a group of people sharing network resources, to aiding security by filtering traffic. Although primarily used for HTTP and FTP, Squid includes limited support for several other protocols including TLS, SSL, Internet Gopher and HTTPS. The development version of Squid (3.0) includes preliminary IPv6 support.


It is useful software to know and understand but the usefulness in home/small office situations is marginal at best (unless you have special circumstances that Squid can mitigate.)

---

### Post by Helbo15 on 2007-11-20
well for me it's all about learning :)
my education fall short in the Linux area we used about 2.5 years to learn how to use M$ as both servers security box and desktop computers and about 2 weeks to learn about Linux :( 
so I put it on myself to learn as much as I can about Linux :) 

but I fail to find motivation if I can't find a direct use for what I'm doing so I decided to set up a Ubuntu as a firewall and let it provide services to my home network that way I found my motivation :)
however squid sounds interesting but I'm beginning to doubt that I'll be able to find motivation if I risk messing up what I've already accomplished.

but you talk about my iptables to allow it does it mean that I should make it go through my firewall rules in FORWARD rule set and then redirect it to squid or should I redirect it to squid and then through the FORWARD rules ? or am I totally lost  here ?

---

### Post by HermanAB on 2007-11-20
There are two ways to dramatically speed up a home connection: DNS slave and Squid-cache.  

The nicest way is to set up Squid-cache as a transparent proxy.  However, while you are experimenting, just install it the default way and adjust your proxy setting in your browser to connect to it.  Go to the Squid-cache web site for details.  Don't run Squid-cache on a public server unless you know what you are doing, since it can be exploited by spammers.

Cheers,

H.

---

