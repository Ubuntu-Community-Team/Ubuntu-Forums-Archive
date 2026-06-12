---
title: "monitor network/internet usage"
date: 2009-10-08
forum: Server Platforms
---

### Post by Linux&amp;Gsus on 2009-10-08
Hi guys.
On my server I would like to monitor which computer is causing how much internet and network traffic. Well, network traffic would be secondary, most important is internet usage. A web interface for this would be nice.
Is there any server based app for this available? Preferably fool-proof to set up??

We are on a bandwidth limited internet plan (is normal here...) and I don't like the idea to get over the bandwidth quota.
Also, is it possible to set different limits for every computer that it is able to download and then slow down the internet connection for this machine? Just e.g. to limit friends who plug in to the network or in case someone should crack the wireless and wants to use it for free download?


Thanks for an y help.
L&G

---

### Post by Lars Noodén on 2009-10-08
Cacti is fairly easy to use:
[http://www.cacti.net/](http://www.cacti.net/)

Usual caveats about PHP apply.

---

### Post by Lars Noodén on 2009-10-08
One of the first things to look at to reduce bandwidth waste would be squid.  
 [http://www.squid-cache.org/](http://www.squid-cache.org/)

It's easy to install and one or two changes to the configuration will have you up and running.

---

### Post by Lars Noodén on 2009-10-08
> **Linux&Gsus said:**
> 
Also, is it possible to set different limits for every computer that it is able to download and then slow down the internet connection for this machine?

IPTables appears to support quotas now, so if your traffic to the outside goes through your linux machine you can enable quotas per IP address (which may or may not translate to specific machines).  

Use of quotas with IPTables seems kind of sparesly documented.  You may have to try a lot of experimenting on local connections first.

If we may ask, what is the topology of your network like?

---

### Post by Linux&amp;Gsus on 2009-10-09
Thanks for the reply. I'll look into that.

The network I have is:
1) Linux server (Debian 4) - mainly for DNS, emails, files - runs 24/7
2) Linux server (Ubuntu server 9.04) - this is for testing, probably will re-install when 9.10 is out, runs only when I wanna test stuff. If needed could be turned into another "production" server
3) Windows XP Laptop
4) Linux Laptop

5-n) Friends who plug in to the network cause need help, etc etc etc. Some plug in regularly, mainly Windows, very few Macs/Linux.

There is a network printer but that one doesn't need to be monitored, of course. Is only turned on when needed, anyways.


So, this is my network. If you need more info just ask.


Got a question about the Squid Proxy Server.
I was under the impression that you actually need to add the Proxy Server to your computer and then the computer will route every internet traffic through that. Now, since we have Laptops (not as Desktop replacements but to really using them outside home a lot) I thought it would cause trouble if the Proxy Server isn't accessible.
Or is there another way to say that all network traffic has to go through that Proxy, no matter the settings on my computer?

I guess now you know how much I know about it... ;)


Anyways, any more comments, help, suggestions, questions, etc. are welcome.
Cheers,
L&G

---

### Post by Lars Noodén on 2009-10-09
> **Linux&Gsus said:**
> 
So, this is my network. If you need more info just ask.

What I was wondering is if your traffic goes through one of your linux boxes.  Does one of them have two network interfaces and act as your router, switch or adsl modem?

That would be the place to have squid (while you are at home) and to run IPTables.

---

### Post by Lars Noodén on 2009-10-09
> **Linux&Gsus said:**
> 
Got a question about the Squid Proxy Server.
I was under the impression that you actually need to add the Proxy Server to your computer and then the computer will route every internet traffic through that. Now, since we have Laptops...

Yep.  That's one of the places to use Squid.  When you are out and about with the laptop, you'll probably be using wifi and that's slow.  So squid can help there, too.  

Put squid on the laptop, set it so it only accepts connections from the local host.  Run web traffic through it. 

After some usage, you'll want to check how the cache is used and adjust settings like size.

---

### Post by dragos2 on 2009-10-09
> **Lars Noodén said:**
> IPTables appears to support quotas now, so if your traffic to the outside goes through your linux machine you can enable quotas per IP address (which may or may not translate to specific machines).  


Can I see an example of iptables quota ?

---

### Post by Lars Noodén on 2009-10-09
> **dragos2 said:**
> Can I see an example of iptables quota ?

It's a quick, not a good example:

```
iptables -A INPUT -s 0/0 -d 0/0 -m quota --quota 30000000 -j ACCEPT

```

I'm unable to find some fresh data on it or even on packet filtering in the linux kernel.

---

### Post by Linux&amp;Gsus on 2009-10-10
> **Lars Noodén said:**
> What I was wondering is if your traffic goes through one of your linux boxes.  Does one of them have two network interfaces and act as your router, switch or adsl modem?

That would be the place to have squid (while you are at home) and to run IPTables.

Sorry, forgot about that part.
I have a (cheap) NetComm Router/Modem/Switch + a Wifi AP. No one Box through which all the traffic routes.

Cheers,
L&G

---

### Post by Linux&amp;Gsus on 2009-10-10
> **Lars Noodén said:**
> Yep.  That's one of the places to use Squid.  When you are out and about with the laptop, you'll probably be using wifi and that's slow.  So squid can help there, too.  

Put squid on the laptop, set it so it only accepts connections from the local host.  Run web traffic through it. 

After some usage, you'll want to check how the cache is used and adjust settings like size.

I personally don't use Wifi at all, always plug in via cable. More a habit really than for any other reason. Must say though that I usually don't sit in Internet Cafes or things like that.

Cheers,
L&G

---

### Post by Lars Noodén on 2009-10-11
> **Linux&Gsus said:**
> Sorry, forgot about that part.
I have a (cheap) NetComm Router/Modem/Switch + a Wifi AP. No one Box through which all the traffic routes.

Cheers,
L&G

Ok.  Then Squid would have to be on one of the other machines on your home network, but for it to be of use that machine has to be turn on.  I'm unfamiliar with the details of the NetComm router.  Can it be set to forward a port to your LAN's proxy?

---

