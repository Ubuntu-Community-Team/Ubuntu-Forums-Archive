---
title: "apache mod_rewite rule help"
date: 2009-06-08
forum: Server Platforms
---

### Post by xkaliburx on 2009-06-08
There are alot of examples, etc. but having a problem getting this to work.  We have a login page (box) that can appear on any page by clicking the login button opening a simple login page.  For PCI req's, that must be behind an https page, so I wish to simply look on the URL, if it sees the login request, to redirect, but still keep the page there on, so if there were at [www.mydomain.com/page1.cfm](www.mydomain.com/page1.cfm) redirect them to [https://www.mydomain.com/page1.cfm?showLogin=true](https://www.mydomain.com/page1.cfm?showLogin=true)

I have the following rule;

RewriteRule showLogin=true https://%{DOCUMENT_ROOT}%?showLogin=true

Now I don't see any errors, but not sure if they would spit out, but when I goto [www.mydomain.com](www.mydomain.com), hit any page, then hit the login, I simply stay on that page; [http://www.mydomain.com/xyz.cfm?showLogin=true](http://www.mydomain.com/xyz.cfm?showLogin=true) (and the login box appears) but no redirect.

Thanks.

---

