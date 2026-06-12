---
title: "Invalid command 'ProxyHTMLEnable', perhaps misspelled or defined by a module not incl"
date: 2010-07-18
forum: Server Platforms
---

### Post by tapas_mishra on 2010-07-18
I am getting following error

"Invalid command 'ProxyHTMLEnable', perhaps misspelled or defined by a
module not included in the server configuration"

Saw this [thread]("http://ubuntuforums.org/showthread.php?t=1395586")

in /etc/apache2/mods-enabled/
I see
```

alias.conf       authz_default.load    autoindex.conf  deflate.conf
dump_io.load  mime.load         proxy.conf       proxy.load
setenvif.conf
alias.load       authz_groupfile.load  autoindex.load  deflate.load
env.load      negotiation.conf  proxy_html.conf  reqtimeout.conf
setenvif.load
auth_basic.load  authz_host.load       cgid.conf       dir.conf
jk.load       negotiation.load  proxy_html.load  reqtimeout.load
status.conf
authn_file.load  authz_user.load       cgid.load       dir.load
mime.conf     proxy_ajp.load    proxy_http.load  rewrite.load
status.load

```
and in /etc/apache2/apache2.conf
```

Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

```

If you see above output of directory it seems that proxy_html is on.

Vhost definition where I did this
```

<VirtualHost *:80>

       ServerAdmin webmaster@localhost
       ServerName site4
       ProxyRequests off
       <Proxy *>
       Order deny,allow
       Allow from all
       </Proxy>
       ProxyPreserveHost Off
 ProxyPass /site4   http://myinternal.server.in
       ProxyHTMLURLMap http://myinternal.server.in

 <Location /site4/>
       ProxyPassReverse http://myinternal.server.in
       ProxyHTMLEnable On
       ProxyHTMLURLMap / /site4/
       RequestHeader unset Accept-Encoding
       </Location>

</VirtualHost>

```

---

### Post by theozzlives on 2010-07-18
You sure it's not supposed to be ```
ProxyHTML Enable
``` notice the space. Just a thought.

---

### Post by tapas_mishra on 2010-07-18
Yes I am sure I checked.Just after your reply and it gave following 
```


Invalid command 'ProxyHTML', perhaps misspelled or defined by a module not included in the server configuration

```

---

### Post by tapas_mishra on 2010-07-18
Finally solved the problem.
[http://apache.webthing.com/mod_proxy_html/config.html](http://apache.webthing.com/mod_proxy_html/config.html)
On the above link version 3.0.1 of libapache2-mod-proxy-html does not use ProxyHTMLEnable instead uses ProxyHTMLInterp On|Off

so this problem is coming.
Ubuntu 10.04 by default uses 
libapache2-mod-proxy-html of version 3.0.1
Changed the ProxyHTMLEnable to
ProxyHTMLInterp
and the error was resolved.
you can check it ```

dpkg -s libapache2-mod-proxy-html
```

---

### Post by levicivita on 2010-11-29
Very helpful, thanks!

---

