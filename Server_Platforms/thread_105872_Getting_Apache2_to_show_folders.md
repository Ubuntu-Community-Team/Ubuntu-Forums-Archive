---
title: "Getting Apache2 to show folders"
date: 2005-12-19
forum: Server Platforms
---

### Post by harisund on 2005-12-19
I am trying to add these lines to my  /etc/apache2/site-available/default file: 

Alias /comics/ "/home/harisund/comics/"
<Directory "/home/harisund/comics/">
Options Indexes Multiviews FollowSymLinks
Order deny,allow
Allow from all
</Directory>

And /comics/ works in my webpage. However, if I try to copy the above lines and paste them again , this time for a different folder, it says 

Forbidden

You don't have permission to access /gallery/ on this server.

Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.

Or simply without the "Additional......"

Any body think of a reason why? 

Thanks !

---

### Post by LordHunter317 on 2005-12-19
Make sure the www-data user has permissions to access the file and directories  in question.

---

### Post by harisund on 2005-12-19
www-data..hmm...thanks.. will look into that..

---

