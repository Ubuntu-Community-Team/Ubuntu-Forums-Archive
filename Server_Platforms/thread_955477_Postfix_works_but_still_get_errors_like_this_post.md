---
title: "Postfix works but still get errors like this post"
date: 2008-10-22
forum: Server Platforms
---

### Post by volkswagner on 2008-10-22
I am trying to pin down the cause for the following error.  First I must confess, it is a surprise it does work.  I followed several how-to's, so it is a patchwork of sorts.

FROM /var/log/auth.log.....I get the error when my domain receives mail.

```
Oct 21 08:39:55 Web postfix/smtpd[9403]: sql_select option missing
Oct 21 08:39:55 Web postfix/smtpd[9403]: auxpropfunc error no mechanism available
Oct 21 08:39:55 Web postfix/smtpd[9403]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql
```

Found this tread, not sure if the fix will be the same for me.

[http://ubuntuforums.org/showthread.php?t=683687]("http://ubuntuforums.org/showthread.php?t=683687")

Oddly, my setup works.  Postfix, Courier, SquirrelMail, Evolution on client via IMAP.

My /etc/posfix/master.cf and /etc/posfix/main.cf files are empty, huh.

File: /etc/postfix/sasl/smtpd.conf  

```
pwcheck_method: saslauthd
mech_list: plain login

```


  File: /etc/default/saslauthd                          

```
# This needs to be uncommented before saslauthd will be run automatically
 START=yes

PWDIR="/var/spool/postfix/var/run/saslauthd"
PARAMS="-m ${PWDIR}"
PIDFILE="${PWDIR}/saslauthd.pid"


# You must specify the authentication mechanisms you wish to use.
# This defaults to "pam" for PAM support, but may also include
# "shadow" or "sasldb", like this:
# MECHANISMS="pam shadow"

MECHANISMS="pam"


# Other options (default: -c)
# See the saslauthd man page for information about these options.
#
# Example for postfix users: "-c -m /var/spool/postfix/var/run/saslauthd"
# Note: See /usr/share/doc/sasl2-bin/README.Debian
#OPTIONS="-c"

#make sure you set the options here otherwise it ignores params above and will $
OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd"
```

Process running

  ```
4444 	root 	Oct19 	/usr/sbin/courierlogger -pid=/var/run/courier/authdaemon/pid -start /usr/lib/cou ...
      4445 	root 	Oct19 	/usr/lib/courier/authlib/authdaemond.mysql
         4479 	root 	Oct19 	/usr/lib/courier/authlib/authdaemond.mysql
         4480 	root 	Oct19 	/usr/lib/courier/authlib/authdaemond.mysql
         4481 	root 	Oct19 	/usr/lib/courier/authlib/authdaemond.mysql
         4482 	root 	Oct19 	/usr/lib/courier/authlib/authdaemond.mysql
         4483 	root 	Oct19 	/usr/lib/courier/authlib/authdaemond.mysql
```

Is that odd.  Why so many authdaemon.mysql running?

Anyway from the linked thread it seems I should add an entry to /etc/posfix/main.cf, but I am not sure exactly what to put there, since I am not running cyrus.

> Can you add "cyrus_sasl_config_path = /etc/postfix/sasl:/usr/lib/sasl2" and "broken_sasl_auth_clients = yes" to your /etc/posfix/main.cf file

I followed most of this how-to. 
[http://flurdy.com/docs/postfix/#config-simple-database]("http://flurdy.com/docs/postfix/#config-simple-database")

Thanks in advance.

---

### Post by volkswagner on 2008-10-22
> **volkswagner said:**
> 
My /etc/posfix/master.cf and /etc/posfix/main.cf files are empty, huh.


Duh, of course those are empty, notice the typo?

see attached.

I noticed empty fields in main.cf

```
mailbox_command =
smtpd_sasl_local_domain =
```

---

