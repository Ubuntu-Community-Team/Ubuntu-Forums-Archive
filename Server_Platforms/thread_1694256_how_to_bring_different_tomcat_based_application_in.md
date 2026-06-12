---
title: "how to bring different tomcat based application in same Apache vhost in same URL"
date: 2011-02-24
forum: Server Platforms
---

### Post by tapas_mishra on 2011-02-24
I basically  have 2 applications
[http://sakai.openitup.in](http://sakai.openitup.in)  
[http://olat.openitup.in](http://olat.openitup.in)  

The working configuration of apache vhost for sakai.openitup.in
> 
    <VirtualHost *:80 >
    
           ServerName sakai.openitup.in
           ProxyPass / ajp://192.168.1.14:8009/
           ProxyPassReverse / ajp://192.168.1.14:8009/
    
    </VirtualHost>

and for olat another apache2 vhost (working configuration)

>     <VirtualHost *:80 >
    
           ServerName olat.openitup.in
           ProxyPass / ajp://192.168.1.15:8009/
           ProxyPassReverse / ajp://192.168.1.15:8009/
    
    </VirtualHost>

then things work.

But if I want both sakai and olat to be accessible at research.openitup.in/sakai and 
research.openitup.in/olat  for this  I modified the virtual host definition of research.openitup.in as follows

>     <VirtualHost *:80 >
           ServerName research.openitup.in
    
    ProxyPass /sakai ajp://192.168.1.14:8009/
    ProxyPassReverse /sakai ajp://192.168.1.14:8009/
    
    ProxyPass /olat ajp://192.168.1.15:8009/
    ProxyPassReverse /olat ajp://192.168.1.15:8009/
    
    
    ProxyPass / [http://192.168.1.14](http://192.168.1.14)
    ProxyPassReverse  / [http://192.168.1.14](http://192.168.1.14)
    </VirtualHost>

then
[http://research.openitup.in/sakai](http://research.openitup.in/sakai)  
[http://research.openitup.in/olat](http://research.openitup.in/olat)
are not accessible.

If you notice I have forwarded root of research.openitup.in to an internal
machine.Which is where it actually is so ProxyPass / for research.openitup.in is needed.

In this situation what can be a possible solution for me so that I can access
[http://research.openitup.in/sakai](http://research.openitup.in/sakai)
and not [http://sakai.openitup.in](http://sakai.openitup.in) and same for olat
[http://research.openitup.in/olat](http://research.openitup.in/olat)
and not [http://olat.openitup.in](http://olat.openitup.in)


All this is done on a Ubuntu server.

---

