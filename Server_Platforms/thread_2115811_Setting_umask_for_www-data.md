---
title: "Setting umask for www-data?"
date: 2013-02-14
forum: Server Platforms
---

### Post by jmickela on 2013-02-14
I'm using 10.04 and am having some problems setting the umask for www-data.

I want to use a umask of 002 when the web server creates files, but nothing I do changes it from the default. I've tried adding 
```

umask 002

```

to: /etc/init.d/apache2
/etc/apache2/envvars
/home/www-data/.bashrc

I have restarted the web server after every file change. What am I missing?

---

### Post by papibe on 2013-02-14
Hi jmickela.

Instead of restarting, try stop and the start.

Just a thought.

Let us know how it goes.
Regards.

---

### Post by jmickela on 2013-02-14
Looks like that did it! Thanks a lot.

---

