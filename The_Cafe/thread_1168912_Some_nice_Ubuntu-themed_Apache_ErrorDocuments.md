---
title: "Some nice Ubuntu-themed Apache ErrorDocuments"
date: 2009-05-24
forum: The Cafe
---

### Post by avahi on 2009-05-24
The default Apache errordocuments put me to sleep, so I've decided to make some nice Ubuntu-toned replacements for my Ubuntu servers.

They are colored by a CSS stylesheet, so it's easy to change the colors for all of them at once.

-----
How to use:

1) Drag the "errordocs" folder in the attached .zip file to your site's root directory

2) In your apache2.conf, add or replace the following lines:

```
ErrorDocument 401 /errordocs/401.html
ErrorDocument 403 /errordocs/403.html
ErrorDocument 404 /errordocs/404.html
ErrorDocument 410 /errordocs/410.html
ErrorDocument 414 /errordocs/414.html
ErrorDocument 418 /errordocs/418.html
ErrorDocument 500 /errordocs/500.html
ErrorDocument 503 /errordocs/503.html
ErrorDocument 509 /errordocs/509.html
```

3) Restart Apache

Enjoy :)
Free to use under GPLv3.

---

### Post by mr.propre on 2009-05-24
It's more user friendly to give people direction's instead of just giving them an error message. Like a search box or your default webpage with a small error message.

Just my &#8364;0.02

*spamMode*
Like this: [http://www.stijn-dhaese.be/blog/2009/04/nothingtofindhere/](http://www.stijn-dhaese.be/blog/2009/04/nothingtofindhere/)
*/spamMode*

---

### Post by billgoldberg on 2009-05-24
> **mr.propre said:**
> It's more user friendly to give people direction's instead of just giving them an error message. Like a search box or your default webpage with a small error message.

Just my €0.02

*spamMode*
Like this: [http://www.stijn-dhaese.be/blog/2009/04/nothingtofindhere/](http://www.stijn-dhaese.be/blog/2009/04/nothingtofindhere/)
*/spamMode*

I agree.

---

