---
title: "Free Internet DNS Service?"
date: 2008-03-19
forum: Server Platforms
---

### Post by GenuineXP on 2008-03-19
So I just recently setup a personal server on my network running Ubuntu and lots of useful services like Apache (HTTP, HTTPS, etc.), FTP, SVN, etc. I also setup a DNS using bind9, lots of reading, and tons of coffee.

DNS has me a little mystified. I understand the underlying concepts, but some of it is a tad confusing. My DNS works just fine on my LAN as I expected, but I'm wondering if there's an easy and free way to provide a domain name over the Internet.

I'd really like to use the exact domain names I've chosen (I've already tried browsing them online and they don't appear to be in use on the Internet). Is there such a free service?

If not... well, why not? I don't completely understand why DNS service would have to cost money (other than preventing spamming the world with billions of new domain names every day). I've read about the master DNS servers and even found a page where their IPs are listed. How is access to these machines controlled?

Is there a way to somehow expose my DNS to the Internet so that the domain configuration on my machine is reflected online?

Thanks for any help with this. After some quick searching, I'm thinking there's no such thing as free customizable DNS service... at least none that doesn't append some stupid "our.service.stupid.com" to the domain name! :P

---

### Post by aashay on 2008-03-19
I dont think that would be possible without actually buying a domain name. You could try [www.dot.tk](www.dot.tk)  to get a [www.site.tk](www.site.tk) address. I havent personally tried it myself though

---

### Post by jeffus_il on 2008-03-19
There are servers which provide the conversion of domain names into ip addresses, I guess it costs money, also there is the registration process which enables you to own a domain, also costing money... The service can be very reasonable, less than 10 dollars a year. The domain registrars also provide management tools  which help you do all sorts of neat tricks, like subdomains, domain forwarding, aliases and many others. Have a look at godaddy.com and see how much it would cost you to purchase the domain you want, it can also be cheaper if you pay for a ten year period rather than one year. What you can get is free is domain parking, I use Google which is free and very good. Other than GMail at my own domain, you get a multi-user setup, with shared calendars and document editing and handling.

---

### Post by x86scorpion on 2008-03-19
better check [DynDNS]("http://www.dyndns.com/services/dns/dyndns/")
it allows you to create a hostname that points to your dynamic IP or static IP address or URL.
you can get five (5) hostnames in 88 available domains for free. [Standard Dynamic DNS Domains]("http://www.dyndns.com/services/dns/dyndns/domains.html")

then download their [DynDNS Update Clients]("http://www.dyndns.com/support/clients/") to continually map your hostname to your IP address (even if it changes).

available for these OSes

    *  Windows update client
    * Mac/OS X client
    * Linux/Unix update clients

I never used ddclient 3.7.3 yet (Linux update client). If you've configured it how please share it here. :)

Recently tried DynDNS Updater (3.1.0.15) Windows (Stable) when I was experimenting these tools within windows. And it simply works.

you can also try:
[no-ip]("http://www.no-ip.com/")
[zoneedit]("http://www.zoneedit.com/")


.

---

### Post by Dr Small on 2008-03-19
Ok, so here is my curious question:
What if your neighbor (outside your LAN) added your DNS IP to his DNS list. Would he then be able to pass his requests though your DNS server and point to the domains?

If not, why not? It sounds practical, but I guess maybe I am confused?
Also, I have bind9 setup on my server, but it looked very complicated on setting up a domain. Any information on this?

Dr Small

---

### Post by jeffus_il on 2008-03-20
> **GenuineXP said:**
> 
I'd really like to use the exact domain names I've chosen (I've already tried browsing them online and they don't appear to be in use on the Internet). Is there such a free service?

Free DynDns won't let him use the exact name he wants ...

---

### Post by wormser on 2008-03-20
> **jeffus_il said:**
> Free DynDns won't let him use the exact name he wants ...

True, but, he could purchase the domain name and point it to the "our.service.stupid.com" address with domain masking.  Then you can go to yourdomain.com and get to the site.

---

### Post by volkswagner on 2008-03-20
I called godaddy.com.  I asked if they had forwarding.  They said it was free with the purchase of a domain registration (10/yr. or less for multiple year registration).  This may be your least expensive solution if you have a static ip.  I forgot to ask if the forwarding can be done to a specific ip.  When I started the registration I only saw the option to use specific name servers.

This is something to look into since you will need to purchase a domain name.  Just running the address in your browser is not always accurate.  You need to check with a registrar such as godaddy or register.com to see if it is available.

---

### Post by smileypaul on 2008-03-20
Hmm..

i may be wrong. But if he uses a forwarder, he will probably have problems with FTP.

If a client connects to "mydomain.com" , which is some forwarding company.. that then forwards it to his IP address.. when the server tries to put the client in PASV mode, he may have issues? 

Thats the sort of issue im having with a forwarder, but it seems to only affect some client.. and for some reason, it never affects FileZilla.


If you have a static ip, why not just throw your domain into ZoneEdit? I believe the first 5 domains are free


someone correct me if im wrong

---

### Post by wormser on 2008-03-20
> **volkswagner said:**
> I called godaddy.com.  I asked if they had forwarding.  They said it was free with the purchase of a domain registration (10/yr. or less for multiple year registration).  This may be your least expensive solution if you have a static ip.  I forgot to ask if the forwarding can be done to a specific ip.  When I started the registration I only saw the option to use specific name servers.

This is something to look into since you will need to purchase a domain name.  Just running the address in your browser is not always accurate.  You need to check with a registrar such as godaddy or register.com to see if it is available.

You would have to use Go Daddy's name servers then forward and mask.

---

### Post by GenuineXP on 2008-03-20
Thanks for all the help everyone.

I've been looking into Go Daddy (which reports the domain name I want is indeed available). However, I'm a bit confused about their service and after reading a few articles including one at Wikipedia I'm not too sure about their practices. :P

Anyway, I thought about the same forwarding issue mentioned about. I don't know what masking is; does anyone care to explain it to me. :P In the meantime, I've heard that it's free to park a domain just to reserve it so that it isn't taken by anyone else. How can this be done? Does Go Daddy provide free domain parking?

Also, I read somewhere that Google also provides domain services, but I couldn't seem to find a Google page for it (even using their search engine, lol).

Thanks again! I appreciate all the great help.

---

### Post by Tavorisch on 2008-03-20
aitdomain.com is like 7$ a year for a nameserver, just go into nameservers and add ns1.yourdomain.com bind9 is pretty easy just follow some guides for local bind9 but put in your outside IP for whatever they have local, also setup your /etc/resolv.conf to hit  nameserver (outsideip)
nameserver (loopback) for apache2 to work off it.
Also whatever htey have example.com put your domain .com and wherever they have ns0.example.com put in your nameserver...
make sure your local network settings to static, in /etc/network/interfaces

also don't forget to portforward 80, and 53...

---

### Post by GenuineXP on 2008-03-20
Hm, I've been checking out AITDomains and I'm a bit worried that it may not work for my rotating IP address. My server gets access through my DSL modem and Internet service from Verizon. My outside IP tends to change. (The server's internal IP, however, is static.)

I'm also confused about how they require the entry of the DNS servers you wish to use. I imagine I would give them the name/address of my DNS, but as I said above it's behind a DSL modem with a changing IP and I'm not sure this'll work.

...I think I'm getting some of these things a bit confused. I guess ultimately my question is does AITDomains provide everything I'll need to get my server on the net even when the IP is dynamic? If not, which service provides this? (I think Go Daddy said something on their page about dynamic DNS and dynamic IPs).

Thanks!

---

### Post by smileypaul on 2008-03-20
Ahh.. didnt realize you were on a dynamic IP .

check out dyndns.org .. and use ddclient to update them.

Its free, works great. But sometimes isn't ideal for FTP.

---

### Post by GenuineXP on 2008-03-20
I've signed up with DynDNS which is great since I can get a free hostname (not the one I wanted, but it'll do for now, especially since it's free).

The problem now is that ddclient updates the IP on DynDNS to the local LAN address! How can I fix this? I was confused by the configuration question about which interface to use, so I entered eth0 (my network interface), since that's all I could think of. Was that the right thing to do?

DynDNS detects the correct IP, but ddclient changes it. The hostname still works from my laptop, but I'm connected to my home network, so I'm sure once I disconnect from this LAN I won't get my server.

---

### Post by jeffus_il on 2008-03-21
What router do you have? I have two at home which both support ddns, so I just set them up for ddns, no need for software!

---

### Post by vpsville on 2008-03-21
EVERYDNS.NET  and AFRAID.ORG  both provide free DNS services.  

They are both excellent as well, some of our domains have used them for years.

I suggest you use both so if one goes down your sites will be unaffected.

---

### Post by GenuineXP on 2008-03-21
Thanks for all the help everyone. I ended up purchasing the domain I wanted with Go Daddy since it wasn't even $10.00. However, I declined their other services and am using EveryDNS per your suggestions and like it very much.

However, I'm having trouble witht he EveryDNS update client. It runs properly, but I'm not sure how to automate it to run at a particular interval as soon as the system boots. Is there an easy way to do this? The client is actually just a Perl script.

Would it be possible to use ddclient? It doesn't seem to have a the right protocol, but I'd prefer to use it since it can run as a daemon.

---

### Post by GenuineXP on 2008-03-21
Nevermind, I think I've got things working use cron. :-)

---

### Post by teqsun on 2008-03-21
Personally I use no-ip.com  I can update the DYNDNS with my router so it is always current.

You get 5 free dynamic dns.

---

