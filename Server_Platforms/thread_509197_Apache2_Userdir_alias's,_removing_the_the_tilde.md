---
title: "Apache2: Userdir alias's, removing the the tilde"
date: 2007-07-25
forum: Server Platforms
---

### Post by piers on 2007-07-25
How can I set change [http://www.myserver.com/~billgates/](http://www.myserver.com/~billgates/) to;

[http://www.myserver.com/users/billgates/](http://www.myserver.com/users/billgates/) or
[http://billgates.myserver.com/](http://billgates.myserver.com/)

Whichevers easier ;)

Thanks

---

### Post by kidders on 2007-07-26
Hi there,

You might find this site useful: [http://httpd.apache.org/docs/](http://httpd.apache.org/docs/)

"http://www.myserver.com/~billgates/",  "http://www.myserver.com/users/billgates/" and "http://billgates.myserver.com/" are all completely different things. You should choose the one that meets your requirements.

---

### Post by jtc on 2007-07-26
mod_rewrite is your friend :-)

[http://httpd.apache.org/docs/2.0/misc/rewriteguide.html](http://httpd.apache.org/docs/2.0/misc/rewriteguide.html)

---

