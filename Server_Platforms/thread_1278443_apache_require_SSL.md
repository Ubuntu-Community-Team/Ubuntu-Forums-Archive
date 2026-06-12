---
title: "apache require SSL"
date: 2009-09-29
forum: Server Platforms
---

### Post by cdenley on 2009-09-29
I'm trying to configure a directory so users on the LAN can access without a password, then everyone else will need to authenticate. Of course, I want to require SSL encryption before they are prompted to send their password in plain text. If LAN requests require SSL as well, then I can live with that.
```

SSLOptions +StrictRequire
SSLRequireSSL
AuthName "My Directory"
AuthType Basic
AuthUserFile /etc/apache2/auth/myfile
require valid-user
Order deny,allow
Deny from all
Allow from 192.168.0.
Satisfy Any

```
When I attempt to access the page from outside the LAN, I am required to authenticate, but not required to use SSL! Shouldn't this work?
[http://httpd.apache.org/docs/2.2/mod/mod_ssl.html#ssloptions](http://httpd.apache.org/docs/2.2/mod/mod_ssl.html#ssloptions)
> 
# StrictRequire

This forces forbidden access when SSLRequireSSL or SSLRequire successfully decided that access should be forbidden. Usually the default is that in the case where a ``Satisfy any'' directive is used, and other access restrictions are passed, denial of access due to SSLRequireSSL or SSLRequire is overridden (because that's how the Apache Satisfy mechanism should work.) But for strict access restriction you can use SSLRequireSSL and/or SSLRequire in combination with an ``SSLOptions +StrictRequire''. Then an additional ``Satisfy Any'' has no chance once mod_ssl has decided to deny access.


---

### Post by cdenley on 2009-09-30
[https://issues.apache.org/bugzilla/show_bug.cgi?id=45801](https://issues.apache.org/bugzilla/show_bug.cgi?id=45801)

I resorted to configuring access in the SSL and default vhost separately, and now it works perfectly. I would have preferred an .htaccess solution.

default
```

<Directory /var/www/mydir/>
       ErrorDocument 403 https://www.mydomain.com/mydir/
       Order deny,allow
       Deny from all
       Allow from 192.168.0.
</Directory>

```

ssl
```

<Directory /var/www/mydir/>
        AuthName "My Encrypted Internet Page"
        AuthType Basic
        AuthUserFile /etc/apache2/auth/myfile
        require valid-user
</Directory>

```

---

