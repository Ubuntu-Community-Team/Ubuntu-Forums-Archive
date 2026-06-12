---
title: "Concrete5 and Ubuntu 10"
date: 2011-12-28
forum: Server Platforms
---

### Post by rodeoboy on 2011-12-28
I am new to both Ubuntu and Concrete5 content manager.  I setup an Ubuntu 10 server with Apache and PHP along with Concrete5 for our website consultant whom has built us a new website under /var/www/concrete5.4.0.5

I have tried to move the site to the /var/www directory so we can access it without adding the additional directory to the domain name.  However after moving all the files to the /var/www directory I get web page not found.

Any ideas how to correct this issue?  My guess is that its a permissions issue.

Thanks in advance,
Rodeoboy

---

### Post by rodeoboy on 2011-12-29
> **rodeoboy said:**
> I am new to both Ubuntu and Concrete5 content manager.  I setup an Ubuntu 10 server with Apache and PHP along with Concrete5 for our website consultant whom has built us a new website under /var/www/concrete5.4.0.5

I have tried to move the site to the /var/www directory so we can access it without adding the additional directory to the domain name.  However after moving all the files to the /var/www directory I get web page not found.

Any ideas how to correct this issue?  My guess is that its a permissions issue.

Thanks in advance,
Rodeoboy

Well I think it was due to permissions, but anyway I made a virtual site and all is well again.  So if anyone is trying to use the root www directory, save yourself some headaches and make a virtual web site.

Have a great New Years!
Rodeoboy

---

