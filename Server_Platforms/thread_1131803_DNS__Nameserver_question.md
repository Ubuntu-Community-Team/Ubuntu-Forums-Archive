---
title: "DNS / Nameserver question"
date: 2009-04-21
forum: Server Platforms
---

### Post by andrewfashion on 2009-04-21
I officially setup my first web server w/ ISPconfig 3 on Ubuntu Server 8.10! YAY:) It's awesome

So I have some questions I am confused about...

I have my router, with specific ports open to allow the webserver to be seen. I setup the DNS server, and registered nameservers with my domain provider pointing the nameservers to my external IP via Comcast

my external ip: 76.x.x.1

It seems, when ever I setup a domain on my server and point the domain to my new nameservers, they always want 2, ns1.domain.com and ns2.domain.com, but if ns1.domain.com is pointing to 76.x.x.1, where the hell do I point ns2?

I've always noticed real hosting companies have ns1 pointing to .1 and ns2 pointing to .2, but I only have one external ip address?

Am i confused, am i doing this right? I basically just want to host my own websites and nameservers, and everything seems to be working fine, just confused by what to point ns2.domain.com to.

Thank you!!! :D

---

### Post by BkkBonanza on 2009-04-21
You are supposed to have 2 ips using 2 machines for redundancy. You can point them to the same ip if it allows that but it's not a good idea. 

Why do you want to run nameservers? You don't need to. It's a lot easier to just use your registrars nameserver unless you have some real specific need to run your own. Your registrar's will be more reliable than yours. And if you are on dynamic ips with comcast then it's an even worse idea. 

It seems everyone's running around in circles nowadays trying to run their own dns when there is very little reason to do that unless you're a big company or managing many servers and need special control.

---

### Post by andrewfashion on 2009-04-21
I just want my own test server in my basement with a real domain, if I don't have my own dns.nameservers, how can I point the domain to my server?

thanks!

---

### Post by BkkBonanza on 2009-04-21
You go to your registrar control panel and revert the nameserver back to them (which you just pointed at your own). Then go to the dns part of the control panel and add records for dns for your sites.

Typically you will want an A record for the main domain name. Probably a CNAME record for aliasing www onto the main one. And likely an MX record for the email server. These would all be setup with your machine's public ip. Any other subdomains or domains you have can also be added there.

I'm assuming you have a half decent registrar - pretty much all of them nowadays have a fairly good dns control panel just to be competitive. Many of them also support dynamic dns if you need. If your registar has an awful control panel with poor functionality then you can point your nameservers to a free public one like zoneedit.com or sitelutions.com. And then edit the dns there. There's lots of decent free ones around and also a few that charge a fee. Pretty much all of them will perform better than doing dns on your home server. They will be in a data center 24/7/365 and usually have resolve times in the 20-50 ms range. 

DNS is done so much and affects site load times quite a bit so it is worth having it handled by a fast server especially if it's free. I did a few tests with several and found that mine being done at name.com were very good.

---

### Post by kpatz on 2009-04-21
You can use your registrar's name servers and still have DNS entries that point to your server.  For example, if you register yourdomain.com, you'd use their nameservers, but then you would set up an A record, for yourdomain.com that points to your IP.  Then when you look up yourdomain.com, it will resolve to your IP.

You may want to look into DynDNS or Zoneedit, as they provide facilities for dynamic IP users, where if/when your IP changes, your DNS records get updated to reflect this.

That's another issue with running a DNS server on a dynamic IP.  If your IP changes, the root nameservers will have to be updated in order for your domain to resolve.  It's better to keep the DNS on the registrar's server and then just point to your server for web or whatever.

---

