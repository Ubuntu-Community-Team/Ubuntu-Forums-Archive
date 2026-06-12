---
title: "ubuntu server 14.04 + postfix + saslauth + crypt"
date: 2016-04-02
forum: Server Platforms
---

### Post by daemoncesar on 2016-04-02
[COLOR=#474B51][FONT=Tahoma]I can not send email encryption.  I using postfix + courier-imap + saslauth.[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]
[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]My smtpd.conf[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]
[/FONT][/COLOR]
```

pwcheck_method: saslauthd
auxprop_plugin: sql
mech_list: PLAIN LOGIN CRAM-MD5 DIGEST-MD5 NTLM
srp_mda: md5
password_format: crypt
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: postfix
sql_passwd: postsol
sql_database: postfix
sql_select: select password from mailbox where username='%u@%r'



```
[COLOR=#474B51][FONT=Tahoma]main.cf[/FONT][/COLOR]
```

[COLOR=#474B51][FONT=Tahoma]smtpd_sasl_auth_enable = yes[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]smtpd_sasl_security_options = noanonymous[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]smtpd_sasl_local_domain =[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]broken_sasl_auth_clients = yes[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]smtpd_sasl_authenticated_header = yes[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]
[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]smtpd_sasl_path = smtpd[/FONT][/COLOR]

```
[COLOR=#474B51][FONT=Tahoma]
[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]/etc/pam.d/smtp[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]
[/FONT][/COLOR]
```

[COLOR=#474B51][FONT=Tahoma]auth    required   pam_mysql.so user=postfix passwd=postsol host=127.0.0.1 db=postfix table=mailbox usercolumn=username passwdcolumn=password crypt=2[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]account sufficient pam_mysql.so user=postfix passwd=postsol host=127.0.0.1 db=postfix table=mailbox usercolumn=username passwdcolumn=password crypt=2[/FONT][/COLOR]

```
[COLOR=#474B51][FONT=Tahoma]
[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]the error:[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]
[/FONT][/COLOR]```

[COLOR=#474B51][FONT=Tahoma]Apr  2 10:42:01 protus  saslauthd[17305]: do_auth         : auth failure: [user=root@mydomain.com] [service=smtp] [realm=] [mech=pam] [reason=PAM auth error][/FONT][/COLOR]

```

[COLOR=#474B51][FONT=Tahoma]
[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]If you use the password normally ( No encryption) works![/FONT][/COLOR]

---

### Post by daemoncesar on 2016-04-02
i change /etc/pam.d/smtp (cryp=3)
```



[COLOR=#474B51][FONT=Ubuntu Mono][FONT=Tahoma]auth    required   pam_mysql.so user=postfix passwd=postsol host=127.0.0.1 db=postfix table=mailbox usercolumn=username passwdcolumn=password crypt=3
[/FONT][/FONT][/COLOR][COLOR=#474B51][FONT=Ubuntu Mono][FONT=Tahoma]account sufficient pam_mysql.so user=postfix passwd=postsol host=127.0.0.1 db=postfix table=mailbox usercolumn=username passwdcolumn=password crypt=3

[/FONT][/FONT][/COLOR]
```[COLOR=#474B51][FONT=Ubuntu Mono][FONT=Tahoma]

[/FONT][/FONT][/COLOR]The value of "crypt" is 3 ?
[COLOR=#474B51][FONT=Ubuntu Mono][FONT=Tahoma]
error:

[/FONT][/FONT][/COLOR]pam_mysql - non-crypt()ish MD5 hash is not supported in this build.

---

### Post by daemoncesar on 2016-04-03
```

root@protus:/etc/postfix/sasl# testsaslauthd -s smtp -u root@domain.com -p  passw
0: OK "Success."



```




But thunderbird does not work ;

---

