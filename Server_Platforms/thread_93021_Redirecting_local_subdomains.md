---
title: "Redirecting local subdomains"
date: 2005-11-21
forum: Server Platforms
---

### Post by mfyahya on 2005-11-21
I'm developing a dynamic site which has most of it's urls in this form:
[http://somepage.mysite.com/](http://somepage.mysite.com/)  where somepage can be any of the dynamic pages. Don't ask me why it's set up like that, that's how the managers want it.

In order to work on this locally I setup a virtualhost mysite-local.com and edited /etc/hosts to point mysite-local.com to 127.0.0.1 
But I also want *.mysite-local.com to point to localhost so I can access the subdomains in the site scripts. How can I do that? Do I need to setup a dns server?  If so, can someone please show me how to set it up for this purpose in ubuntu.
Thanks in advance.

---

### Post by MarcDM on 2005-11-21
Not sure how to do that without a DNS Server. But if you want a quick DNS Server,

take the plunge and try DJBDNS. TinyDNS from that package should serve you well. 

Take a look at [http://cr.yp.to/djbdns.html]("http://cr.yp.to/djbdns.html")

I say take the plunge, cuz once you go djb you might never go bind.

---

