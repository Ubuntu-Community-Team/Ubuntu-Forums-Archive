---
title: "Apache mod_proxy error"
date: 2010-10-26
forum: Server Platforms
---

### Post by pablovg2 on 2010-10-26
I have a problem with a Ubuntu Server and Apache mod_proxy, here is my configuration:

Ubuntu server network conf:

ifconfig
10.0.2.5 eth0
10.9.52.33 eth1

route
default             10.9.52.32         UG    100    0        0 eth0

Ubuntu server, Apache conf:

<VirtualHost *:80>
ServerName domain_public

RewriteEngine On
RewriteRule ^/$ /ecm/ [R,L]
ProxyPass /ecm/ [http://10.0.2.8:8080/ecm/](http://10.0.2.8:8080/ecm/)
ProxyPassReverse /ecm/ [http://10.0.2.8:8080/ecm/](http://10.0.2.8:8080/ecm/)
ProxyRequests Off
 <proxy *>
    Order deny,allow
    Allow from all
  </proxy>
ErrorLog /var/log/apache2/error.ecm.log
</VirtualHost>


My log error:


[Tue Oct 26 22:37:11 2010] [error] (70007)The timeout specified has expired: proxy: prefetch request body failed to 10.0.2.8:8080 (10.0.2.8 ) from ip_userclient_web ()
[Tue Oct 26 22:37:34 2010] [error] (70007)The timeout specified has expired: proxy: prefetch request body failed to 10.0.2.8:8080 (10.0.2.8 ) from ip_userclient_web ()
[Tue Oct 26 22:45:34 2010] [error] (104)Connection reset by peer: proxy: prefetch request body failed to 10.0.2.8:8080 (10.0.2.8 ) from ip_userclient_web ()
[Tue Oct 26 22:45:36 2010] [error] (70007)The timeout specified has expired: proxy: prefetch request body failed to 10.0.2.8:8080 (10.0.2.8 ) from ip_userclient_web ()


Any idea???

---

### Post by SeijiSensei on 2010-10-26
Looks like it can't see the other webserver.  If you open a browser on the box running the proxy and visit [http://10.0.2.8:8080/](http://10.0.2.8:8080/), can you connect?

---

### Post by pablovg2 on 2010-10-26
Yes I can. And the proxy look run good, but when i try to upload something, like a document, i get this error.

If it help, i have a nuxeo on the host: [http://10.0.2.8:8080/ecm/](http://10.0.2.8:8080/ecm/)  and it run perfectly on the internal network. 

Even in my pc with IP 10.0.2.15 (Internal network) I can work  perfectly with the domain_public, because i have put on the file /etc/hosts the server ip

#hosts file on PC
domain_public  10.0.2.5 

The problem is when a user try to upload something from the outside of the network.

---

### Post by SeijiSensei on 2010-10-26
Other people seem to have this problem with large POST payloads and mod_proxy.  I didn't see any answers, though.  Take at look at [these results from a Google search]("http://www.google.com/search?client=ubuntu&channel=fs&q=prefetch+request+body+failed").

---

### Post by pablovg2 on 2010-10-29
I cant make it running. I have tried all combination of directives of Mod_Proxy but when i try to upload a file bigger than 400KB it faild, and I get this error:

[Fri Oct 29 23:12:45 2010] [error] (70007)The timeout specified has expired: proxy: prefetch request body failed to 10.0.2.8:8080 (10.0.2.8:) from 87.232.45.48 ()
[Fri Oct 29 23:14:01 2010] [error] (104)Connection reset by peer: proxy: prefetch request body failed to 10.0.2.8:8080 (10.0.2.8:) from 87.232.45.48 ()

**87.232.45.48  is my public IP outside server proxy

Any alternative to don´t use Apache mod_proxy???

---

### Post by SeijiSensei on 2010-10-29
Are you using mod_proxy to forward requests for specific virtual hosts while serving the rest from the Apache server itself?  Or are you actually forwarding all requests on port 80 to 10.0.2.8:8080?  If the latter, you could just use a plain TCP proxy or use port forwarding in iptables.

This /ecm/ rewriting is an annoyance, though. Are there multiple virtual hosts running on 10.0.2.8:8080? Perhaps you could run another server instance on a different port on 10.0.2.80 to which requests can be sent.  Without knowing more than I probably want to about your internal arrangements I can't really answer your question.  It does look like mod_proxy is not the solution, though.

---

### Post by pablovg2 on 2010-10-30
I am using mod_proxy to forward only  for specific virtual host, i have serveral virtualhosts. So the only way to dont use mod_proxy it would be using a different port to forwarding in iptables, no?

---

### Post by SeijiSensei on 2010-10-30
Yes.  

You might want to dig deeper than I did into the reported problems with mod_proxy and large POST payloads.  I can't say I looked very deeply into the subject, just enough to see that others had reported this problem.  Maybe there's some tweak that will solve your problem.

---

### Post by Vegan on 2010-10-30
Might be an idea to just use simple forwarding to the desired URL.

Apache2 supports that idea fine.

---

