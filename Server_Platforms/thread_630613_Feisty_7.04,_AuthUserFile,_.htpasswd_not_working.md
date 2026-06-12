---
title: "Feisty 7.04, AuthUserFile, .htpasswd not working"
date: 2007-12-03
forum: Server Platforms
---

### Post by stugots on 2007-12-03
This was working on our system in dapper and edgy, but upgrading to feisty broke it.

My site uses Django, and I've password-protected the site's admin interface. Since I upgraded to feisty, apache doesn't pop up a login window and instead immediately decides that the user doesn't have access.

I've tried commenting out the 4 authorization directives (see below), and the site's behavior changes, so I know the <Location> container is being correctly parsed for the admin URL.  

In my config file I have this:

    <Location "/">
        SetHandler python-program
        PythonPath "['/u/django'] + sys.path"
        PythonHandler django.core.handlers.modpython
        SetEnv DJANGO_SETTINGS_MODULE webcode.settings
        PythonInterpreter webcode
        AddOutputFilterByType DEFLATE text/css
        AddOutputFilterByType DEFLATE text/plain
        AddOutputFilterByType DEFLATE text/xml
        AddOutputFilterByType DEFLATE text/html
        AddOutputFilterByType DEFLATE application/xml
        AddOutputFilterByType DEFLATE application/xhtml+xml
        AddOutputFilterByType DEFLATE application/rss+xml
        AddOutputFilterByType DEFLATE application/atom+xml
        AddOutputFilterByType DEFLATE application/ms*
        AddOutputFilterByType DEFLATE application/vnd*
        AddOutputFilterByType DEFLATE application/postscript
        AddOutputFilterByType DEFLATE application/x-javascript
    </Location>
    <Location "/hidden_admin_url">
        AuthType Basic
        AuthName "Mice Only"
        AuthUserFile /etc/apache2/.htpasswd
        Require valid-user
        AddOutputFilterByType DEFLATE text/css
        AddOutputFilterByType DEFLATE text/plain
        AddOutputFilterByType DEFLATE text/xml
        AddOutputFilterByType DEFLATE text/html
        AddOutputFilterByType DEFLATE application/xml
        AddOutputFilterByType DEFLATE application/xhtml+xml
        AddOutputFilterByType DEFLATE application/rss+xml
        AddOutputFilterByType DEFLATE application/atom+xml
        AddOutputFilterByType DEFLATE application/ms*
        AddOutputFilterByType DEFLATE application/vnd*
        AddOutputFilterByType DEFLATE application/postscript
        AddOutputFilterByType DEFLATE application/x-javascript
    </Location>


/etc/apache2/.htpasswd exists.

The loaded modules are:
root@co2:/etc/apache2# apache2ctl -t -D DUMP_MODULES
apache2: Could not reliably determine the server's fully qualified domain name, using co2.trenchmice.com for ServerName
Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 mpm_prefork_module (static)
 http_module (static)
 so_module (static)
 alias_module (shared)
 auth_basic_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_host_module (shared)
 autoindex_module (shared)
 cgi_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 expires_module (shared)
 include_module (shared)
 mime_module (shared)
 python_module (shared)
 negotiation_module (shared)
 php5_module (shared)
 rewrite_module (shared)
 setenvif_module (shared)
 status_module (shared)
Syntax OK
root@co2:/etc/apache2#


I've reduce the logging level to "warn", but there's nothing in the apache logs that hints at the problem.  apache2ctl config-test says:

root@co2:/etc/apache2# apache2ctl configtest
apache2: Could not reliably determine the server's fully qualified domain name, using co2.trenchmice.com for ServerName
Syntax OK

We've had that "count not reliably" message for over a year now...


I've gone around and around on this and my head is bloody from hitting up against the wall for days.  I'm at wit's end.  Can anyone suggest ways I can debug this authentication problem?

Thanks!

---

### Post by bnuytten on 2007-12-15
Solution for the "Could not reliably determine the server's FQDN": put the following line your /etc/apache2/httpd.conf and reload apache
```

ServerName co2.trenchmice.com

```

---

