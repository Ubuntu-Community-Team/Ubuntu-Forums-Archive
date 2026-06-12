---
title: "Questions about hosting multiple websites!"
date: 2011-02-20
forum: Server Platforms
---

### Post by Sir Jake on 2011-02-20
Hello there, I'm looking to redo one of my boxes making it into a webserver.
I've been using a shared hosting account for sometime then played around with one of my boxes but it's time to run the full deal myself.

Question is I'd like to hear what you guys think is the best way or guide to setup a my server for hosting multiple websites.

I'd like to run apache2, mysql, some type of mail server as well.

Looking around on google I've found a few things here and there that I've screwed around with on a old install.   Main thing is I want to do everything fresh and have it setup nice like.

Also if there's any open source panels that might help make life easy that you know of let me know.

Thanks for your help and time in advance, 
Jake.

---

### Post by volkswagner on 2011-02-20
Do you have a static ip address from your isp?  Does your isp block important ports such as 80, 25, etc.?

In my opinion it is not worth hosting multiple domains from a dynamic ip.  You can get an inexpensive VPS in a data center with failover isp, power backup and you won't have to pay for the electric consumption.

If you still want to host from home, there is ispconfig, and webmin for control panel type control.

A really easy mail setup is Citadel.

I would stick with Ubuntu 10.04 for the long term support.

Howtoforge has some nice how-to's such as [this one for 10.10]("http://www.howtoforge.com/virtual-hosting-with-pureftpd-and-mysql-incl-quota-and-bandwidth-management-on-ubuntu-10.10-maverick-meerkat"), but it should work fine using 10.04.

---

### Post by Sir Jake on 2011-02-20
Thanks, yes the box has multiple static ip's guess I should have said it was in a data center.

I've played around a little bit with ispconfig on my test box it seems to be pretty well made.

---

### Post by TheNomad on 2011-04-01
> **Sir Jake said:**
> Thanks, yes the box has multiple static ip's guess I should have said it was in a data center.

I've played around a little bit with ispconfig on my test box it seems to be pretty well made.

I am on the same boat but my VPS is at Ubuntu 9.x not 10 yet. VPS provider does not give v.10 as one of the options.

I am looking for a step-by-step document, explaining how to set up a web server, to host multiple, very low overhead (totally static flash animation with basic HTML) and very low traffic (about 50-100 hits per day tops) websites. One requirement, each domain will have its mail server and need to serve about 20-25 addresses. any web management interface is unnecessary as I will only allow ftp access to upload files.

Does anyone know such document (most probably called "shared hosting setup for dummies") anywhere on the web ?

Thanks

---

