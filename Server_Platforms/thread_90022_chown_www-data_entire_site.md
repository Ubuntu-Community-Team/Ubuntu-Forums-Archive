---
title: "chown www-data entire site?"
date: 2005-11-14
forum: Server Platforms
---

### Post by yellowjelly on 2005-11-14
I have a small web server I'm toying with (breezy 5.10).  It has a couple virtual sites, etc.  During the install of a few content managment packages for testing, they suggest using chmod on directories to make things writable.  I'm a little worried about security.  They also suggested that I can chown these directories if possible.  Since I can do this and I am the only user on the system.  Is it OK to chown the entire web site directory to the apache user ( chown -R www-data [www.sample.com](www.sample.com) ) or ( "chown -R www-data web" which is where my index file resides ), instead of chown -R each separate sub directory for each package?

I don't like the idea of using .htaccess and chmod.

Thanks

---

### Post by LordHunter317 on 2005-11-14
It would be better to only change the ownership on the directories where the applications actually need to be able to write.

---

