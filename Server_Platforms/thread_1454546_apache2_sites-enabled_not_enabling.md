---
title: "apache2 sites-enabled not enabling?"
date: 2010-04-14
forum: Server Platforms
---

### Post by superradical on 2010-04-14
So I am trying to add some sites to my server, right now I have an active site at www2.site.tld.  As a test, I copied www2.site.tld to what.site.tld, and changed only the line

ServerName www2.site.tld 

to

ServerName what.site.tld

as well as renaming the lines for the log files appropriately
then
# a2ensite what.site.tld
# /etc/init.d/apache2 restart

which by everything I have read should result in what.site.tld being identical to [www.site.tld](www.site.tld).  Instead, it flat-out does not resolve.
Apache does create some blank log files in /var/www/
Your thoughts?

---

### Post by iissmart on 2010-04-15
You aren't changing your DNS settings (or at least you didn't mention it) so that what.site.tld points to the same IP as [www.site.tld](www.site.tld). Fix that, then wait ~1hr at most for the DNS settings to propogate, and try again.

---

