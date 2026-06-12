---
title: "Virtual hosts with rewrite problems"
date: 2011-06-28
forum: Server Platforms
---

### Post by norjms on 2011-06-28
I'm having problems configuring my virtual hosts file properly
The site [http://server.com](http://server.com) opens on http and https
The site 10.0.1.3/myapp/ works
I am trying to redirect all traffic from [http://server.com/myapp/](http://server.com/myapp/)
to [http://10.0.1.3:8080/myapp/](http://10.0.1.3:8080/myapp/) while maintaining access to [http://server.com](http://server.com)

```

<VirtualHost *:80>
  ServerAdmin norjms@server.com
  ServerName server.com
  ServerAlias www.server.com

  # Indexes + Directory Root.
  DocumentRoot "/var/www/server.com/public_html"
  DirectoryIndex index.html

  <Directory "/var/www/server.com">
    AllowOverride All
    Allow from All
  </Directory>

  # Logfiles
  ErrorLog /var/www/server.com/logs/error.log
  CustomLog /var/www/server.com/logs/access.log combined
<Location /myapp>
order deny,allow
deny from all
allow from all
ProxyPass http://10.0.1.3:8080/myapp
ProxyPassReverse http://10.0.1.3:8080/myapp
</Location>
</VirtualHost>

```

I am at a loss and I looked all over google for answers, but didn't find the answer.

---

### Post by falko on 2011-06-29
Have you tried to use mod:rewrite instead?

[http://httpd.apache.org/docs/2.0/misc/rewriteguide.html](http://httpd.apache.org/docs/2.0/misc/rewriteguide.html)

---

### Post by SeijiSensei on 2011-06-29
Use this on server.com

```

Redirect /myapp/     http://10.0.1.3:8080/myapp/

```

That presumes visitors can see 10.0.1.3; if not then, you've got to futz with reverse proxies as you are trying to do now.

I think the problem with your current setup is the "deny from all" directive.  Since you don't seem to care about controlling access by IP address or remote host name, get rid of all that and just use:

```

<Location /myapp>
ProxyPass http://10.0.1.3:8080/myapp
ProxyPassReverse http://10.0.1.3:8080/myapp
</Location>

```

Does that work?

---

