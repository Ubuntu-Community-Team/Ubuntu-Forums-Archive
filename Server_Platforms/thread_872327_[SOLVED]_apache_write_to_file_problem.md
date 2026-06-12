---
title: "[SOLVED] apache write to file problem"
date: 2008-07-27
forum: Server Platforms
---

### Post by brocky102 on 2008-07-27
I am trying to write to a file with a web page hosted by apache but it can't write to the file. This website will also need to be able to restart different services any idea?

I tried to add www-data to the sudoers file but that didn't give me any luck at all. Also tried to add www-data to the root group but that didn't work also. 

I want this to work but at the same time be secure if that is at all possible. But I am happy to compromise on the security for the time been.

---

### Post by tamoneya on 2008-07-28
what file are you trying to right to.  Say it is /var/www/wrtiestuffhere you should just do this:```
sudo chown -R www-data:www-data /var/www/writestuffhere
```

---

