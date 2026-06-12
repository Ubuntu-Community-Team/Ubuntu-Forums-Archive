---
title: "apache configuration problems"
date: 2009-11-09
forum: Server Platforms
---

### Post by luftadler on 2009-11-09
I try to activate a new website on Apache and it gives me an error

this are the steps I've made:

```
mkdir -p /srv/www/tralala.edu/public_html
``````
a2ensite tralala.edu
Site tralala.edu does not exist!
``````
a2ensite /srv/www/tralala.edu 
ERROR: No site found matching /srv/www/tralala.edu
```This is first time when I make this kind of operations...
Any help will be appreciated!

Thank you!

---

### Post by Iowan on 2009-11-09
[Here]("https://help.ubuntu.com/community/ApacheMySQLPHP") is a good help page to get started - especially [this]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts") virtual hosts section.

---

### Post by luftadler on 2009-11-12
Thank you! Very useful tutorial. :)

---

