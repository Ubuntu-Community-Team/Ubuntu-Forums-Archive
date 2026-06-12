---
title: "webserver behind monowall safe enough?"
date: 2009-08-12
forum: Server Platforms
---

### Post by Adina on 2009-08-12
Hi, I have up a webserver at home behind a monowall and I got inbound nat working so the web site is available from internet. Is this setup secure enough or do I need more security on my server? 
The server is a new install of ubuntu 8.04 with only sshd and apache2 installed and the monowall only has open port 80 that is natted to the lan ip of the server.

---

### Post by alastair on 2009-08-12
Hard to say - without knowing the monowall security system (but I have also considered a monowall mini-pc/router/firewall). I think if you keep things fully patched (8.04 and monowall) and take care with secure config (and watch logs), it's possible. Tighten things up and keep an eye open ...

---

### Post by Adina on 2009-08-12
Thanks for your reply, I will try to read logs like you said. Is it /var/log/apache2/ you meant? I will also try to learn more about ubuntu server security. Thanks again I really appreciate it!

---

### Post by alastair on 2009-08-12
Keep your install up to date - watch for package/security updates.

Plus :

Ubuntu Security
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Securing Debian
[http://www.debian.org/doc/manuals/securing-debian-howto/index.en.html](http://www.debian.org/doc/manuals/securing-debian-howto/index.en.html)

---

### Post by Adina on 2009-08-13
Thanks again! I will read more about security.

---

