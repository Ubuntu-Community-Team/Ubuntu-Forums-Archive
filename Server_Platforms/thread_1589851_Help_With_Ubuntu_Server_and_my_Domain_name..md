---
title: "Help With Ubuntu Server and my Domain name."
date: 2010-10-07
forum: Server Platforms
---

### Post by bvong20 on 2010-10-07
Hi everyone,

I'm relatively new to the Ubuntu Linux OS, but I feel like I'm catching on fast.
Recently, I've set up Ubuntu Server on a desktop at home, and I'm trying to make it a web server.

This is what I'm looking for:

I want the server to be accessed by typing [http://www.easilykey.com](http://www.easilykey.com) into any web browser with Internet access and I want [www.easilykey.com]("http://www.easilykey.com") to be the server name used to connect with SSH.

I have:
the newest version of Ubuntu Server 64bit
Apache 2
MySQL
and PHP
and the domain easilykey.com purchased from godaddy.com

I just dont know how to put it all together.:confused: So if anyone could toss me some advice, or maybe a link to a good tutorial for my situation, It would be GREATLY appreciated.

---

### Post by robert_pectol on 2010-10-07
You need to be on a static IP with your ISP if you are going to host your own domain (nameserver, mailserver, webserver, etc.).  It needs to be a public, routeable IP.  Assuming you have that requirement met, simply login to your account at your domain registrar and designate your static IP as the one that will be answering authoritative queries for your domain.  Once that's in place, load up a nameserver with your zone file(s) on your IP and play to your heart's content!  :-)

---

### Post by confusedstingray on 2010-10-07
i few things first
if you have a static ip that has to be registered with  a company (the company i'm with calls it dns hosting) set your domain  easilykey.com to point to your ip 
that is step 1

next you have to set your router to allow any request through and send it to your server
also you have to set apache up to accept the request 
and you will need DNS as well
what you want to do i have being doing now for about 2 years 
i host my website and mail in my home

---

### Post by BkkBonanza on 2010-10-08
You can use a dynamic IP as well. It's not as stable because it may be down for a couple minutes when it changes. All you need to do with a dynamic IP is configure a dynamic dns client and make sure your DNS provider has support for dynamic updates. Most decent routers also have support for dynamic IP and just need user/pwd to be added.

When you register your domain name your registrar will usually have DNS services provided free. You should add suitable records there for your IP at home. Usually an "A Record" pointing your domain to your IP and a CNAME record for www. You can add other records as desired for email or other services. 

I would not recommend running your own DNS servers for a home-based server. It will be far less stable and available than the free one provided by your registrar and is just extra work and hassle that you can possibly mess up too. There are also third party free DNS providers like zoneedit.com and sitelutions.com (amongst many others). Dyndns.com is well known for there complete dynamic IP support.

After you have the DNS records added you will want to configure your router to "forward" ports for the services you need to have visible on the web. Port 80 for http, port 443 if you need SSL pages too, port 22 for your ssh. Port forwarding tells your router to open those ports and send any packets for them directly thru to the destination server. For more info on that just google your router make/model with the words "port forward" and no doubt you'll find a guide.

---

### Post by bvong20 on 2010-10-08
Thanks for the advice everyone! You're input has taught me quite a bit and now I have much better ideas for a solution. :popcorn:

---

### Post by robert_pectol on 2010-10-08
> **BkkBonanza said:**
> You can use a dynamic IP as well. It's not as stable because it may be down for a couple minutes when it changes. All you need to do with a dynamic IP is configure a dynamic dns client and make sure your DNS provider has support for dynamic updates. Most decent routers also have support for dynamic IP and just need user/pwd to be added.

Hence the reason I suggested he be on a static IP!  But yes, you can *finagle* it to work with a dynamic IP if you're willing to tollerate occasional interruptions.  Use of a static IP is so much less of a kludge for this sort of thing.
> **BkkBonanza said:**
> 
When you register your domain name your registrar will usually have DNS services provided free. You should add suitable records there for your IP at home. Usually an "A Record" pointing your domain to your IP and a CNAME record for www. You can add other records as desired for email or other services.

I would not recommend running your own DNS servers for a home-based server. It will be far less stable and available than the free one provided by your registrar and is just extra work and hassle that you can possibly mess up too.  There are also third party free DNS providers like zoneedit.com and sitelutions.com (amongst many others). Dyndns.com is well known for there complete dynamic IP support.

It's pretty easy to set up your own nameserver and designate a couple of slaves.  There are providers such as twisted4life that will slave your domain(s) for free.  If you're worried about stability issues in your name resolution on a home server, this is a good solution.  By running your own nameserver, you have ultimate control over your domain(s) and subdomains without having to make changes with your registrar.  You can even host others' domains if you like!  As far as messing things up, I'm assuming the OP is wanting to tinker and learn.  It's my opinion that avoiding a learning experience in the fear of messing things up, is not beneficial.  There are countless how-tos on it if he were to get stuck.  I guarantee he would learn a lot more about how things work.  But all this is on the assumption that no critical services will be relied on regarding the home network, and that it's more for fun and learning.  If that's not the case, then you really shouldn't even be attempting anything like this on a residential Internet connection.
> **BkkBonanza said:**
> 
After you have the DNS records added you will want to configure your router to "forward" ports for the services you need to have visible on the web. Port 80 for http, port 443 if you need SSL pages too, port 22 for your ssh. Port forwarding tells your router to open those ports and send any packets for them directly thru to the destination server. For more info on that just google your router make/model with the words "port forward" and no doubt you'll find a guide.

Yes.  This is good advice.  The applicable ports will need to be forwarded to the appropriate server(s).

---

