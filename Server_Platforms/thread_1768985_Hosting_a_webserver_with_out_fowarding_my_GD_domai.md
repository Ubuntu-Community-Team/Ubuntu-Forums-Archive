---
title: "Hosting a webserver with out fowarding my GD domain"
date: 2011-05-27
forum: Server Platforms
---

### Post by pcarlos853 on 2011-05-27
Hi All!,

I have set up a small website running from my ubuntu 10.10 server. In the past I have bought a domain from godaddy and have set it to forward to my no-ip address which points to my server. But I dont think that this looks good. For ex visitors can't copy and send the url to a page on my site because they will get the masked url which points to my home page. Thanks for putting up with my rambling, but here is my question. Can I make it so that my Godaddy domain points directly to my Apache webserver with out domain fowarding or masking?

Thanks
Carlos

---

### Post by volkswagner on 2011-05-27
You have two options.

1. Manually enter your public ip address in Godaddy's domain control panel DNS settings.  Point your A record to your public ip.  You would need to update this when your ip changes.

You can subscribe to a dynamic dns service such as DynDNS.  With this option you use their DNS servers, and the script to update the records automatically.  The script can run on your server or some routers have Dynamic Dns providers listed to handle at the router level.

I used the DynDNS service.  This is a pay service when you use your own domain.  It can get more expensive if you add many domains names as I did.  This made getting a VPS for ~$10/mo. more of a no brainer.

---

### Post by pcarlos853 on 2011-05-28
Thanks that did it! For some reason I though it was a lot more complicated that it really is. Its really simple!

Thanks Again!

---

### Post by baligena on 2011-06-03
I cant seem to connect my server to the internet I can only access from my network.  Can you help?

---

### Post by volkswagner on 2011-06-04
You should start a new thread, since this one is marked solved you would likely get better exposure with a new one.

Go to canyouseeme.org from inside your LAN and check if port 80 is open.  If it is not open you need open it within your router settings, or contact your isp to see if they block port 80.

---

