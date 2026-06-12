---
title: "From GoDaddy Domain to Ubuntu Server. How???"
date: 2008-08-16
forum: Server Platforms
---

### Post by benbowler on 2008-08-16
**_My Problem is as follows:_**

I have a working instillation of Ubuntu 6.06 Server along with a configured router with port forwarding set up and working fine with a dyndns.com address.

I've also recently bought several domains from GoDaddy (Although I hope the solution should apply to all registrars).

**_What I want to do:_**

I want to be able to enter name servers (Such as 'exampleNS1.dyndns.com') into the registrars control panel and have them point to my server (I understand virtual hosts and all that).

**_What I've tried:_**

Setting up a DNS server using BIND and [this helpful tutorial]("http://ubuntuforums.org/showthread.php?t=236093&highlight=bind+godaddy") but I don't 100% get how this helps to make the domain globally recognisable and I haven't managed it.

**Please help!**

---

### Post by windependence on 2008-08-16
You don't need a DNS server. Log on to your GoDaddy control panel and go to My Domains. Click on the Domain you want to configure and it will bring up all your settings. If you are using their nameservers you would click on nameservers and you will see something like this:

Name Servers: (Last Update 10/16/2007)
NS17.DOMAINCONTROL.COM
NS18.DOMAINCONTROL.COM

They should be prefilled but if not they tell you what to use. If you need to use your dynamic DNS nameservers, find out what they are from your dyndns provider and use those and then just save the config. You can call their support people, they are very good at walking you through all this. they can even help you set up the dynamic DNS.

-Tim

---

### Post by benbowler on 2008-08-16
This is a good solution however DynDNS who I'm with at the moment charge nearly $30 per year for what seems like adding a bind zone to their configuration.

Is there a company who offer this service for free?

Could I use a couple of dyndns addresses which are free as name servers if I configured BIND correctly. How would this propagate?

Has anyone got this system working?

---

### Post by benbowler on 2008-08-16
**_Success!_**

I've found a service called [FreeDNS]("http://freedns.afraid.org/") there a whole list of similar services on [The Free Country]("http://www.thefreecountry.com/webmaster/freedns.shtml").

This service allows you to use the name servers ns1.afraid.org etc. and then manage your domains like DynDNS. I think the limit is 50 but that should be fine for most people and you can upgrade for $5 per month if you really need that amount.

Thanks for the help.

---

### Post by windependence on 2008-08-16
no-ip is really good. You shouldn't have to do any fancy stuff to do this at all. GoDaddy might even have a way, I don't know, I pay $5 a month for a static IP to avoid all this crap. You should call them (it's free) and ask. they may have some suggestions.

-Tim

---

### Post by gishaust on 2008-08-16
I use ddclient with a dynamic ip that then points to zone edit and then zoneedit gets the domain from godaddy I don't have dns on my server and all did was open 80 on my router. I have never had any trouble and zoneedit is free for the first 200mg of transfer.

---

### Post by windependence on 2008-08-17
> **gishaust said:**
> I use ddclient with a dynamic ip that then points to zone edit and then zoneedit gets the domain from godaddy I don't have dns on my server and all did was open 80 on my router. I have never had any trouble and zoneedit is free for the first 200mg of transfer.

That sounds like a good way to do it if you have to go with dynamic dns.

-Tim

---

### Post by mbeach on 2008-08-17
for business use I've always gone with static ip, however for a couple of personal sites I've used the following:

register a dynamic hostname with dyndns (free)
buy a hostname from registrar (I've been using Netfirms for cheap .ca names)
create a "cname" record pointing [www.registrereddomain.ca](www.registrereddomain.ca) to mydomain.dyndns.com
create the appropriate Servername [www.registrereddomain.ca](www.registrereddomain.ca) line in virtual host file, or if this is the only site, no need to.

instructions for cnames at godaddy (tailored for google apps, adjust accordingly):
[http://www.google.com/support/a/bin/answer.py?hl=en&answer=47610](http://www.google.com/support/a/bin/answer.py?hl=en&answer=47610)
just substitute ghs.google.com for your dyndns hostname.

This is all just so [www.mydomain.com](www.mydomain.com) will point to mydnsdomain.com which gets directed to my server with [www.mydomain.com](www.mydomain.com) showing in the browser.  If you are wanting to do something else with your own nameserver, then feel free to disregard this post.

---

### Post by windependence on 2008-08-17
And, I'll add that with a setup like mbeach suggested, at least with no-ip, you can even point their DNS at a specific port on your site so if you want to host on say 8080 because your IPS blocks 80, you can do it without ugly URLs. I'm not sure about the other dynamic DNS providers.


-Tim

---

