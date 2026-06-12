---
title: "Server Configuration Recommendations?"
date: 2007-06-14
forum: Server Platforms
---

### Post by LebowskiT1000 on 2007-06-14
What is the best way to configure Apache such that I can have several separate instances of the same site on the same machine?  Essentially a bunch of sandboxes.  This is for development purposes, NOT for production.

I originally just tried having several different directories within the /var/www directory, but that didn't work for me, because I need each of the site instances to use a particular directory as the web document root directory (i.e. for userA, web root = /var/www/userA/dir1/dir2, for userB, web root = /var/www/userB/dir1/dir2, etc...)

Then I tried using the UserDir Module with Apache and that seems to have the same problem.

Any suggestions on what I can do?

-Chris

---

### Post by Mr. C. on 2007-06-15
Do virtual hosts not meet your needs ?

MrC

---

