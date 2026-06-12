---
title: "Bizarre logrotate behavior with apache"
date: 2010-07-02
forum: Server Platforms
---

### Post by Chaosratt on 2010-07-02
New server up, seems to be working just dandy. Decided to update the apache logrotate script to grab my site-specific log files (which are not in /var/log/apache2 :( ).
Now logrotate is rotating the /etc/init.d/apache2 and my awstats script files whenever it runs!

Heres what /etc/logrotate.d/apache2 has to say for itself:

```
/var/log/apache2/*.log /var/www/<SuperSecretDomain1>/logs/*.log /var/www/<SuperSecretDomain2>/logs/*.log {
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
        prerotate
        /usr/share/doc/awstats/examples/awstats_updateall.pl now -awstatsprog=/usr/lib/cgi-bin/awstats.pl > /dev/null 2>&1
        endscript
        monthly
}

```

I've done some googleing and come up empty. I'm not sure exactly what I did wrong, but someone has to know what/how I've broken it!


Edit: the 'monthly' and 'rotate 52' bits were just me tinkering, it isn't going to stay like that when its acutally working!

---

### Post by Chaosratt on 2010-07-03
In case anyone comes across this in the future, I solved this.
Looks like the logrotate doesnt like the full command. Wrap the awstatsupdate command into a script file (I use /etc/cron.hourly/awstats) and have lograte run that.

---

### Post by DJYoshaBYD on 2010-07-03
nice... i was going to suggest that.. i have run across that problem as well, and did exactly that.. lol

---

