---
title: "Ic-radius"
date: 2011-01-14
forum: Server Platforms
---

### Post by LiLoather on 2011-01-14
A search of this site didn't throw up a single reference to IC-RADIUS.

I know it's old and no longer maintained but it seems to have all I need, unlike FreeRADIUS which is packed with space and resource-consuming bells and whistles I don't need, and a nightmarish configuration.

Does anyone have an experience of running IC-RADIUS on an Ubuntu server?  Is it still obtainable?  Is there a source of documentation - the main website seems to be down?  IS there anyone out there with enough loyalty to IC-RADIUS to help me install and configure it?

---

### Post by HermanAB on 2011-01-15
Howdy,

I had an encounter with RADIUS some years ago. You would need to compile LC-RADIUS from source and figure it out yourself, since very, very few people use RADIUS.

If you need yet another guide on FreeRADIUS, here is mine:
[http://www.aeronetworks.ca/howtos/radius.html](http://www.aeronetworks.ca/howtos/radius.html)

Note that Redhat has a RADIUS wizard.  So, unless you are hell-bent on Ubuntu, I'd suggest using Redhat/CentOS instead.

---

### Post by LiLoather on 2011-01-16
Thanks for the link - looks a very good guide.

I did eventually get FreeRADIUS working, with MySQL - and with Dialup-admin providing a GUI for the former and HeidiSQL ditto for the latter, but I still can't give subscribers a way to check their own useage pulled from the SQL db.  Cistron claims to have a web-interface which allows for that, which would be very useful.

---

