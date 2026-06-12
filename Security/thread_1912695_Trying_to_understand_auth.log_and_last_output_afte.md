---
title: "Trying to understand auth.log and last output after strange logout/reboot"
date: 2012-01-21
forum: Security
---

### Post by KIAaze on 2012-01-21
Hi,

I did not log out before going to sleep and when I woke up, I had to log back in, which I found a bit strange.
So I started checking the logs and found the following:
/var/log/auth.log:
```

Jan 16 07:42:36 *** su[20434]: Successful su for lire by root
Jan 16 07:42:36 *** su[20434]: + ??? root:lire
Jan 16 07:42:36 *** su[20434]: pam_unix(su:session): session opened for user lire by (uid=0)
Jan 16 07:42:37 *** su[20434]: pam_unix(su:session): session closed for user lire
...
Jan 17 07:51:44 *** su[29924]: Successful su for lire by root
Jan 17 07:51:44 *** su[29924]: + ??? root:lire
Jan 17 07:51:44 *** su[29924]: pam_unix(su:session): session opened for user lire by (uid=0)
Jan 17 07:51:48 *** su[29924]: pam_unix(su:session): session closed for user lire
...
Jan 18 07:50:36 *** su[2712]: Successful su for lire by root
Jan 18 07:50:36 *** su[2712]: + ??? root:lire
Jan 18 07:50:37 *** su[2712]: pam_unix(su:session): session opened for user lire by (uid=0)
Jan 18 07:50:39 *** su[2712]: pam_unix(su:session): session closed for user lire
...
Jan 19 11:10:45 *** su[2874]: Successful su for lire by root
Jan 19 11:10:45 *** su[2874]: + ??? root:lire
Jan 19 11:10:45 *** su[2874]: pam_unix(su:session): session opened for user lire by (uid=0)
Jan 19 11:10:49 *** su[2874]: pam_unix(su:session): session closed for user lire
...
Jan 20 15:42:20 *** su[2771]: Successful su for lire by root
Jan 20 15:42:20 *** su[2771]: + ??? root:lire
Jan 20 15:42:20 *** su[2771]: pam_unix(su:session): session opened for user lire by (uid=0)
Jan 20 15:42:23 *** su[2771]: pam_unix(su:session): session closed for user lire
...
Jan 21 03:22:14 *** su[1903]: Successful su for lire by root
Jan 21 03:22:14 *** su[1903]: + ??? root:lire
Jan 21 03:22:14 *** su[1903]: pam_unix(su:session): session opened for user lire by (uid=0)
Jan 21 03:22:16 *** su[1903]: pam_unix(su:session): session closed for user lire

```

last command:
```

***   pts/2        :0.0             Sat Jan 21 06:49   still logged in   
***   pts/1        :0.0             Sat Jan 21 06:49   still logged in   
***   tty1                          Sat Jan 21 06:37 - 06:38  (00:00)    
***   tty1                          Sat Jan 21 06:37 - 06:37  (00:00)    
***   tty7         :0               Sat Jan 21 06:37   still logged in   
reboot   system boot  2.6.32-37-generi Sat Jan 21 02:51 - 06:55  (04:04)    
***   tty7         :0               Fri Jan 20 15:31 - crash  (11:20)    
reboot   system boot  2.6.32-37-generi Fri Jan 20 15:30 - 06:55  (15:25)    

```

/etc/passwd:
```

lire:x:292:129:Lire,,,:/var/lib/lire:/bin/sh

```

After some additional checking, it turns out that the "lire" user seems to be created by the "lire" package: [https://launchpad.net/ubuntu/+source/lire](https://launchpad.net/ubuntu/+source/lire)
I do think I installed it at some point, but never used it. In any case it was installed since a while and the auth.log entries seem legitimate (cf logs below).

Anyway, I would like to understand the following things from the logs:
auth.log:
```

Jan 16 07:42:36 *** su[20434]: + ??? root:lire

```
**What does that mean? That an unknown command was executed by lire as root?**

[edit]
ok, I think I understand part of it now, after doing a "sudo su" myself and seing this:
```

Jan 21 10:00:06 *** sudo:   kiaaze : TTY=pts/2 ; PWD=/home/kiaaze ; USER=root ; COMMAND=/bin/su
Jan 21 10:00:06 *** su[23492]: Successful su for root by root
Jan 21 10:00:06 *** su[23492]: + /dev/pts/2 root:root
Jan 21 10:00:07 *** su[23492]: pam_unix(su:session): session opened for user root by kiaaze(uid=0)
Jan 21 10:02:50 *** su[23492]: pam_unix(su:session): session closed for user root

```
So ??? for unknown terminal I assume. I actually thought it was user lire logging in as root, while it was the opposite (su for lire by root).
[/edit]

last command:
```

reboot   system boot  2.6.32-37-generi Sat Jan 21 02:51 - 06:55  (04:04)    
***   tty7         :0               Fri Jan 20 15:31 - crash  (11:20)    
reboot   system boot  2.6.32-37-generi Fri Jan 20 15:30 - 06:55  (15:25)    

```
[b]How come it shows 06:55 on both reboot lines?
How can I find out why the crash happened? Did the system fully reboot by itself? Or did it just crash gnome? Could it be a power failure?[/b]

======================
Some additional stuff I checked while I was trying to figure out what happened:
```

$ grep lire /var/log/dpkg.log.1
2011-12-03 12:58:55 install lire <nenio> 2:2.1-1
2011-12-03 12:58:55 status half-installed lire 2:2.1-1
2011-12-03 12:58:59 status half-installed lire 2:2.1-1
2011-12-03 12:59:00 status unpacked lire 2:2.1-1
2011-12-03 12:59:00 status unpacked lire 2:2.1-1
2011-12-03 12:59:17 configure lire 2:2.1-1 2:2.1-1
2011-12-03 12:59:17 status unpacked lire 2:2.1-1
2011-12-03 12:59:17 status unpacked lire 2:2.1-1
2011-12-03 12:59:17 status unpacked lire 2:2.1-1
2011-12-03 12:59:17 status unpacked lire 2:2.1-1
2011-12-03 12:59:17 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:18 status unpacked lire 2:2.1-1
2011-12-03 12:59:19 status unpacked lire 2:2.1-1
2011-12-03 12:59:19 status unpacked lire 2:2.1-1
2011-12-03 12:59:19 status unpacked lire 2:2.1-1
2011-12-03 12:59:19 status unpacked lire 2:2.1-1
2011-12-03 12:59:19 status unpacked lire 2:2.1-1
2011-12-03 12:59:19 status unpacked lire 2:2.1-1
2011-12-03 12:59:19 status unpacked lire 2:2.1-1
2011-12-03 12:59:19 status unpacked lire 2:2.1-1
2011-12-03 12:59:19 status unpacked lire 2:2.1-1
2011-12-03 12:59:19 status unpacked lire 2:2.1-1
2011-12-03 12:59:19 status unpacked lire 2:2.1-1
2011-12-03 12:59:19 status unpacked lire 2:2.1-1
2011-12-03 12:59:19 status unpacked lire 2:2.1-1
2011-12-03 12:59:20 status unpacked lire 2:2.1-1
2011-12-03 12:59:20 status unpacked lire 2:2.1-1
2011-12-03 12:59:20 status unpacked lire 2:2.1-1
2011-12-03 12:59:20 status unpacked lire 2:2.1-1
2011-12-03 12:59:20 status unpacked lire 2:2.1-1
2011-12-03 12:59:20 status unpacked lire 2:2.1-1
2011-12-03 12:59:20 status unpacked lire 2:2.1-1
2011-12-03 12:59:20 status unpacked lire 2:2.1-1
2011-12-03 12:59:20 status unpacked lire 2:2.1-1
2011-12-03 12:59:20 status unpacked lire 2:2.1-1
2011-12-03 12:59:20 status unpacked lire 2:2.1-1
2011-12-03 12:59:20 status unpacked lire 2:2.1-1
2011-12-03 12:59:20 status half-configured lire 2:2.1-1
2011-12-03 12:59:21 status installed lire 2:2.1-1

```

```

$  cat /etc/cron.daily/lire 
#! /bin/sh

# $Id: cron.daily,v 1.3 2003/11/13 18:08:54 wsourdeau Exp $

# Run periodical Lire jobs.  See lr_vendor_cron(1).

if test -x /usr/sbin/lr_vendor_cron
then
    LIREUSER='lire' /usr/sbin/lr_vendor_cron daily
fi

```

/usr/sbin/lr_vendor_cron:
```

...
  # use "su -": make sure LIREUSER will be in its own HOME, so that it can
  # savely do: o=`pwd`; cd foo; cd $o.  Scripts like lr_xml2pdf need a cwd
  # to which can get cd-ed.

  # better use sudo, if available?
  eval "$filter" < $logfile | \
    su - $LIREUSER -c \
    "lr_log2mail -s '$rotateperiod $service report from $logfile' $extraopts $service root" 2>&1 | logger -p $PRIORITY -t lire
...

```

From the lire debian package: debian/lire.preinst
```

...
        if grep "^lire:" /etc/group >/dev/null
            then
            :
        else
            addgroup --system --quiet lire
            db_set lire/use_existing_group true || true
            db_fset lire/use_existing_group seen true || true
        fi

        if grep "^lire:" /etc/passwd >/dev/null
            then
            :
        else
        # homedir will contain tmpfiles and maildir for emails containing logs
        # explicitly state group: possibly overwrite adduser.conf setting.
            adduser --system --disabled-password --shell /bin/sh \
                --ingroup lire --no-create-home --home /var/lib/lire \
                --gecos "Lire" --quiet lire
            db_set lire/use_existing_user true || true
            db_fset lire/use_existing_user seen true || true
        fi
...

```

```

$ find /var/lib/lire
/var/lib/lire
/var/lib/lire/data
/var/lib/lire/.lire
/var/lib/lire/.lire/plugins
/var/lib/lire/.lire/schemas
/var/lib/lire/.lire/reports
/var/lib/lire/.lire/templates
/var/lib/lire/.lire/converters
/var/lib/lire/.lire/filters
$ find /var/lib/lire | xargs file
/var/lib/lire:                  directory
/var/lib/lire/data:             setgid directory
/var/lib/lire/.lire:            directory
/var/lib/lire/.lire/plugins:    directory
/var/lib/lire/.lire/schemas:    directory
/var/lib/lire/.lire/reports:    directory
/var/lib/lire/.lire/templates:  directory
/var/lib/lire/.lire/converters: directory
/var/lib/lire/.lire/filters:    directory

```

---

