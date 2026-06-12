---
title: "reconfiguring .htaccess for vhost on 14.04"
date: 2017-06-14
forum: Server Platforms
---

### Post by Drone4four on 2017-06-14
I recently nuked my apache vhost configuration files and started fresh.  Now using .htaccess I&#8217;m trying to restrict my web viewers from traversing directories but I have encountered an issue with my reconfiguration. 

Here is one of my vhosts configuration files:

```

<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerAdmin coffee.drinker.daniel@gmail.com
        ServerName <DN1.com>
        ServerAlias www.<DN1.com>
        DocumentRoot /var/www/html/<DN1.com>/public_html

        <Directory "/var/www/html/<DN1.com>/public_html">
                Options Indexes FollowSymlinks
                AllowOverride All
                Require all granted
        </Directory>

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
RewriteEngine on
RewriteCond %{SERVER_NAME} =<DN1.com> [OR]
RewriteCond %{SERVER_NAME} =www.<DN1.com>
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]

</VirtualHost>

```

I used a guide called &#8220;[The Six Most Common Htaccess Problems and How to Fix Them]("http://smartwebdeveloper.com/apache/htaccess-problems")&#8221; and as suggested, I triple checked every potential error, including  syntax inside the apache configuration files and errors with the naming of .htaccess.  Everything looks OK to me.
  
[One poster on Stackoverflow suggests]("https://stackoverflow.com/questions/12202387/htaccess-not-working-apache") putting a line of nonsense in .htaccess to determine whether or not it&#8217;s being read. This is a helpful technique.  So when I navigate to a directory that I don&#8217;t want my website users to view, the contents of the directory are still showing meaning the problem still is with my apache configuration file, right?

What other information can I provide to help activate my .htaccess file?

Thanks for your attention.

---

### Post by Drone4four on 2017-06-15
I resolved the issue myself.  Take note of the crucial lines from the configuration file:
```
<Directory "/var/www/html/<DN1.com>/public_html">
                Options Indexes FollowSymlinks
                AllowOverride All
                Require all granted
        </Directory>
```

Turns out, this belongs in /etc/apache2/apache2.conf, not inside my vhost configuration file. After making that change, .htaccess is called the way it should!

---

### Post by SeijiSensei on 2017-06-15
Generally speaking, if you have administrative access, it makes sense to get rid of .htaccess files altogether and invoke those directives inside the <Directory> stanzas for the virtual hosts.  The .htaccess file is a kludge for hosting organizations to enable their customers to make changes to the Apache configuration for their own particular website.  I find it much easier to consolidate everything in the virtual host definitions so there's only one place to look.

---

