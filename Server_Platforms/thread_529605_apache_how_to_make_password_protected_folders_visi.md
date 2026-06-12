---
title: "apache: how to make password protected folders visible when browsing?"
date: 2007-08-19
forum: Server Platforms
---

### Post by James79 on 2007-08-19
My root directory is configured with "Options Indexes" to allow for browsing. I wanted to password protect only one of its subdirectories, so in there I placed an .htaccess file and created a corresponding htpasswd file.

Everything does in fact work well. The problem is that when I browse the root directory, I no longer see the password protected subdirectory listed there. I can access it by typing its name in manually (and I get prompted with the password as expected), but I would still want the existance of the folder to be visible to all.

How do I enable this?

Thanks!

---

### Post by James79 on 2007-08-24
Bump :oops:

There has to be an easy fix for this. The problem is, searching google for "apache htaccess hidden" etc etc just returns a million hits for people who don't understand why their .htaccess seemingly disappears :)

Thanks for any insight...

---

### Post by Ryan Hemelaar on 2008-06-09
The way Apache is acting is by design, a person must be authorised to even see a password-protected directory. But to override this functionality, add ***IndexOptions ShowForbidden*** to your .htaccess in the directory where you are listing the index.

---

