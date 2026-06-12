---
title: "Ubuntu Apache fails"
date: 2013-05-24
forum: Server Platforms
---

### Post by mariuszp on 2013-05-24
I am running Ubuntu 12.04.2 LTS (GNU/Linux 3.2.0-38-generic-pae i686), with SSH, FTP, Apache (and PHP and MySQL), and a Minecraft server. IT was all working fine, until I've done some update. SSH, FTP and Minecraft are all working correctly, but Apache does not. When I type in 'service apache2 restart' I get:

```

 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting .apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]

```

I am able to connect with my server and see the website (using lynx) from the server itself (if i conenct to localhost). However, if I try to connect from the outside, it fails to connect. Even on the server, if I use the router's IP address, it can't connect - only localhost.

Does anyone know what to do about this?

---

### Post by mariuszp on 2013-05-24
OK, never mind, fixed it. Turned out to be some strange router problem.

---

