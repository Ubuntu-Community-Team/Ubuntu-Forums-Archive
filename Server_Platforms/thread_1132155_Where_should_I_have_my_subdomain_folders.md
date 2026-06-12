---
title: "Where should I have my subdomain folders?"
date: 2009-04-21
forum: Server Platforms
---

### Post by cmwslw on 2009-04-21
I have my main web folder (example.com or [www.example.com](www.example.com)) set up in /var/www. I've just set up a subdomain (lets say abc.example.com). Right now I have that set up in /var/www/abc. This works fine, but is it the right/normal place to put a subdomain folder? I also noticed that abc's files can be accessed by either abc.example.com OR [www.example.com/abc](www.example.com/abc). This seems like it could cause problems/confusion.

Any suggestions?
-Cory Walker

---

### Post by Kareeser on 2009-04-21
It ultimately depends on you. However, because you may want to limit peoples' access to your clients' subdomain folders, it's better to isolate them.

For me, I do the following when I create a new subdomain:
1. Create a user using "adduser". This creates a home account for them.
2. mkdir /home/{newuser}/www
3. Add html/php files in the www folder.

---

