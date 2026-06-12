---
title: "Docker test on Ubuntu 16.04 server"
date: 2017-07-31
forum: Server Platforms
---

### Post by satimis on 2017-07-31
Hi all,

Host  Ubuntu 16.04 desktop
VM  Ubuntu 16.04 server
Oracle VirtualBox

I followed;
Dockerizing LEMP Stack with Docker-Compose on Ubuntu
[https://www.howtoforge.com/tutorial/dockerizing-lemp-stack-with-docker-compose-on-ubuntu/](https://www.howtoforge.com/tutorial/dockerizing-lemp-stack-with-docker-compose-on-ubuntu/)

Installation went through without problem until;
Step 6 - Testing

```

We can see port 80 for the Nginx container, port 3306 for the MariaDB container, port 9000 for the php-fpm container, and port 8080 for the PHPMyAdmin container.

Access port 80 from the web browser, and you will see our index.html file.

```

1)
[http://ip_address:80](http://ip_address:80)
Unable to connect

2)
[http://ip_address:3306](http://ip_address:3306)
see attached photo

3)
[http://ip_address:9000](http://ip_address:9000)
The connection was reset

3)
[http://ip_address:8080](http://ip_address:8080)
start phpMyAdmin
Welcome to phpMyAdmin

Please advise what is "Access port 80 from the web browser"?

Thanks

Regards
satimis

---

### Post by Frogs Hair on 2017-07-31
Moved to *Server Platforms *

---

