---
title: "Apache2 virtual hosts logrotate"
date: 2012-02-20
forum: Server Platforms
---

### Post by fernandoch on 2012-02-20
How do you guys logrotate your virtual host log files? If I change the default location, then the log rotation does not work anymore.

I changed this file /etc/logrotate.d/apache2 to point to the new log location, but it is not working.

Any clues?

---

### Post by volkswagner on 2012-02-20
Are your other logs rotating?

```
ls /var/log
```

What does your  /etc/logrotate.d/apache2 look like?

```
cat  /etc/logrotate.d/apache2 
```

---

### Post by Vegan on 2012-02-20
the default log rotations will make sure that the disk does not get filled to capacity

for a web appliance I suggests a disk of 80 GB or more.

this way lots of room for temp files and updates etc.

---

### Post by fernandoch on 2012-02-20
> **volkswagner said:**
> Are your other logs rotating?

```
ls /var/log
```

What does your  /etc/logrotate.d/apache2 look like?

```
cat  /etc/logrotate.d/apache2 
```

Yes they are rotating the other logs.

Here is the /etc/logrotate.d/apache2 which is working

```
/var/log/apache2/*.log {
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
}
```

And here is the one I created /etc/logrotate.d/vhosts it is daily just to check it out

```
/srv/www/mysite/logs/*.log {
        daily
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
}
```

Do you see antyhing wrong?

---

### Post by SeijiSensei on 2012-02-20
I presume the virtual hosts have Log directives that point the various log files to /srv/www/mysite/logs/*.log?  Do you see the logs there, but they are not being rotated, or do you not see the logs at all?  If the latter you need to edit your <VirtualHost> definitions.

Are you sure the logs end in ".log"?

---

### Post by fernandoch on 2012-02-20
The logs are in /srv/www/mysite/logs/*.log but they are not being rotated. This is the problem I am facing.

---

### Post by SeijiSensei on 2012-02-20
Run the command "sudo logrotate -v /etc/logrotate.d/vhosts" to force logrotate to do its thing and tell you what is going on (the -v switch).

I presume crond is running?  Do you see it if you run "ps ax | grep cron | grep -v grep"?  If crond isn't running, then scheduled processes like logrotate won't run.

---

### Post by fernandoch on 2012-02-20
It worked it seems :)

```
root@plato:/srv/www/mysite/logs# ls -lrt
total 12
-rw-r--r-- 1 root root  128 Feb 20 15:54 error.log.1
-rw-r--r-- 1 root root 6478 Feb 20 15:54 access.log.1
-rw-r----- 1 root adm     0 Feb 20 15:57 error.log
-rw-r----- 1 root adm     0 Feb 20 15:57 access.log
```

Now why are they being created with group root? It is ok?

---

### Post by fernandoch on 2012-02-20
Maybe because I did run it with root and it was not the cron job who ran it?

---

### Post by fernandoch on 2012-02-21
I confirm it, it has been created with group adm by the cron job.

---

