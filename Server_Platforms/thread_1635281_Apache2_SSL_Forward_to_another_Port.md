---
title: "Apache2 SSL Forward to another Port"
date: 2010-12-01
forum: Server Platforms
---

### Post by TheFuzz4 on 2010-12-01
So here is what I am trying to do.
I have an apache2 server on a Debian box that I am using as the reverse proxy for my sites that are sitting behind it and everyone is happy.  But now I want to be able to access my vmware server console from outside the network without exposing the vmware server port to the internet. So I did this I created a new virtual host for apache and it looks like this (edited for the real world)

```

<VirtualHost *:80>
ServerName server.my.domain
   # RewriteLog "/var/log/apache2/rewrite.log"
   # RewriteLogLevel 9
   SSLProxyEngine On
   ProxyPreserveHost On
   #RewriteEngine     On
   #RewriteRule       ^(.*)$        https://vmware.my.domain$1
   ProxyPass / https://server.my.domain:8333/
   ProxyPassReverse / https://server.my.domain:8333/
ServerAlias vmware.my.domain
</VirtualHost>

```

So here is what I want to be able to do.  I want to be able to punch in [https://vmware.my.domain](https://vmware.my.domain) and have the reverse proxy just take care of everything else without having to punch in the port number or anything else.  I'd also like to have if possible the ssl on the vmware box just pass through the proxy back to the end user.  If that isn't possible and I need to create a new ssl for the apache box then that is ok too.  I have googled this and looked at several other sites but I'm still a little bit lost.  I'm making progress on this as I keep getting different errors but I'm kinda stuck scratching my head right now.  Thank you in advance for your help with this.

---

### Post by SeijiSensei on 2010-12-02
Create separate <VirtualHost> containers for server.my.domain and vmware.my.domain that do what you want.  Remove the ServerAlias above.

---

### Post by numeric_way on 2010-12-03
> **TheFuzz4 said:**
>   I want to be able to punch in [https://vmware.my.domain](https://vmware.my.domain) 
Just adding a precision to seigi's, if you want that you must have <VirtualHost *:443> in your second virtual host for vmware

---

