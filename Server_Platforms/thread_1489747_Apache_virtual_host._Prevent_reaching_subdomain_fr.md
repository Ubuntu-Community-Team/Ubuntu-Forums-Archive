---
title: "Apache virtual host. Prevent reaching subdomain from main domain subfolder"
date: 2010-05-21
forum: Server Platforms
---

### Post by LarsOo on 2010-05-21
Hi!

I'm sorry if this issue is discussed and solved in several threads already. I can't find the correct words to use in a search. A short explanation below should give an idea to what my problem is.

I've have two virtual hosts, lets say:
site1.mydomain.com
site2.mydomain.com

These are located at
/var/www/site1
/var/www/site2

I've gotten the virtual host configuration to work properly since I can browse to site1.mydomain.com/site2.mydomain.com and they behave as expected. 

However, I don't like the fact that I can reach site1 by browsing to [www.mydomain.com/site1]("http://www.mydomain.com/site1")

What is the best way to avoid this?

1. Configure the default address ([www.mydomain.com]("http://www.mydomain.com")) so it is located at /var/www/default?
2. Configure the subdomains to other locations (/var/wwwsub/site1) ?
3. Secret option no 3?

Using 9.04. 

Thanks in advance.

---

