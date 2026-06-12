---
title: "Trying to hide Apache version via httpd.conf  but not working, why?"
date: 2009-08-20
forum: Server Platforms
---

### Post by jocampo on 2009-08-20
Hi

I am trying to hide some Apache WebServer info via httpd.conf , but it seems my changes are not being recognized. I restart apache webserver and also the whole server and nothing. When testing with a not existing folder, this is what I get

```

Not Found

The requested URL /another/ was not found on this server.
Apache/2.2.11 (Ubuntu) Server at x.x.x.x Port 80

```

This is what I'm doing (at httpd.conf file)

```

ServerSignature Off
ServerTokens Prod

```

Obviously, you can see that my Apache webserver version is: 2.2.11

Thanks in advance,

---

### Post by Thirtysixway on 2009-08-20
I believe those settings actually go into apache2.conf, not httpd.conf

---

### Post by Bachstelze on 2009-08-20
Also check /etc/apache2/conf.d/security. On my Debian server, it is included at the end of the main config file, so if those settings are defined it in, they would override yours.

---

### Post by jocampo on 2009-08-20
Thanks for reply ... weird..all online documentation points to httpd, like [http://www.petefreitag.com/item/505.cfm]("http://www.petefreitag.com/item/505.cfm") Maybe the changed that in this new version.

Let me try again ...

---

### Post by jocampo on 2009-08-20
I had to changed it at apache2.conf but why? 

Online and couple of books I have say that change suppose to go at httpd.conf .... also, I noticed that service /etc/init.d/httpd does not exist on mine, it looks like my version is different

---

### Post by Thirtysixway on 2009-08-20
> **jocampo said:**
> I had to changed it at apache2.conf but why? 

Online and couple of books I have say that change suppose to go at httpd.conf .... also, I noticed that service /etc/init.d/httpd does not exist on mine, it looks like my version is different

I've never worked with it, but maybe your book uses Apache 1 or something. :popcorn: not sure.

---

### Post by jocampo on 2009-08-20
> **HymnToLife said:**
> Also check /etc/apache2/conf.d/security. On my Debian server, it is included at the end of the main config file, so if those settings are defined it in, they would override yours.

Yep!

I can change it (with same effect) at 

/etc/apache2/conf.d/security 

or 

/etc/apache2/apache2.conf

I wonder which one is the best admin practice. Asking because I'm new into Apache and Linux and not sure if there is a standard of we got two places because one of them is there for backward compatible issues with older versions or other distros.

Well.. I learned something new today, I guess...

---

### Post by Bachstelze on 2009-08-20
> **jocampo said:**
> Yep!

I can change it (with same effect) at 

/etc/apache2/conf.d/security 

or 

/etc/apache2/apache2.conf

I wonder which one is the best admin practice. Asking because I'm new into Apache and Linux and not sure if there is a standard of we got two places because one of them is there for backward compatible issues with older versions or other distros.

Well.. I learned something new today, I guess...

Change it in /etc/apache2/conf.d/security. The basic idea behind it is that instead of having one, long config file, you have several small ones, dealing with particular aspects of the configuration (in this case, security).

---

### Post by jocampo on 2009-08-20
> **HymnToLife said:**
> Change it in /etc/apache2/conf.d/security. The basic idea behind it is that instead of having one, long config file, you have several small ones, dealing with particular aspects of the configuration (in this case, security).

Thanks! I'll follow the advice ;-)

---

