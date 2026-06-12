---
title: "fcannot access cgi-bin from local-host - permission forbidden"
date: 2011-06-16
forum: Server Platforms
---

### Post by Phil Stone on 2011-06-16
Using httpd - everything usually works but I have written a cgi script and placed in cgi-bin but i cannot access this dir and keep getting forbidden messages.
I have tried adding my root and usual user to the /etc/group file against the user stipulated in the httpd.conf file  but i still can't access the cgi script i wrote (in browser - localhost/cgibin/myscrippt.cgi) when i place it in the cgi-bin under htdocs.  i have also chmod 755 directory and files.

Any suggestions please?

Phil

---

### Post by Phil Stone on 2011-06-20
Error was - I was using a cgi-bin under my htdocs to reflect the live site, as well as permissions. I have this working now. Basically by placing my script in the correct cgi-bin under the apache2 directory and setting permissions correctly.

Solved by - Reading Error Log / httpd.conf & Consulting Apache faq's. 
Thanks Apache working group :) 

Phil

---

