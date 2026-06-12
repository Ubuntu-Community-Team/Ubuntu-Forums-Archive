---
title: "domain in ISPconfig"
date: 2006-12-25
forum: Server Platforms
---

### Post by holsv1 on 2006-12-25
Hi, I have buyed a doman from nordichosting, and om my server I am using ISPconfig on my server. Do someone know how to use a domain on the server?

---

### Post by MrHorus on 2006-12-27
> **holsv1 said:**
> Do someone know how to use a domain on the server?

Yes, you need to install BIND (apt-get install bind9) and then create a zonefile for your domain.

It;s *reasonably* straightforward although if it's your first time you will want to locate someone else's zonefile that you can use as a template and perhaps read a good DNS/BIND primer.

It also goes without saying that for your domain to be accessable then at least one of your nameservers (which your machine will be one of) should be accessable 24/7.

---

