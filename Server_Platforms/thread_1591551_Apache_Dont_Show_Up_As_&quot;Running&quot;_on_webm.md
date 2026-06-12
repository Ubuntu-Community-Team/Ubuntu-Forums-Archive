---
title: "Apache Dont Show Up As &quot;Running&quot; on webmin! ( ubuntu 10.10 rc , webmin 1.520)"
date: 2010-10-09
forum: Server Platforms
---

### Post by ryanteck on 2010-10-09
Hi guys
in the apache and server status parts of webmin i always get Apache Server coming up as " down " or " offline "
can anyone help?

it detected my system as ubuntu 10.10 and uses webmin con fig debien 5.0 altough before it used 6.0 both did not work

---

### Post by ckankiewicz on 2010-10-10
I'm having the same issue.  I'm also seeing this when trying to view the Apache error logs:

```
cat: /var/log/apache2$SUFFIX/error.log: No such file or directory
```

---

### Post by Vegan on 2010-10-10
```
sudo apt-get install apache2
```

---

### Post by ckankiewicz on 2010-10-10
Just tried Vegan's suggestion, no change.

```
chris@PHLAKTOP ~ $ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by CharlesA on 2010-10-10
> **ckankiewicz said:**
> I'm having the same issue.  I'm also seeing this when trying to view the Apache error logs:

```
cat: /var/log/apache2$SUFFIX/error.log: No such file or directory
```

It won't find anything with a "$SUFFIX" unless it's defined.

I've not used Webmin in some time, but check out the module config for apache and see what it says.

I installed the latest version of Webmin on 10.04 and it found apache running. Perhaps try updating all the way to the final release version of Maverick?

---

### Post by Vegan on 2010-10-10
might be an idea for the OP to run


```

sudo apt-get update
sudo apt-get upgrade

```

I got rid of webmin and went back to the command prompt.

Webmin is OK, but its faster with the CLI by 4x for an experienced Linux administrator.

---

### Post by CharlesA on 2010-10-11
Agreed. I got rid of it long ago as well. I find it easier to configure stuff over plain SSH.

---

### Post by ckankiewicz on 2010-10-11
Was up to date before posting originally.  Ran an apt-get update and an apt-get upgrade anyway and still no change.  I think the problem might be with Webmin.

---

### Post by CharlesA on 2010-10-11
I just checked on 32-bit Maverick and it shows Apache as not running, even when it is.

Trying to start it when it is stopped results in an error, but it starts anyway.

I'd say it's a problem with Webmin.

---

### Post by hrpr on 2010-10-12
I just installed Webmin on Ubuntu 10.10 desktop and had same problem.  Fixed in my case by settng path to Apache PID to "/var/run/apache2.pid" rather than using the default setting of "Work out automatically."  I did not make any changes to the  envvars file.

---

### Post by CharlesA on 2010-10-12
> **hrpr said:**
> I just installed Webmin on Ubuntu 10.10 desktop and had same problem.  Fixed in my case by settng path to Apache PID to "/var/run/apache2.pid" rather than using the default setting of "Work out automatically."  I did not make any changes to the  envvars file.

Does it let you stop/start it without displaying errors as well?

---

### Post by ckankiewicz on 2010-10-12
> **hrpr said:**
> I just installed Webmin on Ubuntu 10.10 desktop and had same problem.  Fixed in my case by settng path to Apache PID to "/var/run/apache2.pid" rather than using the default setting of "Work out automatically."  I did not make any changes to the  envvars file.

Thanks! That worked for me, though I'm still having the problem with the random variable in the error log.

---

### Post by CharlesA on 2010-10-12
It sounds like that variable isn't defined, but I don't know where to look, since I don't use webmin.

Anyway, the logs should be in:

```
/var/log/apache2/error.log
```

---

### Post by hrpr on 2010-10-12
> **ckankiewicz said:**
> Thanks! That worked for me, though I'm still having the problem with the random variable in the error log.I had same problem.  Delated the $SUFFIX references in envvars file and log now displays without error.

Here's what my envvars file looks like now:
----------------------------------------------------

# envvars - default environment variables for apache2ctl

# fix for webmin and Ubuntu 10.10 - deleted $SUFFIX references
# 2010-10-12, harryb

# this won't be correct after changing uid
unset HOME

# for supporting multiple apache2 instances
if [ "${APACHE_CONFDIR##/etc/apache2-}" != "${APACHE_CONFDIR}" ] ; then
	SUFFIX="-${APACHE_CONFDIR##/etc/apache2-}"
else
	SUFFIX=
fi

# Since there is no sane way to get the parsed apache2 config in scripts, some
# settings are defined via environment variables and then used in apache2ctl,
# /etc/init.d/apache2, /etc/logrotate.d/apache2, etc.
export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2.pid
export APACHE_RUN_DIR=/var/run/apache2
export APACHE_LOCK_DIR=/var/lock/apache2
# Only /var/log/apache2 is handled by /etc/logrotate.d/apache2.
export APACHE_LOG_DIR=/var/log/apache2

## The locale used by some modules like mod_dav
export LANG=C
## Uncomment the following line to use the system default locale instead:
#. /etc/default/locale

export LANG

## The command to get the status for 'apache2ctl status'.
## Some packages providing 'www-browser' need '--dump' instead of '-dump'.
#export APACHE_LYNX='www-browser -dump'

--------------------------------------------------------------

---

### Post by James78 on 2010-10-14
I have no idea why $SUFFIX causes a problem now, and worked perfectly before, but this fixed my problem. And now I have a perfect upgrade for my server.

---

### Post by Kaigeos on 2010-11-04
Thanks for the help, removing the $SUFFIX was a great fix.

---

### Post by johan_london on 2010-11-19
Huge thanks to hrpr for posting the solution to this problem. I followed his instructions, then restarted apache2 and webmin. Works perfectly now

---

