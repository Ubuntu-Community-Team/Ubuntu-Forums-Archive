---
title: "Apache Reverse Proxy Errors"
date: 2007-08-20
forum: Server Platforms
---

### Post by GTHvidsten on 2007-08-20
Hi,

I've set up a reverse proxy on my Apache2, but I keep getting these errors in the error.log:

```

[Mon Aug 20 22:47:09 2007] [error] [client 192.168.1.3] proxy: error reading status line from remote server 192.168.1.2
[Mon Aug 20 22:47:09 2007] [error] [client 192.168.1.3] proxy: Error reading from remote server returned by /default.aspx
[Mon Aug 20 22:47:18 2007] [error] [client 192.168.1.3] Error in bucket read

```

And this error in the web browser:

```

[SIZE="4"]**Proxy Error**[/SIZE]

The proxy server received an invalid response from an upstream server.
The proxy server could not handle the request *GET /default.aspx*.

Reason: **Error reading from remote server**

```

The info in the access log that prompted the error:

```

192.168.1.3 - - [20/Aug/2007:22:47:18 +0200] "GET /default.aspx HTTP/1.1" 200 2131

```

As you can probably see I'm trying to get a subdomain be redirected to an IIS server, instead of redirecting just a directory on another subdomain. This is what I have in my website configuration file in /etc/apache2/sites-available:

```

<VirtualHost *>
        ServerName sub.mydomain
        ServerAdmin webmaster@mydomain
        DocumentRoot /path/I/dont/think/is/used/for/anything/
        ProxyRequests Off
        ProxyPass / [http://192.168.1.2/](http://192.168.1.2/)
        ProxyPassReverse / [http://192.168.1.2/](http://192.168.1.2/)
        SetOutputFilter  proxy-html
        ProxyHTMLURLMap  [http://192.168.1.2/](http://192.168.1.2/)  /
        RequestHeader    unset  Accept-Encoding
        CustomLog "|/usr/sbin/rotatelogs /var/log/apache2/sub.mydomain.access.log 5M" common
</VirtualHost>

```

Can anybody please help me figure out what's wrong?

---

### Post by EvanWill on 2007-08-21
Look at the following thread:

[http://www.mindquarry.com/forum/comments.php?DiscussionID=206&Focus=1128#Comment_1128](http://www.mindquarry.com/forum/comments.php?DiscussionID=206&Focus=1128#Comment_1128)

Seems as if one must be specific as to what port Apache listens on.

I changed my http.conf from

Listen 80
 
to 

Listen <IP Address>:80

---

### Post by GTHvidsten on 2007-08-23
I changed my as well from

VirtualHost *

to

VirtualHost <IP Address>:80

but that didn't help.

---

### Post by jasoneth on 2008-03-22
(Seems to be the same problem that I posted a solution to [here](http://ubuntuforums.org/showpost.php?p=4567944&postcount=2); reproduced below.)

> **chris.zeman said:**
> I'm using the Reverse Proxy function to forward all requests to URL sub.domain.net to an internal web server, but Apache complains about my ProxyHTMLURLMap directives. I hope there's an answer. :)
I ran into exactly the same problem. The solution turned out to be counter-intuitive (at least to me):

```
# apt-get install libapache2-mod-proxy-html
```

As far as I could tell, mod_proxy_html had been installed along with the apache2 package (/usr/lib/apache2/modules/mod_proxy_html.so existed, proxy_html.load was in /etc/apache2/mods-available). However, until I explicitly installed it, any use of its directives (such as ProxyHTMLURLMap) would cause Apache to fail to start.

---

### Post by twistedtwig on 2008-03-25
this may not happen or be relevant but I had issues with using reverse proxy to an iis box inside my network.

I would get random 502 errors:

[http://ubuntuforums.org/showthread.php?t=688156]("http://ubuntuforums.org/showthread.php?t=688156")

basic solution:

SetEnv force-proxy-request-1.0 1
SetEnv proxy-nokeepalive 1

as I say it might help.. it might not

---

