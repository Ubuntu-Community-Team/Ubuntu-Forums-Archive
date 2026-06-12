---
title: "apache permission for /var/www"
date: 2014-06-03
forum: Server Platforms
---

### Post by monkeybrain20122 on 2014-06-03
Hi,

I am trying to figure out what is the proper permission for www-data on /var/www
According to [http://askubuntu.com/questions/20105/why-shouldnt-var-www-have-chmod-777](http://askubuntu.com/questions/20105/why-shouldnt-var-www-have-chmod-777), it seems that it is a bad idea to give www-data write permission to /var/www, but does it need to have write permission to serve files, say image?

---

### Post by CharlesA on 2014-06-03
You only need to give www-data read permission unless you really needs to write to a folder like if you are running wordpress or owncloud or similar applications.

---

### Post by monkeybrain20122 on 2014-06-03
Thanks for the reply.
/var/www is owned by root:root. Now if I want to write to it without using sudo (say I am testing scripts) a common suggestion is to change the group for /var/www to www-data and add myself to the group and give it write permission. Does it sound like a sensible thing to do?

---

### Post by CharlesA on 2014-06-03
Or just change the owner to you.

```
sudo chown -R $user:$user /var/www
```

---

### Post by monkeybrain20122 on 2014-06-03
With permission 775 and www-data has the permission of 'others'?  (r+x)

---

### Post by CharlesA on 2014-06-03
> **monkeybrain20122 said:**
> With permission 775 and www-data has the permission of 'others'?  (r+x)

Correct. That should work fine unless you need to give the web server write access.

---

