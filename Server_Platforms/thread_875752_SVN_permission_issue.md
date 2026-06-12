---
title: "SVN permission issue"
date: 2008-07-31
forum: Server Platforms
---

### Post by ErwinB on 2008-07-31
Hello,

I have to configure SVN & Trac on a server running Ubuntu. The installation was ok, configuration is done. Everything should be right, but I have a 403 error with Apache when I try to access the repository (event with public write permission + not any .htaccess), and SVN client can't access the repository too.

Does anyone have an idea? Thank you for your help,

Regards,

ErwinB

---

### Post by StickyStyle on 2008-08-04
If your still having the problem we need a few more details...

1. let's see the apache error log after you get the 403 error.
2. does trac work fine when you run it stand as its standalone daemon (tracd)?
3. how did you setup you SVN server; (x)initd, mod_dav_svn, svn daemon?
4. What are the permissions directory permissions on the repository?

---

