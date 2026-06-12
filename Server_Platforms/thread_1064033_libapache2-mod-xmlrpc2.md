---
title: "libapache2-mod-xmlrpc2"
date: 2009-02-08
forum: Server Platforms
---

### Post by mrlinus on 2009-02-08
I've been using Wtorrent for a while with a source compiled setup of Apache2, which requires XMPRC. Recently switched to an apt-get installation of Apache2 and hence installed libapache2-mod-xmlrpc2, which resulted in apache returning the following error when I try to start it:

```

Syntax error on line 185 of /etc/apache2/apache2.conf: 
Syntax error on line 1 of /etc/apache2/mods-enabled/xmlrpc.load: 
Cannot load /usr/lib/apache2/modules/mod_xmlrpc.so into server: 
/usr/lib/apache2/modules/mod_xmlrpc.so: 
undefined symbol: xmlrpc_registry_new

```

If I do disable xmlrpc-mod it works fine, but since I need to use it, it's not really an option.

Any way to fix this error?

---

