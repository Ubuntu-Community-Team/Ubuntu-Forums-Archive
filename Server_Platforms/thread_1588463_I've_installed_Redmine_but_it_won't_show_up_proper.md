---
title: "I've installed Redmine but it won't show up properly on browser"
date: 2010-10-04
forum: Server Platforms
---

### Post by deadguysleeps on 2010-10-04
Hi all. I've installed Redmine using the tutorial on this site [http://www.jamestoyer.me.uk/how-tos/installing-redmine-and-subversion-on-ubuntu-10-04/]("http://www.jamestoyer.me.uk/how-tos/installing-redmine-and-subversion-on-ubuntu-10-04/") but without installing subversion.

However, after installing Redmine, I point my browser to [http://202.x.x.x/redmine/](http://202.x.x.x/redmine/) but it shows up like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171341&stc=1&d=1286249418[/IMG]

This is my virtualhost configuration: /etc/apache2/sites-available/default:

```
<VirtualHost *:80>
    bla bla bla
</VirtualHost>
<VirtualHost *:80>
    DocumentRoot /var/www/redmine/public

    PassengerPoolIdleTime 0

        <Directory "/var/www/redmine/public">
                PassengerEnabled on
                AllowOverride
                Options -MultiViews
        </Directory>

    LogLevel warn
    ErrorLog /var/log/apache2/redmine_error
    CustomLog /var/log/apache2/redmine_access combined

</VirtualHost>
```

* it does show up properly in the browser when i test it using Webrick webserver
* I don't put in the line ServerName in the virtualhost configuration because my company doesn't yet purchase a domain name for this IP address (maybe my boss prefer this site to be semi-private)

**Setup:**

Ubuntu 9.10
Redmine 1.0.2

Ruby version              1.8.7 (i486-linux)
RubyGems version          1.3.7
Rack version              1.0
Rails version             2.3.5
Active Record version     2.3.5
Active Resource version   2.3.5
Action Mailer version     2.3.5
Active Support version    2.3.5
Edge Rails revision       unknown
Application root          /var/www/redmine
Environment               production
Database adapter          mysql
Database schema version   20100819172912

Any help will be appreciated. Thanks in advance.

---

### Post by deoren on 2010-11-13
I used a different install directory, but here is what I had:
```

    Alias /redmine /opt/redmine/public
    <Location /redmine>
        # Per Redmine FAQ, "I get a 404-error when I try to view or diff a PHP-file"
        RemoveHandler .php

        PassengerEnabled On

        # Redmine is incompatible with this option enabled
        PassengerHighPerformance Off

        RailsEnv production
        RailsBaseURI /redmine
        PassengerAppRoot /opt/redmine

        Options Indexes FollowSymLinks -Multiviews
    </Location>
```
My document root was somewhere else, so I had to place a symlink in the document root to point to my public folder. Since your document root *is* the public folder, I don't think you'll need that.

My guess is that you need to specify the **RailsBaseURI**. Try that and let us know if it works.

Also, run this:

```
. /etc/apache2/envvars && apache2 -M
```

and make sure this is in the list:
> passenger_module

---

