---
title: "2 Domains sent to IP address, need to route one to server."
date: 2015-08-13
forum: Server Platforms
---

### Post by Harley_Frank on 2015-08-13
I have a UBUNTU SERVER 14.04 Server running and want to link one of my domains to it. I have one domain sent to my home IP address so I can access my network. But I want to host my portfolio on my server at home under a new domain name. It is going to run my website and mail as well. I wanted to know if there was a way to fully link a domain to a server so that there are no complications.

---

### Post by Habitual on 2015-08-13
Sure. point the "A Record" of the new domain at the home IP.

---

### Post by volkswagner on 2015-08-13
To host multiple websites/domains from the same ip address, you'll want to use Apache2 virtual hosts. 

Use the links at the top of this forum for documentation. Apache2 link [here]("https://help.ubuntu.com/14.04/serverguide/httpd.html").

The mail server is another story. If your home has a dynamic ip address your mail will likely be blocked by many mail servers such as gmail, aol, yahoo, etc.

I suggest getting a virtual private server from somewhere like Linode or DigitalOcean.

---

