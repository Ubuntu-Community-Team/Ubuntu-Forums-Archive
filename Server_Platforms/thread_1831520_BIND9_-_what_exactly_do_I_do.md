---
title: "BIND9 - what exactly do I do?"
date: 2011-08-23
forum: Server Platforms
---

### Post by m-one on 2011-08-23
Hey there, I've sucessfully set up everything I need on my Ubuntu 11.04 machine to handle being a web server.. All except BIND9. The only experience I've had with it is looking at it with a confused face.

I've followed guides and instructions, but very little of it makes any sense to me. So here are a few questions I have:

I have a domain that I want to use as the nameserver domain, such as ns1.domain-a.com and then from another registrar, use that ns and a backup ns for domain-b.com.
How do I set up Bind to allow this?

Also, I have absolutely no idea how Bind relates to Apache2, let's say that I want to point another domain to the server, I'll set up the site in Apache2, no problem.. but.. what does Bind need to do at this point?

It's all very confusing for me. :c

---

### Post by awi on 2011-08-23
Apache serves web requests. Bind9 will provide to the internet the name or names(virtual hosts) pointing to IP address to your web server.
An excelent start will be the ubuntu guide:

[https://help.ubuntu.com/10.04/serverguide/C/dns.html](https://help.ubuntu.com/10.04/serverguide/C/dns.html)

---

