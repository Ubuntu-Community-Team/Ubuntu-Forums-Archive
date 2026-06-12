---
title: "Apache showing directory content"
date: 2006-05-28
forum: Server Platforms
---

### Post by el3ktro on 2006-05-28
Hello,

I want Apache to show the content of a certain directory on my webserver. There's no index.html in this directory, so it just lists the files in this directory Explorer-like. This is exactly what I want, it's just that the filename column is very narrow, is there a way to make this column wider so that long filenames display properly? I'd prefer to have this as a Apache2-wide setting, because I need this pretty often. Could I also remove some of the other columns that show the size or mtime etc.?

In other worlds: How and where can I configure how Apache2 does directory listings?

Tom

---

### Post by wapowell on 2006-05-28
Hi Tom,

Yeah, this link is just what you need.  This covers the exact example you mentioned.

Hope this helps you.  If you have other questions, please ask!

-Bill

[http://www.debian-administration.org/articles/195]("http://www.debian-administration.org/articles/195")

---

### Post by MJN on 2006-05-29
The directory listings are handled by the **autoindex** module - you'll find all the directives at:

[http://httpd.apache.org/docs/2.0/mod/mod_autoindex.html](http://httpd.apache.org/docs/2.0/mod/mod_autoindex.html)

As linked to by the previous poster the **namewidth** option in the **indexoptions** directive is what you're after. It may be worth you removing the Description column if you don't require it to free up screen space (using the** suppressdescription** option).

Mathew

---

