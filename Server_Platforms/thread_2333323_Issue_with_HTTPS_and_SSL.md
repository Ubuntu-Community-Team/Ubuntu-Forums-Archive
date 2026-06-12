---
title: "Issue with HTTPS and SSL"
date: 2016-08-09
forum: Server Platforms
---

### Post by adrdev on 2016-08-09
Hi all!!

It's possible to serve websites in the same host with the same apache some in https and others in simple http? 

If it is possible, can anyone give me a hint to make it works?

Thanks in advance!!

---

### Post by darkod on 2016-08-09
Each site has it's own .conf file in /etc/apache2/sites-available. In this .conf file you can enable or not HTTPS so you can serve some sites only in HTTP and others in HTTP and HTTPS.

---

### Post by SeijiSensei on 2016-08-09
Well, it's a bit more complicated than that.  While you can have multiple HTTP virtual hosts, usually you can only have one HTTPS host per IP address.  So if you wanted to have one SSL site and one or more unencrypted sites, you can do that with one IP address.  The HTTPS host listens on port 443 while the HTTP hosts listen on port 80.

There are newer methods to get around the one-IP restriction, but not all browsers support them.

The default SSL configuration is stored in /etc/apache2/sites-available/default-ssl.conf.

---

