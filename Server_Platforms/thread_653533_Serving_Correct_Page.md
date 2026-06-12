---
title: "Serving Correct Page"
date: 2007-12-30
forum: Server Platforms
---

### Post by TANGUN on 2007-12-30
Ubuntu Server...check
Apache2...check
DNS names...check

Configuration...help!

I've got the DNS set up so that typing in the URL to my test site (test.server.com) serves a default page. When I type in the directory after the URL (test.server.com/test/) It serves the page in the 'test' directory. 

I'd like apache to redirect requests for test.server.com to test.server.com/test so I can keep my sites separate. I hope this also removes the default page.

QUESTION #1) How do I redirect the requests as described above?

"Sites?", you say. I also have separate directories which I can access from test.server.com/DirName/...however, I'd rather have them accessable by typing in just the URL.

Example: test.server.com redirects to test.server.com/test
and different.server.com redirects to different.server.com/different

QUESTION #2) How do I setup the VirtualHosts correctly to have each site served by the different addresses?

I think I need to create/edit a file for each site in '/etc/apache2/sites-available/SiteName...or should I change the default file in that directory?

Thanks all for your help!

---

### Post by g2g591 on 2007-12-30
1: in your /etc/apache2/sites-enabled/(either 000-default if you havn't created another, or another) add "RedirectMatch ^/$ /test/ " under <Directory /var/www/>

---

