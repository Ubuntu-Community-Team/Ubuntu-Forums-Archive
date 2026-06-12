---
title: "Home domain"
date: 2012-03-12
forum: Server Platforms
---

### Post by halversondm on 2012-03-12
So I setup a home server using Ubuntu Server 11.10.  I want to host my own website at home and other stuff.

I setup the server with DNS, apache and tomcat.  Through all the doc on DNS, I have a successful DNS working to host my domain.  I set my DNS to forward to the OpenDNS servers as well.  So I've got a caching DNS and a primary master.  I did not setup a secondary master since I only have one server.  To test all of this out.  I set my laptop to have a primary DNS of my internal server and no secondary DNS via a static setup.  Again, I could get to my site.  Ping my address, etc; no issues.

So then I went to my router and updated the primary DNS to my internal DNS and the left the secondary DNS to an OpenDNS server.  Now I reset my laptop to use DHCP and get the primary DNS off the router (which oddly is 192.168.1.1 and no secondary).  When I go to my browser, clear the cache, and enter my website address, I go outside my network to some site that wants me to buy that domain.  

I tried to remove the secondary DNS from my router and BOOM, website is accessible again.  Anyone know why this is?  

I would have thought that the routers primary and secondary DNS entries are for the purposes of failover.  However, it seems as if that's not the case.

I could set the router to have just my DNS server, but I want the option to shut that box off and just use the secondary DNS to serve my needs.

---

### Post by papibe on 2012-03-12
Hi halversondm.

Interesting situation.

My first question would be what brand and model is your router? Since there's no standard rules on how routers handle those situations, it would be relevant to kown.

Is 192.168.1.1 your router or the address of your internal DNS?

I have a test for you. What happens when you set your laptop to use just OpenDNS directly, and then you try get to your website? Do you get the same site that offers you to buy the domain?

Regards.

---

### Post by halversondm on 2012-03-13
pabibe,
 
Router model is Netgear N600.  Router IP address is 192.168.1.1 and the internal DNS is 192.168.1.101 (static IP, outside of the DHCP range).

I'll try the test later tonight.

Thanks

halversondm

---

### Post by halversondm on 2012-03-13
Also the address of my website is:
 
[http://www.halverson.net/](http://www.halverson.net/)
 
Which will bring you to hover something or other. I'm at work now and this is the same site I get while I'm at home even though the router has my internal DNS as the primary.

---

