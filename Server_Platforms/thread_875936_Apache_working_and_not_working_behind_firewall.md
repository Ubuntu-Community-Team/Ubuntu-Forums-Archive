---
title: "Apache working and not working behind firewall"
date: 2008-07-31
forum: Server Platforms
---

### Post by remii68 on 2008-07-31
Okay, Ubuntu Hardy (desktop) with Apache2 (LAMP) 

I can access apache from my internal network, could do this from day one.

Tried to access from Internet and ran into two problems, first was the bind = localserver.  I changed this to the internal network IP address 198.162.x.x.  Then I realized that Verizon blocked port 80.  So I signed up for no-ip.com for port 80 redirect and set my firewall to redirect that high port to port 80 of my LAMP server.

Okay here is the wierd thing.

I have a blackberry handheld and when I use the Internet browser going through the no-ip.com address, I can see my web pages.

When I use my laptop (dual boot Vista and Ubuntu) I cannot see my web pages.  Firefox says it cannot establish a connection to 175.x.x.x:yyyy.  IE jumps to putting the website into a google search box (behavior that says it cannot find that site).

This is driving me crazy.  

1.  Seeing it locally tells me it is up and running
2.  Seeing it over my blackberry internet browser says that my firewall is set up correctly as is apache for more than localserver.
3.  Why can't I see it over my laptop.

I have tested this both from an external location and from inside my house (not sure how that resolves when I go to no-ip.com and back to my  WAN address).

Any advice would be great,
-remii68

---

### Post by MJN on 2008-07-31
If you give us the URL we can help, if not we're pretty much left guessing.
 
Mathew

---

### Post by remii68 on 2008-07-31
[http://hospice.zapto.org](http://hospice.zapto.org)

---

### Post by MJN on 2008-07-31
It works from here (no, really it does! ;))...

Is the laptop the only client that cannot see it? If so I'd suspect that. If not, what else can't?

Mathew

---

### Post by remii68 on 2008-07-31
Thanks.  I cannot get to it from either of my laptops from my internal network when I use the no-ip.com address.  Both laptops can see it from the internal network when using the internal ip address.

I had tried it from an external public network at the nearby hospital that I was at over the weekend and could not get the page to display.  It is possible that the hospital blocked high ports which was the only thing that I could think of.

Well, that makes me feel a lot better.  I am going on a trip and wanted to be able to get to the site from outside of the house.

Thanks,
-remii68

---

### Post by MJN on 2008-07-31
> **remii68 said:**
> Thanks.  I cannot get to it from either of my laptops from my internal network when I use the no-ip.com address.  Both laptops can see it from the internal network when using the internal ip address.Can *any* internal machine see it using the no-ip.com address? If not, it is likely that your router doesn't support 'NAT loopback' and hence they must access the server using either the internal server IP address or you could put an entry for hospice.zapto.org in your clients' HOSTS files.

> I had tried it from an external public network at the nearby hospital that I was at over the weekend and could not get the page to display.  It is possible that the hospital blocked high ports which was the only thing that I could think of.Maybe... You could try a more standard port which may not have been blocked by your ISP (give 8080 at try).

Mathew

---

### Post by remii68 on 2008-07-31
Thanks.  I had a suspected that it was the router for my internal side of the house.  I will be testing the external side on my trip at another ISP.  Since the one person got through and my blackberry got through too, I will assume that the external place that I was testing it at was blocking the port I was using to use as my httpd address.

Thanks,
-remii68

---

