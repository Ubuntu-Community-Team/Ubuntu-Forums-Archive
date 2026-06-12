---
title: "LDAP Missing File"
date: 2009-05-06
forum: Server Platforms
---

### Post by AndyXS on 2009-05-06
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

I am trying to follow this setup guide for samba and openldap however I have come across a small problem. where it says "Edit the file /etc/ldap/slapd.conf", the file is missing. Up to this point I followed the guide exactly.

Can you help?

---

### Post by jnorth on 2009-05-07
> **AndyXS said:**
> [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

I am trying to follow this setup guide for samba and openldap however I have come across a small problem. where it says "Edit the file /etc/ldap/slapd.conf", the file is missing. Up to this point I followed the guide exactly.

Can you help?

Are you on Jaunty?  If so it includes OpenLDAP 2.4 which no longer includes this file, it is configured via the cn=config db.

I'm trying to learn this setup myself and just came across your question...

---

### Post by The Foz on 2009-06-24
I am also trying to get OpenLDAP working on Jaunty. I have a working configuration under Hardy (8.10) - the older version of OpenLDAP. I am trying to migrate it.

It is actually possible to start the slapd using an old style slapd.conf file, but there seem to be other problems. The provided man pages don't seem to be completely correct for this version.

To start slapd using slapd.conf, I:
[LIST=1]
[*]Edited the file /etc/init.d/slapd, to set SLAPD_CONF="/etc/ldap/slapd.conf"
[*]Just to be sure, also edited the file /etc/default/slapd to set SLAPD_CONF="/etc/ldap/slapd.conf"
[*]Created a slapd.conf - a copy of the one on my Hardy installation
[*]Renamed the directory /etc/ldap/slapd.d to something else
[/LIST]

I am now able to do a slapadd, and to confirm the results with slapcat. The problem is that the slapd daemon doesn't seem to start. The command /etc/init.d/slapd start (or restart) seems to work without errors, but there is no daemon process running, and nothing listening on port 389.

I will continue working on it, and post here again if I make any more progress.

I suspect that there is a better way to do this. I tried connecting with Luma, to see if I could configure the basedn, set up users, etc., via the client, but was not able to get that to work.

Update:

I am getting the following in the syslog -

Jun 24 16:24:48 df-services1 slapd[11974]: @(#) $OpenLDAP: slapd 2.4.15 (Mar 19 2009 10:08:25) $ ^Ibuildd@palmer:/build/buildd/openldap-2.4.15/debian/build/servers/slapd 
Jun 24 16:24:48 df-services1 slapd[11974]: /etc/ldap/slapd.conf: line 115: rootdn is always granted unlimited privileges. 
Jun 24 16:24:48 df-services1 slapd[11974]: /etc/ldap/slapd.conf: line 132: rootdn is always granted unlimited privileges. 
Jun 24 16:24:48 df-services1 slapd[11975]: hdb_db_open: database "dc=fosberry,dc=com": alock package is unstable. 
Jun 24 16:24:48 df-services1 slapd[11975]: backend_startup_one: bi_db_open failed! (-1) 
Jun 24 16:24:48 df-services1 slapd[11975]: slapd stopped.

---

### Post by The Foz on 2009-06-26
I have managed to get the slapd working from the slapd.conf file.

It seems that the slapadd command is not 100% reliable, so you just have to keep cleaning the database, and re-adding the data, and then restarting the daemon, until it works.

I did notice that there seemed to be a problem with a file in the /var/lib/ldap directory having the wrong owner & group, so after each slapadd I did a "sudo chown openldap /var/lib/ldap/*" and "sudo chgrp openldap /var/lib/ldap/*".

Once I have everything configured as I want, I will try to create an ldif configuration from the slapd.conf file using the command "slapd -f /etc/ldap/slapd.conf -F /etc/slapd.d".

---

### Post by mwallette on 2010-05-21
I don't normally reply to year-old posts, but I thought I would add this for anyone else running into this problem.  I was getting the same errors in /var/log/syslog when trying to start openldap in a new installation:

```
May 21 11:02:34 cartman2 slapd[29237]: hdb_db_open: "dc=example,dc=com"
May 21 11:02:34 cartman2 slapd[29237]: hdb_db_open: database "dc=example,dc=com": alock package is unstable.
May 21 11:02:34 cartman2 slapd[29237]: backend_startup_one (type=hdb, suffix="dc=example,dc=com"): bi_db_open failed! (-1)
May 21 11:02:34 cartman2 slapd[29237]: slapd shutdown: initiated
May 21 11:02:34 cartman2 slapd[29237]: ====> bdb_cache_release_all
May 21 11:02:34 cartman2 slapd[29237]: slapd destroy: freeing system resources.
May 21 11:02:34 cartman2 slapd[29237]: slapd stopped.
```

After a quick Google search, I found an indication that it might be a permissions problem on the LDAP database.  Looking at /var/lib/ldap, the permissions looked good (owned by openldap:openldap and mode 750 for the directory), but the actual database files inside /var/lib/ldap were owned by root:root with mode 640.  After running...:
```
#chown -R openldap:openldap /var/lib/ldap/*
#chmod 640 /var/lib/ldap/*
```
I was able to start openldap.  HTH!

---

