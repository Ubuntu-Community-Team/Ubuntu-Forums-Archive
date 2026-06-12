---
title: "Domain root"
date: 2012-02-05
forum: Server Platforms
---

### Post by fistuks on 2012-02-05
Hey all,

I just upgraded myself from a shared hosting plan to a dedicated server and I have a newbie question...

My server will host multiple domains.
My server's root directory is /var/www

I added a domain to the site-available and site-enabled restarted apache2 and everything works great with one problem.

Right now if you go to via the browser to my server's ip you will get the index file at /var/www

The new domain's DocumentRoot is pointing to:
/var/www/sites/SOMEDOMAIN

For testing, I placed an index file at the domain directory and if i go to:
[www.XXX.com/index.php](www.XXX.com/index.php)
I works great but if i go to 
[www.XXX.com](www.XXX.com)
I get the index of the root (the one at /var/www. 

What do i need to do to change in order to make it work in a way that each domain will point to it's own index file when navigating to the domain without a reference to a specific page?

---

### Post by fistuks on 2012-02-05
Embarrassing :)

After hours of hair pulling, just needed to clean the browser's cache.

Hope others will be smarter to check the forum before wasting time and will get this post.

Found the solution here:
[http://ubuntuforums.org/showthread.php?t=1556868]("http://ubuntuforums.org/showthread.php?t=1556868")

---

