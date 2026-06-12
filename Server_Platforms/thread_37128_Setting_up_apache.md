---
title: "Setting up apache"
date: 2005-05-26
forum: Server Platforms
---

### Post by DeekoVB5 on 2005-05-26
Ok I'm trying to get Apache2 running on my new Ubuntu setup.  It works for the default directory, but when I try to point it at my server(DocumentRoot /media/C/Inetpub/wwwroot/) it says connection refused.  Am I doing something wrong?

---

### Post by stevenyu on 2005-05-26
double check your apache2 config file in /etc

I use webmin to do all my setting on the server.

---

### Post by LordHunter317 on 2005-05-26
Post your /etc/apache2/sites-enabled/000-default file.  I hope that's the one you changed.

---

### Post by s0c0 on 2005-05-26
[QUOTE=DeekoVB5]Ok I'm trying to get Apache2 running on my new Ubuntu setup.  It works for the default directory, but when I try to point it at my server(DocumentRoot /media/C/Inetpub/wwwroot/) it says connection refused.  Am I doing something wrong?[/QUOTE]

Ensure you have configured the /etc/host file, ensure proper permissions are set on the doc root for yuor webpages.  Ensure you can ping the server and run a port scan on the server to ensure that port 80 is open.

---

