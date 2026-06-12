---
title: "Links don't work with an Apache Reverse Proxy"
date: 2009-09-03
forum: Server Platforms
---

### Post by icarius on 2009-09-03
I am trying to configure a reverse proxy using Apache. I can get the reverse proxy to partially work where it forwards the directory. I.E. When I connect to [http://oso/gis/](http://oso/gis/) it correctly forwards to my backend server which is located at [http://antero/services](http://antero/services). However, when I click on a link, it rewrites the entire url and I get a "Not Found" error. 

This is what I have in my configuration file:

        ProxyRequests Off
        <Proxy *>
               Order deny,allow
        </Proxy>

        ProxyPass /gis/ [http://antero/services](http://antero/services)
        ProxyPassReverse /gis/ [http://antero/services](http://antero/services)

Any help on this would be greatly appreciated!

---

### Post by Waappu on 2009-09-07
Hi

Try this
```

        <IfModule mod_proxy.c>
                ProxyPreserveHost       Off
                ProxyRequests           Off

                <Location /gis>

                        Options None
                        Order allow,deny
                        allow from all

                        ProxyPass http://antero/services
                        ProxyPassReverse http://antero/services

                </Location>
        </IfModule>

```

---

