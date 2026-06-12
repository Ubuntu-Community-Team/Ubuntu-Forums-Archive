---
title: "Virtual Directory Listing Deny on apache"
date: 2008-01-01
forum: Server Platforms
---

### Post by kool_kat_os on 2008-01-01
I have apache 2 on windows xp (unfortunately)  and I need to make it so it does not show the contents of a directory? ie: if there is a picture at "www.mysite.com/images/mypicture.gif" how do I make it so that if you type in "www.mysite.com/images" it does not show the contents of that folder? Thanks

---

### Post by kool_kat_os on 2008-01-01
anyone???

---

### Post by Mr. Picklesworth on 2008-01-01
Sorry, I don't have time to go into detail, but check out ".HTACCESS" files. (Google gives lots of good links there).

---

### Post by andol on 2008-01-01
Well, you could use .htaccess, or simply make the modification in your apache-conf.

What you want to do is to disallow the Option Indexes.

[http://httpd.apache.org/docs/2.0/mod/core.html#options](http://httpd.apache.org/docs/2.0/mod/core.html#options)

---

