---
title: "Change Server Information"
date: 2005-10-03
forum: Server Platforms
---

### Post by morficus on 2005-10-03
Sorry for my lack of technical terms but... How do I get Appache to stop showing so much information about my server?

you know.. the server info it puts at the end of the dir when view it

> Apache/2.0.53 (Ubuntu) PHP/4.3.10-10ubuntu4.1 Server at [*your-web-addres-here*] Port 80

Is there a way to make is show only certain things?
thanx

-morficus

---

### Post by morficus on 2005-10-03
hhmm... is this even posible?

---

### Post by NixMonk on 2005-10-03
Change ServerSignature to off in /etc/httpd/conf/httpd.conf, and restart apache.

```

#
# Optionally add a line containing the server version and virtual host
# name to server-generated pages (error documents, FTP directory listings,
# mod_status and mod_info output etc., but not CGI generated documents).
# Set to "EMail" to also include a mailto: link to the ServerAdmin.
# Set to one of:  On | Off | EMail
#
ServerSignature Off

```

---

### Post by NixMonk on 2005-10-03
Sorry, I'm too used to RedHat's way of doing things.
Under Ubuntu append this to your /etc/apache2/apache2.conf
```

ServerTokens Prod

```
Servertokens info @ [http://httpd.apache.org/docs/2.0/mod/core.html#servertokens](http://httpd.apache.org/docs/2.0/mod/core.html#servertokens)
It seem's ServerSignature doesn't work the same with Apache2.

---

### Post by morficus on 2005-10-03
wow, thanx :razz:

---

### Post by Garciat on 2008-01-15
Is there a way to make it a custom message?

---

### Post by MJN on 2008-01-15
Not easily, and likely not without compiling from source. See [this thread](http://ubuntuforums.org/showthread.php?t=629397) for a similar discussion (which may help in deciding if you really need/want to).

Mathew

---

