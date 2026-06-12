---
title: "Apache  Proxy Problem"
date: 2010-05-10
forum: Server Platforms
---

### Post by marcio123 on 2010-05-10
I have installed jabber server on ubuntu 9.10 (ejabberd). I had written JS client (JsJac) which needs http-binding to work. 

All worked on WAMP in XP. WAMP had proxy to virtual UBUNTU where I had Jabber.

Now I don't have XP and I want to do it on Ubuntu.

In /etc/apache2/mods-enabled/proxy.conf I have

IfModule mod_proxy.c>
        #turning ProxyRequests on and allowing proxying from all may allow
        #spammers to use your proxy to send email.

        ProxyRequests Off

        <Proxy *>
                Order deny,allow
                Deny from all
                #Allow from .example.com
        </Proxy>
 ProxyPass /http-bind/ [http://localhost:5280/http-bind/](http://localhost:5280/http-bind/)
 ProxyPassReverse /http-bind/ [http://localhost:5280/http-bind/](http://localhost:5280/http-bind/)


        # Enable/disable the handling of HTTP/1.1 "Via:" headers.
        # ("Full" adds the server version; "Block" removes all outgoing Via: he$
        # Set to one of: Off | On | Full | Block

        ProxyVia On
</IfModule>

When I go to  DOMAIN/http-bind I get 403 Frobidden. 

If I change Deny from all to allow from all I get Internal Gateway Error. 

Any ideas ?





EDIT

I needed to add proxy_http module.

---

