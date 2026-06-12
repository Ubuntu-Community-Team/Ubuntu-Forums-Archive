---
title: "Connection from samba to LDAP server failed"
date: 2014-01-30
forum: Server Platforms
---

### Post by masoodmx on 2014-01-30
I use samba and LDAP for file sharing and directory service.
Some days ago, I noticed that samba has problem in connection to the LDAP service while beforehand it was working properly. But still the shared directories were accessible. After restarting the smbd service, it is not accessible anymore. So, there are lots of necessary files unavailable for people in the network!
Any help?

The samba log file has reported:

[COLOR=#696969][2014/01/30 11:21:59,  1] lib/smbldap.c:1265(another_ldap_try)
  Connection to LDAP server failed for the 1 try!
[2014/01/30 11:22:00,  1] lib/smbldap.c:1265(another_ldap_try)
  Connection to LDAP server failed for the 2 try!
[2014/01/30 11:22:01,  1] lib/smbldap.c:1265(another_ldap_try)
  Connection to LDAP server failed for the 3 try!
[2014/01/30 11:22:02,  1] lib/smbldap.c:1265(another_ldap_try)
  .
  .  (the number is just counted up)
  .
  Connection to LDAP server failed for the 13 try!
[2014/01/30 11:22:12,  1] lib/smbldap.c:1265(another_ldap_try)
  Connection to LDAP server failed for the 14 try!
[2014/01/30 11:22:13,  1] lib/smbldap.c:1265(another_ldap_try)
  Connection to LDAP server failed for the 15 try!
[2014/01/30 11:22:14,  0] smbd/server.c:1201(main)
  ERROR: failed to setup guest info.
[2014/01/30 11:22:14,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2014/01/30 11:22:14,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2014/01/30 11:22:14,  0] lib/smbldap.c:1086(smbldap_connect_system)
  failed to bind to server ldapi:/// with dn="uid=samba,ou=system-accounts,dc=example,dc=com" Error: Invalid credentials
        (unknown)

[/COLOR]some corresponding system logs:[COLOR=#696969]

[/COLOR][COLOR=#696969][FONT=Verdana]Jan 30 14:27:34 atom-lan slapd[2320]: connection_read(24): no connection![/FONT][/COLOR]
[COLOR=#696969]Jan 30 14:27:35 atom-lan winbindd[2872]: [2014/01/30 14:27:35,  0] lib/smbldap.c:656(smbldap_store_state)
Jan 30 14:27:35 atom-lan winbindd[2872]:   PANIC: assert failed at lib/smbldap.c(656): tmp_ldap_state == smbldap_state
.
. (repetition)
.
Jan 30 14:42:55 atom-lan init: smbd main process (5977) terminated with status 255
Jan 30 14:42:55 atom-lan init: smbd main process ended, respawning
Jan 30 14:42:55 atom-lan smbd[6037]: [2014/01/30 14:42:55,  0] smbd/server.c:1115(main)
Jan 30 14:42:55 atom-lan smbd[6037]:   standard input is not a socket, assuming -D option
Jan 30 14:42:55 atom-lan smbd[6037]: [2014/01/30 14:42:55,  0] lib/smbldap.c:1086(smbldap_connect_system)
Jan 30 14:42:55 atom-lan smbd[6037]:   failed to bind to server ldapi:/// with dn="uid=samba,ou=system-accounts,dc=example,dc=com" Error: Invalid credentials
[/COLOR]

---

### Post by SeijiSensei on 2014-01-30
I'm no expert on this, but what about the error
```
failed to bind to server ldapi:/// with dn="uid=samba,ou=system-accounts,dc=example,dc=com" Error: Invalid credentials
```
There doesn't seem to be a server name in the ldapi:/// URL.  Should there be?

---

