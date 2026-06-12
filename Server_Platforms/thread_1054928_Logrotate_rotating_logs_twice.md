---
title: "Logrotate rotating logs twice"
date: 2009-01-30
forum: Server Platforms
---

### Post by wjlroe on 2009-01-30
Hi,

I'm having problems with logrotate. It is creating two rotated archives every night. For example:

```
-rw-r----- 1 root     adm      4.6M 2009-01-30 11:23 access.log
-rw-r----- 1 root     adm      490K 2008-06-08 07:57 access.log.10.gz
-rw-r----- 1 root     adm        20 2009-01-30 04:28 access.log.1.gz
-rw-r----- 1 root     adm       44K 2009-01-30 04:28 access.log.2.gz
-rw-r----- 1 root     adm        20 2009-01-29 04:25 access.log.3.gz
-rw-r----- 1 root     adm       30K 2009-01-29 04:25 access.log.4.gz
-rw-r----- 1 root     adm        20 2009-01-28 04:22 access.log.5.gz
-rw-r----- 1 root     adm      400K 2008-06-29 07:56 access.log.7.gz
-rw-r----- 1 root     adm      270K 2008-06-22 07:56 access.log.8.gz
-rw-r----- 1 root     adm      596K 2008-06-15 07:56 access.log.9.gz
```

However, the logrotate config for this stipulates not to rotate empty log files and shouldn't be running twice in the same minute:

```
/home/*/logs/*.log {
   daily
   missingok
   rotate 5
   compress
   notifempty
   create 640 root adm
   sharedscripts
        prerotate
                [ -f /etc/awstats/awstats.conf ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null
                for cfg in `find /etc/awstats -name 'awstats.*.conf' -printf '%f\n' | sed 's/^awstats\.\(.*\)\.conf/\1/'`; do
                /usr/lib/cgi-bin/awstats.pl -config=$cfg -update >/dev/null
                done
        endscript
   postrotate
      if [ -f /var/run/apache2.pid ]; then
         /etc/init.d/apache2 reload > /dev/null
      fi
   endscript
}
```

Any clues?

---

### Post by koenn on 2009-01-31
possible clue:
if /home/* matches 2 directories, this might cause logrotate to be run twice, if I read man logrotate correctly.

---

