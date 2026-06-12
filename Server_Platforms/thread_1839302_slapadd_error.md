---
title: "slapadd error"
date: 2011-09-05
forum: Server Platforms
---

### Post by SwitchLink on 2011-09-05
```
Old server:
Linux 2.6.22-14-server #1 SMP Tue Feb 12 03:10:53 UTC 2008 x86_64
(Ubuntu 7.10)
@(#) $OpenLDAP: slapd 2.3.35 (Mar  5 2008 15:13:34) $
        buildd@king:/build/buildd/openldap2.3-2.3.35/debian/build/servers/slapd


New Server:
Ubuntu 11.04 (GNU/Linux 2.6.38-8-server x86_64)
@(#) $OpenLDAP: slapd 2.4.23 (Apr  7 2011 18:00:55) $
        buildd@allspice:/build/buildd/openldap-2.4.23/debian/build/servers/slapd
```


I am trying to migrate my ldap from one server to another.  An LDIF has been exported from the old server.  I exported the data from the old server using 

```
slapcat -l
```

I install slapd on the new server: 

```
apt-get install slapd ldap-utils
```

I verified slapd was working on the new server (clean install, able to administrate and connect using jexplorer).  I verified the slapd.conf and DB_CONFIG files on the new server against the old, and to the best of my knowledge, everything looked good.  I added some lines to the DB_CONFIG, how much memory it should use, etc.

```
set_cachesize 8 0 16
set_lk_max_objects 1500
set_lk_max_locks 1500
set_lk_max_lockers 1500
set_flags DB_LOG_AUTOREMOVE
```


I stopped slapd, removed the database file from the new server.

```
cd /var/lib/ldap/
rm *__db.* *.bdb alock log.*
```

Imported the data using:

```
sudo slapadd -l Fullbackup-09-03-11.ldif
```

It took about 20 hours to complete and ended with the following message:

```
Closing DB...Error, entries missing!
entry 1: dc=domain,dc=com
entry 2: dc=ldap,dc=domain,dc=com
```

I've done some searching around on the net and I think the solution might be something simple but haven't found my exact problem.

Is there a log file or something I can look at or a quick command I can run that might give me a hint as to what is wrong?

I can't post the contents of the ldif file because it's over 2GB in size, but if there is a section that might be helpful to look at, I can certainly post that.

As always, all help is greatly appreciated.

---

### Post by SwitchLink on 2011-10-17
The problem stemmed from the fact that the configuration files (rootDSE) had the suffix as dc=domain,dc=com.

I'm not entirely sure how everything works, I just knew that I needed my base DN to be dc=prod,dc=ldap,dc=domain,dc=com.  I did that by editing the config files directly, then importing the ldif.

[http://ubuntuforums.org/showthread.php?t=1860022]("http://ubuntuforums.org/showthread.php?t=1860022")

Not saying what I did was right, but for lack of any knowledge to the contrary, I'm sharing. :)

---

