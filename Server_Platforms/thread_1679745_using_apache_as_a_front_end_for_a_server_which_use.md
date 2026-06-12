---
title: "using apache as a front end for a server which uses tomcat"
date: 2011-02-01
forum: Server Platforms
---

### Post by jamesbon on 2011-02-01
I have a server on which there is an LMS known as Sakai running.
Internally (i.e. on LAN) I can access it [http://192.168.1.4:8080/portal](http://192.168.1.4:8080/portal)
but when from internet some one tries to reach it 
the site is in accessible.

Server where Apache is running and where sakai is running are two physically different servers.
Following is Apache vhost conf of server which faces internet.

```

<VirtualHost *:80>
        ServerName someserver
        ProxyRequests off
        <Proxy *>
        Order deny,allow
        Allow from all
        </Proxy>

        ProxyPass /portal http://192.168.1.4:8080/portal
        ProxyPassReverse /portal http://192.168.1.4:8080/portal

 
       ProxyPass / http://192.168.1.4/
       ProxyPassReverse / http://192.168.1.4/

</VirtualHost>

```As per instructions given on this page

[https://confluence.sakaiproject.org/display/~steve.swinsburg]("https://confluence.sakaiproject.org/display/%7Esteve.swinsburg/Fronting+Tomcat+with+Apache+via+mod_proxy_ajp")
[/Fronting+Tomcat+with+Apache+via+mod_proxy_ajp]("https://confluence.sakaiproject.org/display/%7Esteve.swinsburg/Fronting+Tomcat+with+Apache+via+mod_proxy_ajp")

I am not clear with 2 things
1) Point no 5
2) Point no 7

the confusion is in ajp.conf and what should I use in vhost configuration.I have defined ajp.conf on server facing internet.

Point no 5 of URL says to use
```

ProxyPass / ajp://localhost:8009/
ProxyPassReverse / ajp://localhost:8009/

```

in my case the server on which Apache is running and the server where
Sakai is are physically different machines.
So my guess is I should replace localhost by IP of machine where sakai
(tomcat) instance is running.Is that correct?

Second I am not clear with point no 7 of URL.
Which says

"Once again, ensure you have the line in httpd.conf that is going to
load this ajp.conf file."

here is it referring to the Apache vhost file or apache2.conf I am
having a Ubuntu server which does not have httpd.conf What I till now
have understood the server which faces the internet I should have some
thing defined in Apache vhost on that server.
Correct me if I am wrong.
The above configuration is server on which Apache is running and
mod_proxy_ajp of Apache is configured
I have created a file named ajp.conf but not clear with the entries.

This is the site [http://research.openitup.in/portal](http://research.openitup.in/portal)

---

