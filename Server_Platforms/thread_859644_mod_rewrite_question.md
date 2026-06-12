---
title: "mod_rewrite question"
date: 2008-07-14
forum: Server Platforms
---

### Post by Phristen on 2008-07-14
I am using apache2, and I need everything to be redirected to a single page (let's call it index.php), even when the requested file doesn't exist. 500 errors should also redirect there.
Also, the address bar should still read whatever the user entered, NOT index.php.

Is it possible to do this with htaccess?

---

### Post by skunkbad on 2008-07-15
I don't think it can be done with mod_rewrite, but if it can be done in some other way, you need to make sure that you are using a 301 redirect, or the duplicate content will make search engines think you are a bad person.

---

### Post by amenszer on 2008-07-17
This thread may help you out.
[http://www.phpbb-seo.com/boards/apache-mod-rewrite/discussions-vt1799.html]("http://www.phpbb-seo.com/boards/apache-mod-rewrite/discussions-vt1799.html")

---

