---
title: "Problems with Postfix and SASL after update"
date: 2014-05-08
forum: Server Platforms
---

### Post by omael on 2014-05-08
Hello,

i was running smoothly with postfix and sasl configured in 10.04 LTS and after an update today sasl stopped working, i've been reading around the forums and can't find a possible solution.

I originally installed my server with this tutorial [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

My problem is that the authentification with sasl is failing:
```
 May  8 17:58:36 www postfix/smtpd[2612]: connect from unknown[201.161.22.18]May  8 17:58:36 www postfix/smtpd[2620]: warning: unknown[201.161.22.18]: SASL NTLM authentication failed: authentication failure
May  8 17:58:36 www postfix/smtpd[2620]: warning: SASL authentication failure: unable to canonify user and get auxprops
May  8 17:58:36 www postfix/smtpd[2620]: warning: unknown[201.161.22.18]: SASL DIGEST-MD5 authentication failed: authentication failure
May  8 17:58:36 www postfix/smtpd[2620]: warning: unknown[201.161.22.18]: SASL LOGIN authentication failed: authentication failure
May  8 17:58:36 www postfix/smtpd[2620]: lost connection after AUTH from unknown[201.161.22.18]
May  8 17:58:36 www postfix/smtpd[2620]: disconnect from unknown[201.161.22.18]

```
I don't know why is trying digest-md5 if i only enabled login and plain in /etc/postfix/sasl/smtp.conf
```
pwcheck_method: saslauthd auxpropmech_list: plain login
log_level: 7
allow_plaintext: true
auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passw: PASSWORD
sql_database: maildb
sql_select: select clear from users where id='%u@%r' and enabled = 1

```

And this is failing even when after i used testsaslauthd it return success
```

root@www:/etc/postfix/sasl# testsaslauthd -u omael -p PASSWORD -s smtp -r DOMAIN.com

```

I've read around and found that it may be a problem with the version, but i think i have the latest
```
# saslauthd -vsaslauthd 2.1.25
authentication mechanisms: sasldb getpwent kerberos5 pam rimap shadow ldap
```
Also when i check this there's no mysql or sql mechanism.

I'm also checking the log from /var/log/auth.log and finding something interesting
```
May  8 18:05:02 www postfix/smtpd[4371]: NTLM server step 1May  8 18:05:02 www postfix/smtpd[4371]: client flags: ffff8207
May  8 18:05:02 www postfix/smtpd[4371]: NTLM server step 2
May  8 18:05:02 www postfix/smtpd[4371]: client user: omael
May  8 18:05:02 www postfix/smtpd[4371]: client domain: DOMAIN.com
May  8 18:05:02 www CRON[4513]: pam_unix(cron:session): session closed for user omael

```


Here's my relevant part from /etc/postfix/main.cf
```

smtpd_recipient_restrictions = reject_unauth_pipelining,permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unknown_sender_domain, reject_unauth_destination, permit

#saslsmtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain=pcsmexico.com

```

In a couple of post i see that you need to remove [COLOR=#111111][FONT=Consolas]libsasl2-modules-sql [/FONT][/COLOR]So i uninstalled it, don't know if this is causing problems, or why should i remove it if i'm using auxprop plugin mysql.

Why it isn't working when the testsaslauthd is working flawlessly?


Thanks in advance for your attention

---

### Post by omael on 2014-05-09
I changed the smtp.conf and it started working, but i don't know why, does anyone knows the answer?
```

log_level: 7
pwcheck_method: auxprop
auxprop_plugin: sql
#allow_plaintext: true
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passwd: PASSWORD
sql_database: maildb
sql_select: sELect clear from users where id='%u@%r' and enabled = 1

```

---

