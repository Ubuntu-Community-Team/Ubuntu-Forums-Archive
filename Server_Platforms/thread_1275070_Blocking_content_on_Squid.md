---
title: "Blocking content on Squid?"
date: 2009-09-25
forum: Server Platforms
---

### Post by Trifid on 2009-09-25
Hello.

I'm trying to block a certain website on squid, even if someone tries to access it through a web proxy.

Currently I have this in the conf

acl block url_regex "/etc/squid/squid-block.acl"
http_access deny block

and the site blocked in the acl file which works. Unfortunately the site can be accessed through a wed proxy. 

Is there a way to actively block content that contains certain words? I.e. "facebook"

Thanks.

---

### Post by i.r.id10t on 2009-09-25
If they are going out via a different proxy you can't do it...

---

### Post by Trifid on 2009-09-25
They are hitting my proxy server first and then going to a web based proxy service to access Facebook. I would like to be able to block any page containing the word facebook in the content and not just the url.

---

