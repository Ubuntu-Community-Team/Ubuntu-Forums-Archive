---
title: "Forward traffic from a domain to another server behind a firewall"
date: 2010-01-29
forum: Server Platforms
---

### Post by wheniwork on 2010-01-29
I have a server on my router on the DMZ. All outside traffic goes to it. 

This server has Apache running and the domain mysite.com resolves to the the DMZ web server. 

I have a second server on the LAN that also has apache running. I want to set up another domain, myothersite.com to resolve to the second server on the LAN.

Since the main server is on DMZ I have the DNS A records for myothersite.com pointing to the public IP that the DMZ is on. 

How do I get myothersite.com to resolve to the second webserver on the LAN? What configuration do I need to do on my DMZ server so it routes traffic for myothersite.com to the other server on teh LAN?

Do I use BIND DNS? If so please advise on how to set that up. BIND DNS seems confusing and I having trouble knowing how to configuring it.

Is there another option besides BIND? 

Thanks for the help!

---

### Post by rituraj_tiwari on 2010-01-29
You should look at Apache's reverse proxy ability. You can configure Apache running mysite.com to (reverse) proxy traffic for myothersite.com over your LAN.

[http://httpd.apache.org/docs/1.3/mod/mod_proxy.html]("http://httpd.apache.org/docs/1.3/mod/mod_proxy.html")

---

### Post by wheniwork on 2010-01-29
That looks promising, but I am at a bit of a loss as to how I go about implementing the right configuration. Any ideas?

---

