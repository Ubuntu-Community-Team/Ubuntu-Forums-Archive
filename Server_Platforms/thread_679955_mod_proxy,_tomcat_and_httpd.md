---
title: "mod_proxy, tomcat and httpd"
date: 2008-01-27
forum: Server Platforms
---

### Post by Cowloon on 2008-01-27
I have a servlet running on tomcat 5.5 at [http://localhost:8082/testserv](http://localhost:8082/testserv), which works. I want to have apache httpd 2.2 act as a proxy, so that I can load the servlet as [http://localhost/testserv](http://localhost/testserv).

So, I've enabled proxy.conf proxy.load and proxy_ajp.load modules.

In proxy.conf I've changed Deny from all to Allow from all in the <Proxy *>...</Proxy> directive, and at the end, before </IfModule>, I've added:

ProxyPass /testserv [http://localhost:8082/testserv](http://localhost:8082/testserv)
ProxyPassReverse /testserv [http://localhost:8082/testserv](http://localhost:8082/testserv)

And I've restarted apache2.

Now if I try to load [http://localhost/testserv](http://localhost/testserv) I get 403 forbidden.

/var/log/apache2/error.log says:

proxy: No protocol handler was valid for the URL /testserv/. If you are using a DSO version of mod_proxy, make sure the proxy submodules are included in the configuration using LoadModule.

But, I have proxy.load and proxy_ajp.log symlinked in mods-available.

Do you know what the problem can be?

---

