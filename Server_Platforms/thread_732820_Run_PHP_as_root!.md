---
title: "Run PHP as root?!?"
date: 2008-03-23
forum: Server Platforms
---

### Post by Dudsmacka2 on 2008-03-23
Running latest 7.10 server edition.

Trying to use sockets in php.  First installed using LAMP option from installer, then installed sockets w/
```
sudo apt-get install php-net-socket
```

phpinfo() is showing sockets as enabled.

Getting the following error when trying to create a socket:

```
**Warning:** socket_create() [function.socket-create]: Unable to create socket [1]: Operation not permitted in /var/www/... 
```

My best guess is that this is a permission problem.  I would be greatly appreciative if anyone could help point m in the right direction!

---

