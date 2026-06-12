---
title: "pointing subdomain to page?"
date: 2009-01-16
forum: Server Platforms
---

### Post by belfasttim on 2009-01-16
HI all-- I would like to configure apache2 to point a subdomain (subdomain.domain.com) to a page, rather than a directory. SO if you typed in [http://subdomain.domain.com](http://subdomain.domain.com) you would end up at [www.domain.com/mypage.htm](www.domain.com/mypage.htm) (or whatever).

Do I need to make changes to BIND and to Apache, or can this be just an Apache virtual host?

Thanks for any help-- the more explicit the better!

---

### Post by baudday on 2009-01-16
Just point it to a directory with an index.php page that forwards to [www.domain.com/mypage.htm](www.domain.com/mypage.htm)

---

### Post by volkswagner on 2009-01-17
As baudday suggested, put a redirect to the address you want to show.

This page helped me set up [redirects]("http://www.webconfs.com/how-to-redirect-a-webpage.php") on all types of servers.  Very useful.

You will probably want to choose the htaccess redirect method.

---

### Post by belfasttim on 2009-01-19
Thanks guys-- I see your point-- 
So is it true that you don't need to set each subdomain explicitly in DNS? WIll the subdomain request go to the "main" domain by default, where it can be handled by htaccess?

Thanks again

---

### Post by volkswagner on 2009-01-20
> **belfasttim said:**
> Thanks guys-- I see your point-- 
So is it true that you don't need to set each subdomain explicitly in DNS? WIll the subdomain request go to the "main" domain by default, where it can be handled by htaccess?

Thanks again

No, the subdomain still needs to be listed in DNS.  I use DynDns service.  Whenever I add a subdomain, I add it to the list of hosts there first.  If you are running your own DNS, you will need to make the appropriate entry.

---

