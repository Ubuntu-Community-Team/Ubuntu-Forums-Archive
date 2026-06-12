---
title: "http:// works, www. doesnt"
date: 2009-10-29
forum: Server Platforms
---

### Post by virtuoosi on 2009-10-29
Hello,

I am running an webserver on my server computer. I am using a free dynamic DNS service provided by dy.fi. I can find my webserver at [http://mysubdomain.dy.fi](http://mysubdomain.dy.fi), but [www.mysubdomain.dy.fi](www.mysubdomain.dy.fi) doesn't work. 

Can someone point me into the right direction?

---

### Post by y@w on 2009-10-29
You want to make sure of two things:


1) www. is an CNAME to non-www. or an A record with the same IP.
2) www. is an alias to the main virtual host inside Apache if you are using virtual hosts.

---

