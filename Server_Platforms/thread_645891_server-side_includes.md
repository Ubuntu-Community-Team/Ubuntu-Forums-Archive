---
title: "server-side includes"
date: 2007-12-20
forum: Server Platforms
---

### Post by bfkeats on 2007-12-20
I just switched my server from gentoo to ubuntu. I can't seem to get server side includes to work however. According to [this]("http://httpd.apache.org/docs/2.2/howto/ssi.html"), I need to do two things:

1. Add  Options +Includes to an .htaccess file or httpd.conf (I've tried both).

2 Add the following directives. 

 AddType text/html .shtml
AddOutputFilter INCLUDES .shtml

...which already seem to be set in mods-enabled/mime.conf and mods-avaliable/mime.conf.

The relevant line of code in index.shtml is,
```
<!--#include virtual="primarynav.shtml"-->
```

The error in the apache log is,
```
[Thu Dec 20 19:22:18 2007] [error] an unknown filter was not added: includes
```

Am I missing something here? Does ubuntu have some special appache configuration that overrides these docs?

---

### Post by FakeOutdoorsman on 2007-12-20
Depending on how Apache is configured you may need to add something like the following to your Apache config file:
```
LoadModule include_module modules/mod_include.so
```

or more likely you just need to enable the module:
```
sudo a2enmod include
```

Now restart Apache:
```
sudo /etc/init.d/apache2 force-reload
```

---

### Post by bfkeats on 2007-12-21
Enabling the module worked. Thanks you're a prince!

---

