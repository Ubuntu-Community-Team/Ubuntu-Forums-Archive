---
title: "logrotate issue"
date: 2011-10-05
forum: Server Platforms
---

### Post by Moptop650 on 2011-10-05
Hi guys,

I am trying to set up Logrotate on my ubuntu server. I want it to rotate my apache logs when they reach over 100Mb in size. However, it seems to be rotating them whenever the cron job runs instead of waiting for this limit.

My logrotate.d is the defaults -- 

> weekly

# keep 4 weeks worth of backlogs
rotate 4

# create new (empty) log files after rotating old ones
create

# uncomment this if you want your log files compressed
#compress

# packages drop log rotation information into this directory
include /etc/logrotate.d

# no packages own wtmp, or btmp -- we'll rotate them here
/var/log/wtmp {
    missingok
    monthly
    create 0664 root utmp
    rotate 1
}

/var/log/btmp {
    missingok
    monthly
    create 0660 root utmp
    rotate 1
}

# system-specific logs may be configured here


And the configuration for my apache logs - 

> /home/www/logs/*.log {
        olddir /home/www/logs/oldlogs/
        size 100M
        missingok
        rotate 300
        compress
        compressext .gz
        create 777 www www
        sharedscripts
                prerotate
                /usr/lib/cgi-bin/awstats.pl -update -config=mysite.com > /dev/null
        endscript
        postrotate
                /etc/init.d/apache2 reload > /dev/null
        endscript
}

I am confident my paths are correct, and if my understanding is correct, "size 100M" should only let it rotate logs over 100M? What is the problem?

---

