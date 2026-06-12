---
title: "curious about apache directive or module related to appending file suffixes"
date: 2007-09-18
forum: Server Platforms
---

### Post by mattie_linux on 2007-09-18
I recently moved from an old Apache 1.x server that i had no control over, to a new Apache 2.x server.

One strange thing changed:

We have some links that point to a page, [FONT="Courier New"]**foo.html**[/FONT].

But rather than have the href point to **[FONT="Courier New"]foo.html[/FONT]**, the link points to "**[FONT="Courier New"]foo[/FONT]**" and worked in the old system. It actually found foo.html, even though the link points to "foo" ***with no suffix***.

(i didn't make these pages, and agree if you think it serves no purpose to do this).

When we switched to Apache 2, these "foo" links stopped working, and get the 404 messages I'd normally expect.

I'm willing to pour over my tree and fixes these links manually, but I'm wondering if anybody could identify the Apache directive or module that addresses this.

---

### Post by a9k on 2007-09-22
see if the old config had 
AddHandler type-map .var
in it. If so you had content negotiation running in 1.3.

[http://httpd.apache.org/docs/1.3/content-negotiation.html](http://httpd.apache.org/docs/1.3/content-negotiation.html)

---

### Post by g14 on 2007-09-22
Doing that is not good performance-wise, but you can do what you're trying to do with mod_rewrite. You might also look at mod_speling:
[http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html](http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html)
[http://httpd.apache.org/docs/2.0/mod/mod_speling.html](http://httpd.apache.org/docs/2.0/mod/mod_speling.html)

---

