---
title: "Postgresql with PAM-LDAP generating errors"
date: 2007-12-16
forum: Server Platforms
---

### Post by delerious010 on 2007-12-16
Ok, so I've got Postgresql authenticating through pam-ldap.
My users can logging and access the databases but on each login attempt I get the following syslog error : 

[From the remote webserver]
authpriv  notice  authentication  pam_unix(postgresql:auth): authentication failure; logname= uid=107 euid=107 tty= ruser= rhost= user=serafini

[From local psql]
 18:44:33  	 cybrain  	 authpriv  	 notice  	 authentication  	 pam_unix(postgresql:auth): authentication failure; logname= uid=107 euid=107 tty= ruser= rhost= user=serafini
18:44:30 	cybrain 	authpriv 	notice 	authentication 	pam_unix(postgresql:auth): authentication failure; logname= uid=107 euid=107 tty= ruser= rhost= user=serafini
18:44:29 	cybrain 	authpriv 	crit 	authentication 	pam_unix(postgresql:auth): auth could not identify password for [serafini]
18:44:29 	cybrain 	authpriv 	err 	authentication 	pam_unix(postgresql:auth): conversation failed

uid=107 is postgresql
user=serafini is a user in the LDAP database

[/etc/postgresql/8.2/main/pg_hba.conf] contains 
host    all         all         10.0.0.0/24          pam postgresql

[/etc/pam,d/postgresql] contains
@include common-auth
@include common-account

[/etc/pam.d/common-auth] contains
auth        required     pam_env.so
auth        sufficient   pam_unix.so likeauth nullok
auth        sufficient   pam_ldap.so use_first_pass
auth        required     pam_deny.so

[/etc/pam.d/common-account] contains
#account     required     pam_access.so accessfile=/etc/security/access.conf
account     sufficient   pam_ldap.so
account     sufficient   pam_unix.so
account     required     pam_deny.so

Anyone have an idea ?

---

