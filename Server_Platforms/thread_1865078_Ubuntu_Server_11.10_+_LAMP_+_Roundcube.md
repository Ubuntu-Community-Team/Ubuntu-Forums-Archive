---
title: "Ubuntu Server 11.10 + LAMP + Roundcube"
date: 2011-10-19
forum: Server Platforms
---

### Post by ftornell on 2011-10-19
Hi,
Im trying to get Roundcube e-mailclient up but it fails.

The webpage says "Connection to IMAP server failed".

I have installed ubuntu server as a webserver with apache, mysql, php, and postfix.

if I restart apache I get:
```

* Restarting web server apache2                                                                                                                                                                                                             apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

```

everything else seems to work ok, except to login to the page.

---

### Post by newbie-user on 2011-10-19
You'd have to check that you set up Roundcube to access the correct mail server.  Check your config files for Roundcube to make sure that your mail server is referenced correctly and that you're using the correct ports for the mail server.

---

