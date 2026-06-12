---
title: "Apache2 default site prevents any other from being viewed"
date: 2010-10-28
forum: Server Platforms
---

### Post by Pitt Stains on 2010-10-28
The machine in question runs Apache 2.2.14 on Ubuntu 10.04.1.  The problem is that unless I disable the 000-default site, the virtualhost I have set up doesn't show up.  I get the "it works" page instead.  I have other servers where my virtualhosts sit alongside the default site without problems, so I'm kind of scratching my head at this point.

I haven't changed /etc/apache2/sites-available/default since install.  The config for my virtualhost follows:

```

<VirtualHost *:80>
        ServerName backuppc.loc
        ServerAlias www.backuppc.loc

        DocumentRoot /usr/share/backuppc/cgi-bin/
#       Alias /backuppc /usr/share/backuppc/cgi-bin/

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

        RewriteEngine On
        RewriteCond %{HTTP_HOST} !^backuppc\.loc(:80)?$
        RewriteRule ^/(.*) http://backuppc.loc/$1 [R=301]

        RewriteRule ^/backuppc/(.*) /$1 [R=301]

        <Directory /usr/share/backuppc/cgi-bin/>
                AllowOverride None
                Options ExecCGI FollowSymlinks
                AddHandler cgi-script .cgi
                DirectoryIndex index.cgi

                AuthGroupFile /etc/backuppc/htgroup
                AuthUserFile /etc/backuppc/htpasswd
                AuthType basic
                AuthName "BackupPC admin"
                require valid-user
        </Directory>
</VirtualHost>

```

The only unusual thing I can think of is that the hostname of the machine in question is backuppc, and that in /etc/hosts I've got:

```

127.0.1.1       backuppc.loc backuppc localhost
10.10.10.70     backuppc.loc backuppc localhost

```

In other words, the output of "hostname -f" is backuppc.loc, which is also the name of the virtualhost, as well as the name of the config file for the virtualhost.

---

### Post by LaserBoi on 2011-06-28
I have exact same problem. 
Did you find a solution?

---

### Post by falko on 2011-06-28
Do you use a domain/hostname specified in ServerName/ServerAlias to access your vhost? If you use anything else, the default vhost will be shown.

---

