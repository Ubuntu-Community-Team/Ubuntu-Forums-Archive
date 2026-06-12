---
title: "[SOLVED] Kolab web admin just gives blank page"
date: 2007-12-06
forum: Server Platforms
---

### Post by pwaldo on 2007-12-06
Hi all,

I've been trying to evaluate Kolab for days now. Tried the build from source route, but no luck.  I'm running **64 bit Kubuntu Gutsy**, and I think the 64 bit-ness is the problem.

Anyway, I installed the kolabd package and all of its dependencies. I successfully ran kolab_bootstrap and started up all of the services.  I hit the URL [https://mysever/admin](https://mysever/admin) and all I get is a blank page.

The first problem I have is that slapd will not stay up when executed from the init script:
```
root@kolab2:/var/log# ps -efw|grep slap
root      3644  3478  0 12:28 pts/0    00:00:00 grep slap
root@kolab2:/var/log# /etc/init.d/slapd start
Starting OpenLDAP: slapd.
root@kolab2:/var/log# ps -efw|grep slap
root      3652  3478  0 12:29 pts/0    00:00:00 grep slap

```
The weird thing is that if I start up manually it stays up...
```
root@kolab2:~# /usr/sbin/slapd -- -g openldap -u openldap
root@kolab2:~# ps -efw|grep slap
root      3686     1  0 12:33 ?        00:00:00 /usr/sbin/slapd -- -g openldap -u openldap
root      3689  3478  0 12:33 pts/0    00:00:00 grep slap

```

OK, so lets assume I can get slapd to stay up.  I now need to restart the processes that depend on LDAP.  Now that they can talk to LDAP, they won't authenticate:
```
root@kolab2:~# /etc/init.d/kolab-cyrus restart
Stopping Cyrus IMAPd: cyrmaster.
Waiting for complete shutdown...
Starting Cyrus IMAPd: cyrmaster.
root@kolab2:~# tail /var/log/syslog
Dec  6 12:38:16 kolab2 cyrus/ctl_cyrusdb[3731]: checkpointing cyrus databases
Dec  6 12:38:16 kolab2 cyrus/ctl_cyrusdb[3731]: archiving database file: /var/lib/cyrus/annotations.db
Dec  6 12:38:16 kolab2 cyrus/master[3732]: about to exec /usr/lib/cyrus/bin/notifyd
Dec  6 12:38:16 kolab2 cyrus/notify[3732]: executed
Dec  6 12:38:16 kolab2 cyrus/ctl_cyrusdb[3731]: archiving log file: /var/lib/cyrus/db/log.0000000001
Dec  6 12:38:16 kolab2 cyrus/ctl_cyrusdb[3731]: archiving database file: /var/lib/cyrus/mailboxes.db
Dec  6 12:38:16 kolab2 cyrus/ctl_cyrusdb[3731]: archiving log file: /var/lib/cyrus/db/log.0000000001
Dec  6 12:38:16 kolab2 cyrus/ctl_cyrusdb[3731]: archiving log file: /var/lib/cyrus/db/log.0000000001
Dec  6 12:38:16 kolab2 cyrus/ctl_cyrusdb[3731]: done checkpointing cyrus databases
Dec  6 12:38:16 kolab2 cyrus/master[3727]: process 3731 exited, status 0
root@kolab2:~# /etc/init.d/kolabd restart
 * Stopping Kolab server kolabd                                                                                  [ OK ]
 * Starting Kolab server kolabd                                                                                  [ OK ]
root@kolab2:~# tail /var/log/syslog
Dec  6 12:38:48 kolab2 kolabd[3625]: Kolab is shutting down
Dec  6 12:38:50 kolab2 C Error: Unable to bind to DN `cn=manager,cn=internal,dc=waldo,dc=home'
Dec  6 12:38:50 kolab2 C Error: Unable to find kolab object `k=kolab,dc=waldo,dc=home'
Dec  6 12:38:50 kolab2 kolabd[3760]: Kolab is starting up
Dec  6 12:38:50 kolab2 cyrus/master[3765]: about to exec /usr/lib/cyrus/bin/imapd
Dec  6 12:38:50 kolab2 cyrus/imap[3765]: executed
Dec  6 12:38:50 kolab2 cyrus/imap[3765]: accepted connection
Dec  6 12:38:50 kolab2 cyrus/imap[3765]: ldap_simple_bind() failed 2 (Protocol error)
Dec  6 12:38:50 kolab2 cyrus/imap[3765]: ldap_simple_bind() failed 2 (Protocol error)
Dec  6 12:38:50 kolab2 cyrus/imap[3765]: badlogin: localhost [127.0.0.1] plaintext manager SASL(-13): authentication failure: checkpass failed

```

Any help is greatly appreciated!

---

### Post by reckless2k2 on 2007-12-06
i had nightmares trying to get kolab and hula to work. i did a bit of troubleshooting and queries in various forums. i could not get around the issues with either. 

i ended up installing zimbra and have been very happy. i don't know if that helps you but it is well documented and very easy install for ubuntu. 

i've been using zimbra for a little over a year.

---

### Post by pwaldo on 2007-12-06
> **reckless2k2 said:**
> 
i ended up installing zimbra and have been very happy. i don't know if that helps you but it is well documented and very easy install for ubuntu. 

Zimbra is going to be my backup plan, but I really want the integration with Kontact...

---

### Post by pwaldo on 2007-12-10
Anybody at all using Kolab???

---

### Post by reckless2k2 on 2007-12-11
well i know they make it look easy in the tutorial/picture. hahaha. but then again the burger doesn't look nearly as nice in person as it does look in the commercial. hahaha. get my drift?

---

### Post by pwaldo on 2007-12-14
OK, so nobody uses Kolab....

I did try the latest beta and built from source.  That seems to be running OK.

---

