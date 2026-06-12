---
title: "apache2 two sites in subfolders?"
date: 2009-02-04
forum: Server Platforms
---

### Post by neuromancer2701 on 2009-02-04
I have been running a wordpress mu site(experimental).  I put a new installation in the root and the old site in the a subfolder.

I can access both sites but when I click on links on the subfolder site they link back to the main one.  All the links are display correctly when hovered over.

ie   url/alpha/groups/ is displayed but when click it takes you to url/groups/

I have been messing around with splitting them out into two separate folders /var/www/beta/ and /var/www/alpha/ but I don't think that I am configuring apache2 correctly.

What would be the best way to do this?  It should not be a problem if the test users have to add /alpha/ to the url manually to get the old site.

Thanks
Seth

---

### Post by Poleh on 2009-02-04
> **neuromancer2701 said:**
> 
I have been messing around with splitting them out into two separate folders /var/www/beta/ and /var/www/alpha/ but I don't think that I am configuring apache2 correctly.

What would be the best way to do this?  It should not be a problem if the test users have to add /alpha/ to the url manually to get the old site.

Thanks
Seth

Definately splitting into two sites is best - this is known as vhosts and allows you run multiple sites on a single server. This is a good way to keep instances of installs separate and test functionality.

Here's a good link to a vhosts tut - not the current version of Ubuntu but it is still relevant: [http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/](http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/)

Moving websites to sub-folders, particularly dynamic ones like Wordpress is always prone to break things - you could try checking your wordpress setup for a "document / site root" which refers to the top-level of the site, and change that to point to the sub-folder you moved things to.

GL!

---

