---
title: "MySQL / PAM Authentication"
date: 2009-05-05
forum: Security
---

### Post by lightnb on 2009-05-05
I'm trying to set-up mysql authentication on Ubuntu server 8.10.

There's very little documentation on how to do this, so alot of this is guesswork.... but when I added the common-auth line that's supposed to add Mysql as an authentication source, I can't login using either a mysql user (from the `Users` table) or as a regular system user.

Here's my common-auth file:

```

# here are the per-package modules (the "Primary" block)
auth    [success=2 default=ignore]      pam_unix.so nullok_secure
auth    [success=1 default=ignore]      pam_ldap.so use_first_pass

# Adding MySQL as an authentication method...
auth required /lib/security/pam_mysql.so user=root passwd=secret54 host=localhost db=AuthTest table=Users usercolumn=UserName passwdcolumn=Password crypt=0

# here's the fallback if no module succeeds
auth    requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth    optional                        pam_smbpass.so migrate
auth    optional        pam_ecryptfs.so unwrap
# end of pam-auth-update config

```

Any ideas?

Thanks,

Nick

---

### Post by lightnb on 2009-05-08
More details:

Trying to change/set a password for a user via

```
passwd jdoe
```
yields the error:

```
passwd: Failed preliminary check by password service
passwd: password unchanged
```

Auth.log shows:
```

May  8 05:51:56 balrogjr2 passwd[5031]: pam_unix(passwd:chauthtok): user "jdoe" does not exist in /etc/passwd
May  8 05:51:56 balrogjr2 passwd[5031]: pam_mysql - MySQL error (You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'FROM user WHERE user.user_name = 'jdoe'' at line 1)

```


At the same time, the MySQL log shows:
```

090508  5:58:34	    142 Connect     nss@localhost on nss_mysql
		    142 Query       select user.user_name,user.uid,NULL,user.realname,user.shell,user.homedir,user.gid from user where user.user_name='jdoe' and user.uid is not null and user.status = 'A' order by user.uid
		    143 Connect     nss-shadow@localhost on nss_mysql
		    143 Init DB     nss_mysql
		    143 Query       SELECT 0,  FROM user WHERE user.user_name = 'jdoe'
		    143 Quit       
		    142 Quit

```

It seems that the module is sending invalid queries... The question is, how can it be fixed?

---

