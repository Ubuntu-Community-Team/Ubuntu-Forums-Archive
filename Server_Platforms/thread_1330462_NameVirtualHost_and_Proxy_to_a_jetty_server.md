---
title: "NameVirtualHost and Proxy to a jetty server"
date: 2009-11-18
forum: Server Platforms
---

### Post by ildella on 2009-11-18
hi everyone. 

I have a NameVirtualHost *:80 
one VirtualHost working that allow me to have a wordpress site

[http://danieledellafiore.net/](http://danieledellafiore.net/)

and two applications running on jetty with a proxy:
[http://danieledellafiore.net/artivio/](http://danieledellafiore.net/artivio/)
[http://danieledellafiore.net/newsletter/](http://danieledellafiore.net/newsletter/)

Now I want the first app to run on its own domain, artivio.com
Here is the config and you can see result here: [http://artivio.com/](http://artivio.com/)

<VirtualHost *:80>

        ServerName artivio.com
        ProxyRequests Off
        ProxyPreserveHost Off

        <Proxy *>
            Order deny,allow
            Allow from all
        </Proxy>

        ProxyPass / [http://localhost:8080/artivio](http://localhost:8080/artivio)
        ProxyPassReverse / [http://localhost:8080/artivio](http://localhost:8080/artivio)

</VirtualHost>

If I change the ProxyPass and ProxyPassReverse to
/artivio [http://localhost:8080/artivio](http://localhost:8080/artivio)

the app start answering at 
[http://artivio.com/artivio/](http://artivio.com/artivio/)

which is correct. I think that apache config is correct, I wonder is a problem about jetty that have the applications mapped to a specific context. 
I think I should manage to make that application answer on :8080/ but only one while I would like to make many applications run on the same jetty instance with different domains. 

Any advice?

---

