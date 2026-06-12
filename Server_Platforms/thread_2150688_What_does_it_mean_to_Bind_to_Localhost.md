---
title: "What does it mean to: Bind to Localhost?"
date: 2013-06-01
forum: Server Platforms
---

### Post by Ravenshade on 2013-06-01
I've seen a few of these items, specifically when you want a secure server that doesn't accept incoming connections from say over the internet. However I've never seen it explained or given a satisfactory answer. 

So how would one bind a server to say 127.0.0.1 (eg localhost)? 

Kind Regards.

---

### Post by bab1 on 2013-06-02
> **Ravenshade said:**
> I've seen a few of these items, specifically when you want a secure server that doesn't accept incoming connections from say over the internet. However I've never seen it explained or given a satisfactory answer. 

So how would one bind a server to say 127.0.0.1 (eg localhost)? 

Kind Regards.
Configure it to only accept a connection to that interface.  This is usually done in the individual servers (services) configuration file.

---

### Post by SeijiSensei on 2013-06-02
In Apache, for instance, the default virtual host entry in /etc/apache2/ports.conf includes the line:

```
NameVirtualHost  *:80
```

which tells Apache to listen to port 80 on all interfaces.  Replacing that with 

```
NameVirtualHost 127.0.0.1:80
```

would tell it to listen only on localhost.

Many Ubuntu services are configured to bind to localhost by default for security reasons.  The primary examples are mail servers like Postfix and sendmail and, I believe, database servers like MySQL and PostgreSQL as well.  Apache is shipped to listen on all interfaces as I described above.

Apache is especially flexible in this regard.  You can bind specific virtual hosts to specific IP/port combinations.  For instance, I built a gateway for a client with a web-based configuration interface.  I bound the configuration site to the gateway's internally-facing network interface and put it on a non-standard port.  Thus it is entirely invisible to outside visitors, and only visible to internal staff if they know which port to use.

---

### Post by Ravenshade on 2013-06-02
Ah excellent...

Nginx  "listen 80 default_server; listen [::]:80 default..." shoudl be perfectly acceptable then, thank you!

---

