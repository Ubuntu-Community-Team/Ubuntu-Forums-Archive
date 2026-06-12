---
title: "Cannot access Lamp when no network..."
date: 2008-09-19
forum: Server Platforms
---

### Post by zccpop on 2008-09-19
I followed the wiki:   [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
to finish the LAMP configuration.
And it works perfectly.

But today I found a problem: when I pulled out the wire, and no network or lan. I cannot access [http://localhost/](http://localhost/)

Have you met such questiones? 
What should I do ?

---

### Post by cdenley on 2008-09-19
> **zccpop said:**
> I followed the wiki:   [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
to finish the LAMP configuration.
And it works perfectly.

But today I found a problem: when I pulled out the wire, and no network or lan. I cannot access [http://localhost/](http://localhost/)

Have you met such questiones? 
What should I do ?

Make sure your server is listening to *:80
```

sudo lsof -n -i :80

```
Make sure it isn't a name resolution issue
```

telnet 127.0.0.1 80
GET / HTTP/1.0
[blank line]

```

---

### Post by zccpop on 2008-09-19
> **cdenley said:**
> Make sure your server is listening to *:80
```

sudo lsof -n -i :80

```
Make sure it isn't a name resolution issue
```

telnet 127.0.0.1 80
GET / HTTP/1.0
[blank line]

```

When I typed the first code, it displayed:
```

COMMAND  PID     USER   FD   TYPE DEVICE SIZE NODE NAME
apache2 5886     root    3u  IPv6  14868       TCP *:www (LISTEN)
apache2 5973 www-data    3u  IPv6  14868       TCP *:www (LISTEN)
apache2 5974 www-data    3u  IPv6  14868       TCP *:www (LISTEN)
apache2 5975 www-data    3u  IPv6  14868       TCP *:www (LISTEN)
apache2 5976 www-data    3u  IPv6  14868       TCP *:www (LISTEN)
apache2 5977 www-data    3u  IPv6  14868       TCP *:www (LISTEN)
firefox 6230      zcc   21w  IPv4  22020       TCP 172.24.213.161:50062->64.233.189.102:www (ESTABLISHED)
firefox 6230      zcc   46u  IPv4  23810       TCP 172.24.213.161:58455->74.125.11.19:www (CLOSE_WAIT)
firefox 6230      zcc   53u  IPv4  24017       TCP 172.24.213.161:39277->91.189.94.12:www (ESTABLISHED)
apache2 6648 www-data    3u  IPv6  14868       TCP *:www (LISTEN)

```

It may have listened.
and I donnot know the second.

---

