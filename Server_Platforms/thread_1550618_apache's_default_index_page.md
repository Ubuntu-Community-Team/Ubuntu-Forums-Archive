---
title: "apache's default index page"
date: 2010-08-11
forum: Server Platforms
---

### Post by fantastic on 2010-08-11
How do you change the default indexing page in apache (meaning when indexing is turned on)? Right now it displays the IP address and port number at bottom. I'm trying to remove the IP and port number from the bottom but cannot seem to figure out where to change it.

---

### Post by Bachstelze on 2010-08-11
You would change that in /etc/apache2/conf.d/security.

---

### Post by fantastic on 2010-08-11
> **Bachstelze said:**
> You would change that in /etc/apache2/conf.d/security.

Thanks.

I've made these changes

```
ServerSignature Off
ServerTokens Prod
```

and then restarted apache, but when I view that indexing page or a 404 it still displays the OS, IP and port.

Am I changing wrong settings?

---

### Post by Bachstelze on 2010-08-11
No, those are the right settings. Did you do something unusual with your Apache config?

---

### Post by fantastic on 2010-08-11
> **Bachstelze said:**
> No, those are the right settings. Did you do something unusual with your Apache config?

I modified ports.conf to include:

```
NameVirtualHost *:82
Listen 82
NameVirtualHost *:83
Listen 83
NameVirtualHost *:84
Listen 84
```

And I modified 000-default to include VirtualHost entries for each port, similar to:

```
<VirtualHost *:82>
  ServerAdmin webmaster@localhost
      ServerName mydomain.com
      DocumentRoot /usr/local/bin/www/mydomain/
      <Directory /usr/local/bin/www/mydomain/>
              Options Indexes FollowSymLinks MultiViews
              AllowOverride None
              Order allow,deny
              allow from all
      </Directory>
</VirtualHost>
```

---

### Post by cdenley on 2010-08-11
Works fine for me.

Before:
```

[COLOR="SlateGray"]cdenley@vmware:~$[/COLOR] grep "^[^#]" /etc/apache2/conf.d/security
[B]ServerTokens OS
ServerSignature On[/B]
TraceEnable Off
[COLOR="SlateGray"]cdenley@vmware:~$[/COLOR] echo -e "GET /does/not/exist HTTP/1.0\n"|nc -q 1 127.0.0.1 80
HTTP/1.1 404 Not Found
Date: Wed, 11 Aug 2010 15:24:59 GMT
**Server: Apache/2.2.14 (Ubuntu)**
Vary: Accept-Encoding
Content-Length: 296
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>404 Not Found</title>
</head><body>
<h1>Not Found</h1>
<p>The requested URL /does/not/exist was not found on this server.</p>
<hr>
**<address>Apache/2.2.14 (Ubuntu) Server at vmware.localdomain Port 80</address>**
</body></html>

```

After:
```

[COLOR="SlateGray"]cdenley@vmware:~$[/COLOR] grep "^[^#]" /etc/apache2/conf.d/security
[B]ServerTokens Prod
ServerSignature Off[/B]
TraceEnable Off
[COLOR="SlateGray"]cdenley@vmware:~$[/COLOR] echo -e "GET /does/not/exist HTTP/1.0\n"|nc -q 1 127.0.0.1 80
HTTP/1.1 404 Not Found
Date: Wed, 11 Aug 2010 15:25:42 GMT
**Server: Apache**
Vary: Accept-Encoding
Content-Length: 212
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>404 Not Found</title>
</head><body>
<h1>Not Found</h1>
<p>The requested URL /does/not/exist was not found on this server.</p>
</body></html>

```

Perhaps your browser is displaying a cached response.

---

### Post by fantastic on 2010-08-26
I meant to respond to this and forgot.

I added the following to /etc/apache/apache2.conf and restarted apache:

```
ServerSignature Off
ServerTokens Prod
```

---

