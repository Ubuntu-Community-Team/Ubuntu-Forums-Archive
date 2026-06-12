---
title: "Setting apache for web development only with a third level domain"
date: 2009-12-29
forum: Server Platforms
---

### Post by karimone on 2009-12-29
Hi folks!

I would like to use my server to host my works and let the customers preview the website before the publish.

I have a good isp contract and a dynamic IP that I configured with dyndns and a third-free-level domain. Now I can connect in http and see the default host configured with apache2 but how I can configure more website?

I can only use subdir and I cant' change the third level. How I can setup the vhost to point not the third level but only [COLOR="Red"]the dir[/COLOR]?  
```
[http://example.domain.com/](http://example.domain.com/)[COLOR="Red"]site[/COLOR] 

```
I hope my question is clear.

OS: Ubuntu Server 9.10
Computer: Apple Mac Mini 1.42 Ghz@PPC-G4

---

### Post by mhanson on 2009-12-30
Your question is not clear enough. Im not sure what you mean by third level domain.

Are you asking how to use Apache to host multiple domains on one ip address? Then that is easy. Just consult the web for virtual hosting on apache.

If you only need to host one site then just place your site directly in /var/www

Cheers

---

