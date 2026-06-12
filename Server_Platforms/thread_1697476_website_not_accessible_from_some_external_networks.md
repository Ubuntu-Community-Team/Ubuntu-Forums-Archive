---
title: "website not accessible from some external networks"
date: 2011-02-28
forum: Server Platforms
---

### Post by jay3712 on 2011-02-28
I have set up a simple one page website using ubuntu server at my house. The page is viewable from most small networks like home networks and cell networks, but for some reason the connection times out when I try to access it from my corporate network as well as most any other corporate network.

What other info can I post to help figure this out? I have tried searching but I haven't found a question that is the same as the problem that I am having. 

The site is jasonfeather.com.

Thanks,
Jason

---

### Post by artheus on 2011-03-01
You could start by posting the config file of your web server. And maby some info about what routers and other hardware you've got in your setup.

Cheers,
Artheus

---

### Post by mimor on 2011-03-01
If I traceroute to your website it won't go further than:
CHARTER-COM.edge3.washington1.level3.net

Perhaps some corporate proxy software might be hanging there for a bit too long to end with a time-out. :confused:

---

### Post by SeijiSensei on 2011-03-01
> **mimor said:**
> If I traceroute to your website it won't go further than: CHARTER-COM.edge3.washington1.level3.net

I actually got all the way to his machine with traceroute but there was a big delay between the upstream router and his machine.

nmap shows a number of "filtered" ports including port 80.  I'm guessing there are either firewall rules on the server, or on the router, that are blocking the connection.

I'm unable to telnet to port 80 on your machine; it just times out.

---

### Post by jay3712 on 2011-03-01
Thanks for the replies. Does any of this explain why I can access the page easily from my phone on verizon and my friends can access from personal computers but inside certain networks it times out (it appears to happen on company networks). 

Jason

---

### Post by mimor on 2011-03-01
From the public network, I can access it. 
But from within the enterprise network it times out.
Guess it has something to do with the firewalls and the routing, but not sure :(

---

### Post by pricetech on 2011-03-01
You might also be in a cluster of IPs that are blocked for some reason.

Times out from here also on comcrap.  I can try it from home using charter if you want me to.

---

### Post by jay3712 on 2011-03-01
> **pricetech said:**
> You might also be in a cluster of IPs that are blocked for some reason.

Times out from here also on comcrap.  I can try it from home using charter if you want me to.

Hey pricetech that would be good; i expect that you will get there ok from charter. 

Is there any way around this if my ip is in fact blocked? It is a dynamic ip and has changed several times, but the problem persists no matter what charter changes the ip to. I need to be able to send the link to anyone and have it show up reliably. If anybody has any ideas I would be glad to try them.

Thanks,
Jason

---

### Post by SeijiSensei on 2011-03-01
> **jay3712 said:**
> Hey pricetech that would be good; i expect that you will get there ok from charter.

I'm on Verizon FiOS (business).  I can't see it.

---

### Post by pricetech on 2011-03-03
It loads via charter.

---

### Post by jay3712 on 2011-03-04
From what I can gather via these responses and other people on different ISPs that I have talked to, the page loads on Charter but not on any other ISP. Anybody have an idea why that would be the case, or how I may be able to fix it?

Thanks for all your help!
Jason

---

### Post by mimor on 2011-03-05
Just FYI; It's accessible from Dommel ISP

---

### Post by windependence on 2011-03-05
This is because most corparate networks and even some ISPs block traffic that is redirected in certain ways. I have been saying this for years and yet there are some people who still don't believe it is happening. If you really want visibility, you really need to have your own static IP with DNS set up properly (this does NOT mean you need to run a DNS server). Dynamic IPs and redirects like DynDNS are blocked on many many corporate networks at their firewall. 
 
-Tim

---

### Post by jay3712 on 2011-03-05
Thanks for the info windependence and mimor. I am using zoneedit to track my dynamic ip, and it has worked perfectly for remote access to my network for a while.

Is the only solution to this going to be to pay for hosting? I like having it on the machine at my house, but I guess that would mean getting a static IP from Charter, which will cost more (and possibly require an upgrade to a business accout?).

Thanks,
Jason

---

### Post by windependence on 2011-03-05
> **jay3712 said:**
> Thanks for the info windependence and mimor. I am using zoneedit to track my dynamic ip, and it has worked perfectly for remote access to my network for a while.
 
Is the only solution to this going to be to pay for hosting? I like having it on the machine at my house, but I guess that would mean getting a static IP from Charter, which will cost more (and possibly require an upgrade to a business accout?).
 
Thanks,
Jason
You don't need to relinquish your hosting. I host all mu stuff at home and lease a block of 8 IPs from my ISP for $15 a month. Remember, your ISP probably isn't the only one available in your area. Check out SpeakEasy. they are reasonably priced and don't give you crap about running servers. 
 
-Tim

---

### Post by lisati on 2011-03-06
Not loading here, either by IP address or by host name.

By the way, SORBS reckons you're on a dynamic IP address. See [http://lisati.homelinux.com/dnsbl-check](http://lisati.homelinux.com/dnsbl-check) for more info......

---

