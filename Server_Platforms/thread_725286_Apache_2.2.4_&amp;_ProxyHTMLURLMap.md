---
title: "Apache 2.2.4 &amp; ProxyHTMLURLMap"
date: 2008-03-15
forum: Server Platforms
---

### Post by chris.zeman on 2008-03-15
I'm using the Reverse Proxy function to forward all requests to URL sub.domain.net to an internal web server, but Apache complains about my ProxyHTMLURLMap directives. I hope there's an answer. :)

Loaded Modules:```
root@automation:/etc/apache2/mods-enabled# dir
alias.conf            cgi.load          negotiation.load     setenvif.conf
alias.load            deflate.conf      php5.conf            setenvif.load
auth_basic.load       deflate.load      php5.load            ssl.conf
authn_file.load       dir.conf          proxy_ajp.load       ssl.load
authz_default.load    dir.load          proxy_balancer.load  status.conf
authz_groupfile.load  env.load          proxy.conf           status.load
authz_host.load       headers.load      proxy_connect.load   suexec.load
authz_user.load       include.load      proxy_ftp.load       userdir.conf
autoindex.conf        mime.conf         proxy_http.load      userdir.load
autoindex.load        mime.load         proxy.load
cache.load            negotiation.conf  rewrite.load
```

Virtual Host File:```
<VirtualHost *>
    ServerName  http://sub.domain.net
ProxyPass / http://172.16.1.20/
ProxyPassReverse / http://172.16.1.20/
ProxyHTMLURLMap http://172.16.1.20/ /
<Location />
ProxyPassReverse /
    SetOutputFilter     proxy-html
    ProxyHTMLURLMap     /    /
    ProxyHTMLURLMap     /    /
    RequestHeader      unset    Accept-Encoding
</Location>
ProxyRequests Off
<Proxy *>
Order deny,allow
Allow from all
</Proxy>
</VirtualHost>
```

Everything appears to match what I find in the tutorials, but Apache complains when I try to apply the changes. ```
Syntax error on line 5 of /etc/apache2/sites-enabled/sub.domain.net.conf:
Invalid command 'ProxyHTMLURLMap', perhaps misspelled or defined by a module not included in the server configuration
```

I'm running Apache 2.2.4 on Ubuntu Server 7.10. The proxy works if I comment out the ProxyHTMLURLMap directives, but there is another problem that I don't believe is related and I want to just rule it out. The internal server is running a program called HFS. HFS is a single executable file that allows access to files on the local machine via a web page. The images are within the executable itself, and are served as ```
http://sub.domain.net/~image.jpg
```. I know the '~' is the problem, but the gentleman who writes HFS has shown little interest in changing how HFS serves images.

Thank you,
Chris

---

### Post by jasoneth on 2008-03-22
> **chris.zeman said:**
> I'm using the Reverse Proxy function to forward all requests to URL sub.domain.net to an internal web server, but Apache complains about my ProxyHTMLURLMap directives. I hope there's an answer. :)
I ran into exactly the same problem. The solution turned out to be counter-intuitive (at least to me):

```
# apt-get install libapache2-mod-proxy-html
```

As far as I could tell, mod_proxy_html had been installed along with the apache2 package (/usr/lib/apache2/modules/mod_proxy_html.so existed, proxy_html.load was in /etc/apache2/mods-available). However, until I explicitly installed it, any use of its directives (such as ProxyHTMLURLMap) would cause Apache to fail to start.

---

### Post by chris.zeman on 2008-03-22
Hi jasoneth,

Thanks for that info! I'm sorry to say, though, that it didn't do the trick. I suspect the problem is how the image is being served. ```
<a href="~login" class="button"><img src="/~img27"> LOGIN</a>
```
The strange thing, however, is that the login link works just fine. I click on LOGIN and it opens a login window. :confused:

Thank you,
Chris

---

### Post by chris.zeman on 2008-05-04
I upgraded my server to 8.04, and now it works. :confused: I won't complain. I just won't complain. lol

Chris

---

