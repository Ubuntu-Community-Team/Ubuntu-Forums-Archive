---
title: "neen to serve one domain on two ip addresses"
date: 2010-01-18
forum: Server Platforms
---

### Post by nephish on 2010-01-18
Hey all,

We have  a  server that needs to be hi availablility. 
The problem is, sometimes our internet winks out for a few minutes.

We decided that we wanted to get two seperate lines to our server, and so they would be two different ip addresses. 

What out there would allow us to serve apache on [www.mywebsite.com](www.mywebsite.com) on more than one ip, and, if we can, how to do load ballancing?

thanks for any tips, this part is all new to me.

---

### Post by HermanAB on 2010-01-18
Howdy,

See the Advanced Routing Howto at [www.tldp.org](www.tldp.org).  You can do it by using two ethernet cards and two internet connections.  There is also a guide here [http://www.aeronetworks.ca/doublebarrel.html](http://www.aeronetworks.ca/doublebarrel.html)

However, you will likely be best served by simply buying a little dual port load balancing router from Dlink or Netgear for example.

---

### Post by nephish on 2010-01-18
> **HermanAB said:**
> 
However, you will likely be best served by simply buying a little dual port load balancing router from Dlink or Netgear for example.

thanks for the quick response and the links. 
If the load balancing router will do what we need, that will be better.

i have part of this that seems tricky to me though. 
in the dns server, we use ip xx.xx.xx.xx to route to [www.ourdomain.com](www.ourdomain.com). 
what do we do to have more than one ip address route to the same domain?
a certain web domain can be reached from more than one address ,right?

anyway, again, thanks for the help

---

### Post by gombadi on 2010-01-18
In dns you can set the same domain with more than one ip address - it is called round robin load balancing. Just add another entry for the domain and give it a new ip address.

On the down side I don't think it will solve your problem.

Lets say you have two ip addresses - 1.1.1.1 and 2.2.2.2 and have dns setup so that remote uses get both ip addresses returned and therefore choose one of them.

What happens when the link to 1.1.1.1 drops? Remote uses will be given the ip address still and will therefore try and make a connection to it but the link is down so it will fail.

All you will do is change from a "site is down" to a "site is randomly down" situation.

---

### Post by nephish on 2010-01-18
after looking at the hardware solutions suggested above, i think this is the way we are going to go. 
one solution we are entertaining is this one.

[http://www.peplink.com/index.php?view=faq&id=125&path=19](http://www.peplink.com/index.php?view=faq&id=125&path=19)

Not totally sure, but would this solve what you were talking about with the Round Robin ?

thanks

---

### Post by Vegan on 2010-01-18
> **nephish said:**
> Hey all,

We have  a  server that needs to be hi availablility. 
The problem is, sometimes our internet winks out for a few minutes.

We decided that we wanted to get two seperate lines to our server, and so they would be two different ip addresses. 

What out there would allow us to serve apache on [www.mywebsite.com](www.mywebsite.com) on more than one ip, and, if we can, how to do load ballancing?

thanks for any tips, this part is all new to me.

You are better off getting a faster network card and router. Far more efficient than using 2 old cards and trying to cope with load balancing unnecessarily.

If 1Gb Ethernet is no good, 10Gb Ethernet is now available for copper. 100Gb is on the drawing board.

---

### Post by nephish on 2010-01-18
Right, well we are not so concerned about bandwidth limits, but loss of connection altogether. We want to use 2 ISPs to serve one web domain.

thanks

---

### Post by gombadi on 2010-01-18
> 
Not totally sure, but would this solve what you were talking about with the Round Robin ?


It will reduce the problem but not eliminate it. It still relies on dns queries to direct incoming request to one or both of the links. DNS queries are cached upstream so if the initial connection goes to 1.1.1.1 and then that link fails then because of caching of the dns, even for minutes, new requests will try and go to 1.1.1.1.  This solution is better suited for load balancing while the situation you described in the original post (the link failing for a few minutes) is in need of a fail over solution.

Give the solution a go and see if it works - time will tell :-)

---

### Post by BkkBonanza on 2010-01-19
To solve the dns round robin problem you have to use monitoring to remove the ip that is down until it comes up again. There are dns services that can do this but they usually charge a fair bit.

If you're looking for high availability then start by doing the sensible thing and putting your site on a server in a data center. That doesn't need to cost much, certainly less then you'll spend on fancy routers and stuff. Data centers have multi-homed connections and much better reliability than your typical internet connection. Plus they have power redundancy.

---

