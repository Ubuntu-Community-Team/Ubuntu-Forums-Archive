---
title: "Paths changed on new nginx jnstall."
date: 2016-01-09
forum: Server Platforms
---

### Post by ex-para on 2016-01-09
I have  Nginx software running on a laptop as a server, I was getting a few problems as it had been working for a good few years so I re-installed  but some paths have changed on the new install 


example     gksudo gedit /var/www/nginx-default/index.html  (old path )
                   
                  gksudo gedit /usr/share/nginx/www/index.html      (my new path) it works

               
   sudo ln -s /var/www/my-www/my-index.html /var/www/nginx-default/index.html   (old path)

sudo ln -s /usr/www/www/index.html /usr/www/nginx-default/index.html    Would this path also work, if not please why not.
There are other paths but if the above worked I could then sort them out.  
I am using Ubuntu 12 lts.

---

### Post by matt_symes on 2016-01-09
Thread moved to **server platforms**.

This is a better forum for your query.

---

### Post by ex-para on 2016-01-10
Where will i find server platforms.

---

### Post by QIII on 2016-01-10
Right here.  Your thread has been moved.

---

