---
title: "running apache2 as root"
date: 2005-11-22
forum: Server Platforms
---

### Post by Snargle on 2005-11-22
I remember hearing somewhere that it's a bad idea to run Apache as root, but I don't know of any way around it in ubuntu. 

I get this error:
```

zach@zm:~$ apache2
(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

```

Is there a simple solution to this, and if so, why isn't it in the Breezy starter guide?

Thanks

---

### Post by LordHunter317 on 2005-11-22
You have to start Apache as root.  That doesn't mean Apache is running as root.

---

### Post by paddyg on 2005-11-22
...as files are served by unprivileged child processes (www-data)

---

### Post by s0c0 on 2005-11-23
Yes in ubuntu you have to use the sudo command and then start apache.  The apache config file defaults to www-data as the user/group and in most cases it should be left this way.

---

