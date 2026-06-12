---
title: "Logrotate errors on Ubuntu 10.10"
date: 2010-09-01
forum: Server Platforms
---

### Post by deoren on 2010-09-01
Hi,

I've called myself searching the forums and using Google, so my apologies if this has already been answered somewhere before.

I had an Ubuntu 10.04.1 LTS server setup with Apache and various other services. Everything was working fine and log rotation was occurring daily as expected. The output from any scripts was mailed via cron and logrotate itself was pretty much silent in regards to chatter.

Then I upgraded to 10.10 and as a result of this, the Apache configuration and it's logrotate config file (/etc/logrotate.d/apache2) were modified.

I merged the changes with my existing files by hand and that's when I started getting this:

> /etc/cron.daily/logrotate:
stty: standard input: Invalid argument
error: error running shared postrotate script for ‘/var/log/apache2/*access*.log ‘
stty: standard input: Invalid argument
error: error running shared postrotate script for ‘/var/log/apache2/*error*.log ‘
run-parts: /etc/cron.daily/logrotate exited with return code 1Here are the contents of:

**/etc/logroate.d/apache2**
```
/var/log/apache2/*access*.log {

    olddir /mnt/backups/logs/apache2
    daily
    missingok
    rotate 30
    compress
    delaycompress
    notifempty
    create 640 root adm
    sharedscripts
    postrotate
        /etc/init.d/apache2 reload > /dev/null
    endscript
}

/var/log/apache2/*error*.log {    
    olddir /mnt/backups/logs/apache2
    daily
    mail root
    mailfirst
    missingok
    rotate 30
    compress
    delaycompress
    notifempty
    create 640 root adm
    sharedscripts
    postrotate
        /etc/init.d/apache2 reload > /dev/null
    endscript
}
```**/etc/fstab**
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=5ed08cb3-b5e5-4101-acc1-d385cbe298ce /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0a375213-e8bc-4fcf-b572-f415bd86c5a1 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```**/etc/logrotate.conf**
```
# see "man logrotate" for details
# rotate log files daily
daily

# keep 30 days worth of backlogs
rotate 30

# create new (empty) log files after rotating old ones
create

# uncomment this if you want your log files compressed
compress

# Place older log files in /mnt/backups so they can be placed in Tivoli
olddir /mnt/backups/logs

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
```**/etc/crontab**
```
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root

# minute    hour    dom     month   dow     command
# ------------------------------------------------------------------------------------------

17          *       *       *       *       cd / && run-parts --report /etc/cron.hourly
25          6       *       *       *       test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47          6       *       *       7       test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52          6       1       *       *       test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

```

Anyone see anything out of place? Any tips?

Thanks for your time.

---

