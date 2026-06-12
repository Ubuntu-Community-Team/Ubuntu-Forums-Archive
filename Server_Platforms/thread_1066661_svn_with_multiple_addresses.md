---
title: "svn with multiple addresses"
date: 2009-02-11
forum: Server Platforms
---

### Post by bartvh on 2009-02-11
I'm setting up SVN with Apache2. I'm going to host multiple repositories, and will put them all in one directory (/home/svn), for easy administration and use by software like WebSVN and/or Trac.

My idea was to create a VirtualHost in apache will will run on all addresses like "http://svn.anyofmydomains.tld". This is not hard.

However, I'd also like to be able to access a repository named "foo" at "http://thefoodomain.org/svn". Is this possible at all?

---

