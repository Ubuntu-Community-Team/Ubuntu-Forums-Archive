---
title: "apache config"
date: 2008-03-14
forum: Server Platforms
---

### Post by gjj391 on 2008-03-14
i got apache mysql and php working great,

 but I'd like to move cgi inside the www folder, kinda annoying for it to be some other place and is there a way to set the permissions different so i dont have to be su to do anything to /www

---

### Post by scragar on 2008-03-14
you could just re-chmod the folder:
```
sudo chmod -r 777 /var/www
```
but be warned that it's not exactly secure

---

