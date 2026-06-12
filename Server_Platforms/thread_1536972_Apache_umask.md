---
title: "Apache umask"
date: 2010-07-22
forum: Server Platforms
---

### Post by RLovelett on 2010-07-22
I am trying to set the default files created by www-data to 774 (umask of 003).

I go to ```
/etc/apache2/envvars
``` and have set these parameters. NOTE: The only thing I actually changed was adding the umask 003 at the end.

```
# envvars - default environment variables for apache2ctl

# Since there is no sane way to get the parsed apache2 config in scripts, some
# settings are defined via environment variables and then used in apache2ctl,
# /etc/init.d/apache2, /etc/logrotate.d/apache2, etc.
export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2.pid

## The locale used by some modules like mod_dav
export LANG=C
## Uncomment the following line to use the system default locale instead:
#. /etc/default/locale

export LANG

## The command to get the status for 'apache2ctl status'.
## Some packages providing 'www-browser' need '--dump' instead of '-dump'.
#export APACHE_LYNX='www-browser -dump'
#

umask 003

```

However, when I create new files the permissions are being set as 755 (or a umask of 022).

I tried setting the /etc/profiles to be 002 as well to no avail. ***What am I missing here?***

---

### Post by RLovelett on 2010-08-04
Bump?

---

### Post by ruffEdgz on 2010-08-04
From what I have been reading, when a file is created in linux, the default permissions should be:
```

666 - UMASK

```
When a directory is created in linux, the default permissions should be:
```

777 - UMASK

```
So from that evidence I have found, it seems that the UMASK isn't going to help you with files needing to be 0774 (0003) with UMASK. I have read that one way to make sure that all files in a specific directory does have the executable for both the UID and GID section of the permissions would be to write a script and place into crontab to run every 5 minutes. 

The script could be simple as just 'chmod -R 774 /var/www/*' or complex to make sure it only does files that need to be changed to '774'.

I'm surprised by your quote here:
> 
However, when I create new files the permissions are being set as 755 (or a umask of 022).

just because it doesn't seem like it could or should happen on your system.

Another idea would be to use ACLs for that directory to see if that helps:
[https://help.ubuntu.com/community/FilePermissions#ACLs]("https://help.ubuntu.com/community/FilePermissions#ACLs")

Hope this helps!

---

### Post by Bachstelze on 2010-08-04
> **RLovelett said:**
> 
However, when I create new files

How?

---

### Post by vanyatka on 2011-03-13
Have exactly the same problem as originally posted. Adding umask 002 to /etc/apache2/envvars doesn't have any effect.

The 'chmod + chron' solution offered earlier, is a laugh, really )

---

### Post by vanyatka on 2011-03-13
> **Bachstelze said:**
> How?

Via mod_dav, mounted as a shared folder from Mac Os. Files are created as '-rw------'.

I wonder if this should be configured elsewhere, on the mod_dav level.

---

### Post by SeijiSensei on 2011-03-13
Try creating a .profile file in /var/www, addding the umask command to it, then restarting Apache.  Did that help?

---

### Post by vanyatka on 2011-03-13
> **SeijiSensei said:**
> Try creating a .profile file in /var/www, addding the umask command to it, then restarting Apache.  Did that help?

SeijiSensei, thanks for the advice. Unfortunately, it didn't help.

Also, I tried to add this command to apachectl and init.d/apache2, no luck as well.

upd. Seems I'm not the only one struggling with this issue:
[http://forum.linode.com/viewtopic.php?p=34393]("http://forum.linode.com/viewtopic.php?p=34393")

---

### Post by lil_elvis2000 on 2011-05-07
There is a bug in the Apache mod_dav module in 10.04 (2.2.14 apache2) so that all files are created with the wrong permissions.

You can either:
 - install apache 2.2.15 - I am thinking about that but I've no clue how to do that without breaking everything else!
 - Upgrade to 10.10
 - setup a crontab script to change the permissions

I've done the last one there. But looking for help on doing the first one.

See related bug [https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/540747](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/540747)

---

