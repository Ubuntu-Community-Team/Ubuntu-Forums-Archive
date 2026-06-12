---
title: "Pointing Logrotate at user defined location for CustomLog"
date: 2009-07-30
forum: Server Platforms
---

### Post by Magnificent 7 on 2009-07-30
Hi,

I've had a trawl around these support forums using a variety of search terms, and not turned up anything exactly dealing with my question.

My main server is configured for name-based virtual hosting and is taking traffic for five domains. Each domain configuration file in /etc/apache2/sites-available points access.log and error.log at a custom directory location /home/httpd/vhtdocs/name_of_domain/logs.

All is peachy, apart from logrotate apparently not having been automatically reconfigured with each invokation of a2ensite to point to the altered location of the logs for each domain. As a consequence these are not rotating.

Reading up a bit on logrotate, it seems it looks at a variety of inputs, one of which is the contents of directory /etc/logrotate.d, containing an entry apache2 placed there by the web server. At the moment this contains the directive

```
[color=green]/var/log/apache2/*.log {
        weekly
        missingok
        rotate 52
        compress
        delaycompress
        notifempty
        create 640 root adm
        sharedscripts
        postrotate
                if [ -f "`. /etc/apache2/envvars ; echo ${APACHE_PID_FILE:-/var/run/apache2.pid}`" ]; then
                        /etc/init.d/apache2 reload > /dev/null
                fi
        endscript
}[/color]
```

Which of course is correct if the default location is accepted for all the configured domains. The question is, is the accepted way to kick-start logrotate in my circumstances to doctor /etc/logrotate.d/apache2 to look something like

```
[color=green]/var/log/apache2/*.log {
        weekly
        missingok
        rotate 52
        compress
        delaycompress
        notifempty
        create 640 root adm
        sharedscripts
        postrotate
                if [ -f "`. /etc/apache2/envvars ; echo ${APACHE_PID_FILE:-/var/run/apache2.pid}`" ]; then
                        /etc/init.d/apache2 reload > /dev/null
                fi
        endscript
}[/color]

[color=red]/home/httpd/vhtdocs/name_of_domain_1/logs/*.log {
        weekly
        missingok
        rotate 4
        compress
        delaycompress
        notifempty
        create 640 root adm
        sharedscripts
        postrotate
                if [ -f "`. /etc/apache2/envvars ; echo ${APACHE_PID_FILE:-/var/run/apache2.pid}`" ]; then
                        /etc/init.d/apache2 reload > /dev/null
                fi
        endscript
}

/home/httpd/vhtdocs/name_of_domain_2/logs/*.log {
        weekly
        missingok
        rotate 4
        compress
        delaycompress
        notifempty
        create 640 root adm
        sharedscripts
        postrotate
                if [ -f "`. /etc/apache2/envvars ; echo ${APACHE_PID_FILE:-/var/run/apache2.pid}`" ]; then
                        /etc/init.d/apache2 reload > /dev/null
                fi
        endscript
}[/color]
```

If this is the correct location and form for this code, is it necessary to run the [sharedscripts]...[endscript] after the rotation declaration for each virtual host?

Despite not being up to speed on the syntax for the bit of code in sharedscripts I presume that this has something to do with forcing the Apache daemon to release the file that has just been renamed access.log.1 or error.log.1, as I noticed that when I tried to rotate the logs manually with

```
[color=green]cd /home/httpd/vhtdocs/name_of_site/logs
sudo mv access.log access.log.1[/color]
``` Apache miraculously continued writing to access.log.1 and no new access.log was created!

Any help with this would be appreciated as I would rather not stop Apache to do the log rotation manually.

---

