---
title: "why am i getting 403 &quot;Forbidden&quot; error"
date: 2009-08-09
forum: Server Platforms
---

### Post by rhythmiccycle on 2009-08-09
i'm setting up a web site, i have it working on my laptop running xp and xampp. 

i have ubuntu desktop with LAMP installed.

i have an html file i named "toolbox.html" in a folder called "admin"

this html file is just a page of links, to go to pages that initialize and display tables on a data base.

when i try to open the page i get "403 Forbidden: You don't have permission to access /admin/ToolBox.html on this server."

i didn't get this error when i was tesing the site on my laptop.

why am i getting this message and how do i change it?

---

### Post by rhythmiccycle on 2009-08-09
i solved my own problem using the  code

```
sudo chmod a=rwx /var/www/admin/ToolBox.html
```

[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

---

