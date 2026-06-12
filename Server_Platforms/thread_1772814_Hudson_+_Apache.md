---
title: "Hudson + Apache"
date: 2011-06-01
forum: Server Platforms
---

### Post by dimas09 on 2011-06-01
Hello!
I installed hudson and I can open it as [http://mydomain.com:8080/](http://mydomain.com:8080/)
but i want setting up apache for opening as [http://mydomain.com:8080/hudson](http://mydomain.com:8080/hudson)
My settings in /etc/apache2/mods-enabled/proxy.conf
```

<IfModule mod_proxy.c>
        #turning ProxyRequests on and allowing proxying from all may allow
        #spammers to use your proxy to send email.

        ProxyRequests Off

        <Proxy *>
                AddDefaultCharset off
                Order deny,allow
                #Deny from all
                Allow from all
                #.liveyurist.ru
        </Proxy>

        RewriteRule       ^/hudson(.*)$  http://mydomain.com:8080/hudson$1 [P,L]
        ProxyPassReverse  /hudson        http://mydomain.com:8080/hudson

        <Proxy http://mydomain.com:8080/hudson*>
          Order deny,allow
          Allow from all
        </Proxy>

        # Enable/disable the handling of HTTP/1.1 "Via:" headers.
        # ("Full" adds the server version; "Block" removes all outgoing Via: headers)
        # Set to one of: Off | On | Full | Block

        ProxyVia On
</IfModule>

```
But I can open hudson with link [http://mydomain.com:8080/hudson](http://mydomain.com:8080/hudson)
Please advice.

---

