---
title: "Question about configuring Apache php server"
date: 2008-02-06
forum: Server Platforms
---

### Post by Olnex on 2008-02-06
I have desktop version with apache server utilities installed, I found that all web are in /var/www, what I want is to give each user the right to make their own web, so that:
user Tom with user name tom can access his web(and can be accessed by others) by going to:
[http://localhost/~tom](http://localhost/~tom)
and Tom can put his web files into something like /home/tom/WWWPublic

Thanks a lot

---

### Post by jken146 on 2008-02-06
You could make a folder in /var/www for each user, for example ```
sudo mkdir /var/www/tom
``` then change the ownership of those folders to reflect the user they are intended for, e.g. ```
sudo chown tom:tom /var/www/tom
```

If you want all users to be able to access all folders in /var/www, you'll need to give all users read permissions on them, i.e. ```
sudo chmod -R a+r /var/www
```

---

