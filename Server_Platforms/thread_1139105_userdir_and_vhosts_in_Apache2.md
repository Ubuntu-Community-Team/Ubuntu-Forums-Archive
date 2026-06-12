---
title: "userdir and vhosts in Apache2"
date: 2009-04-26
forum: Server Platforms
---

### Post by gmuir on 2009-04-26
I just recently was asked to setup a basic webserver box for a couple of friends that are planning on putting the machine in a colocation center. They own two domain names that they are planning to host out of the machine. I have setup vhosts to handle their domains to two separate directories so they can keep them separate. They are now asking if they can have one of the vhosts serve up userdirs but have the other not serve them. So if they get a request to [www.domain1.com/~user/](www.domain1.com/~user/) it will serve user's public_html but [www.domain2.com/~user/](www.domain2.com/~user/) will not.

From what I can tell, userdir.conf in mods-available is for the entire Apache installation. Is there anyway that I can setup apache to accept userdir requests on one domain and not another?

---

### Post by rrll1977 on 2009-05-18
Hi,

Have you got to work mod_rewrite with mod_userdir

I can't get mod_rewrite to work with user's pages on /home/user/public_html, although it appears to work fine for server root pages on /opt/lampp/htdocs

Regards

---

