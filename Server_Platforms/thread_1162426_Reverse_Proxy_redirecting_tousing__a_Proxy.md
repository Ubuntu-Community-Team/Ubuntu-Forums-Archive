---
title: "Reverse Proxy redirecting to/using  a Proxy"
date: 2009-05-17
forum: Server Platforms
---

### Post by eldoctor on 2009-05-17
Hi everyone, I want to ask something I am not sure of how to accomplish.

There is a internet site that the intranet users (employees) want to access, and the idea is to configure a reverse proxy that sends the requests to the company proxy so that bandwith between workstations and the reverse proxy can be limited. So when someone from the intranet types: [http://reverseproxy:port/index.html](http://reverseproxy:port/index.html) (lets asumme reverseproxy is an alias for the server where the Apache is) the reverse proxy should send the request through the company proxy.
Is there a way to accomplish this, I mean is like I should be able to configure Apache to use the company proxy when it redirects the request, is that possible someway??

Thanks in advance!!!

---

