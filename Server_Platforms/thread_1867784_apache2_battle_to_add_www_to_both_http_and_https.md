---
title: "apache2 battle to add www to both http and https"
date: 2011-10-23
forum: Server Platforms
---

### Post by pmla on 2011-10-23
Hi,

ufff, I have been fighting this for a week now without success.. and google is not showing anything useful about this.

What I want to accomplish is basically using the RewriteEnine ON and the .htaccess file to add www to all web requests (http and https using SSL). For that I have 2 vhosts files for the domain (80 & 443)

so domain.com rewrites to [www.domain.com](www.domain.com)

Here comes the tricky part... I would like this done for both HTTP and HTTPS requests (port 80 and por 443) I DO NOT WANT TO FORCE SSL :)

so
[http://domain.com](http://domain.com) rewrites to [http://www.domain.com](http://www.domain.com)
and
[https://domain.com](https://domain.com) rewrites to [https://www.domain.com](https://www.domain.com)

So far I can achieve and rewrite http with this code in .htaccess... but the code does not rewrite the https
```

HTTP
RewriteEngine On
RewriteCond %{HTTP_HOST} ^domain\.com
RewriteRule ^(.*)$ http://www.domain.com$1 [R=permanent,L]

```

After a week a reading about this, seems the best way is to use ports for coding .htaccess
```

# Port 80 is http
RewriteCond %{SERVER_PORT} ^80$
# fetch properly escaped host
RewriteCond %{HTTP_HOST} ^domain\.com [NC]
# use existing {REQUEST_URI} for redirect
RewriteRule .? http://www.domain.com%{REQUEST_URI} [R=301,L]

# Port 443 is https
RewriteCond %{SERVER_PORT} ^443$
# fetch properly escaped host
RewriteCond %{HTTP_HOST} ^domain\.com [NC]
# use existing {REQUEST_URI} for redirect
RewriteRule .? https://www.domain.com%{REQUEST_URI} [R=301,L]

```

But again... failure, the http rewrites to www but https does rewrite to www.

Any apache guru around?

---

### Post by pmla on 2011-10-23
Solved

---

