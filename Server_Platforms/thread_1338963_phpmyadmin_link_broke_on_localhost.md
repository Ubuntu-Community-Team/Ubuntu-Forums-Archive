---
title: "phpmyadmin link broke on localhost"
date: 2009-11-27
forum: Server Platforms
---

### Post by tapas_mishra on 2009-11-27
In an earlier thread on the community I had asked regarding my apache2 configuration right now apache2 has started working phpmyadmin on localhost has broken 
[http://localhost/phpmyadmin](http://localhost/phpmyadmin) 
shows  me 
**[SIZE=2]Oops! This link appears to be broken.[/SIZE]**

Where should  I look in

---

### Post by Queue29 on 2009-11-27
If you installed apache2 and phpmyadmin through apt-get, there should be a directory /etc/apache2/sites-enabled/ and in that directory there should be a symlink called phpmyadmin. There should also be near the bottom of /etc/apache2/apache2.conf a line that says "Include /etc/apache2/sites-enabled" and it should _not_ be commented out.

---

