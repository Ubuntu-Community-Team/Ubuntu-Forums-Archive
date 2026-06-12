---
title: "SMTP Relay Client Authentication"
date: 2010-01-16
forum: Server Platforms
---

### Post by michellez on 2010-01-16
Hi,

I'm getting myself confused here, even more so when searching and working out what I need :(

My aim:
1, Clients on the local subnet can send via the mail server with out authenticating
2, Clients connecting externally are required to authenticate (with the same system account they would use with (Courier)IMAP/SquirrelMaill etc) - So I don't have an open relay!

Can any one provide a pointer/link/etc?

Thanks!
Michelle

---

### Post by xerophyte on 2010-01-16
You have to give us more info like what kind of MTA you are using for your email system 

for example if you use SASL with your MTA 

[http://www.ltrr.arizona.edu/~mmunro/ldapmail/saslauthdata.gif](http://www.ltrr.arizona.edu/~mmunro/ldapmail/saslauthdata.gif)

---

### Post by michellez on 2010-01-16
Hi,

Yes, sorry, I was vague!

Using Postfix and SASL with 'shadow'. I'm think shadow is what I want? I just want people to auth as a system user. Think I'm *nearly* there.

Getting the following in my mail log though:
```
postfix/smtpd[24521]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
postfix/smtpd[24521]: warning: SASL authentication failure: no secret in database
postfix/smtpd[24521]: warning: host1[ip1]: SASL NTLM authentication failed: authentication failure
postfix/smtpd[24521]: warning: SASL authentication failure: realm changed: authentication aborted
postfix/smtpd[24521]: warning: host1[ip1]: SASL DIGEST-MD5 authentication failed: authentication failure
postfix/smtpd[24521]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
last message repeated 2 times
postfix/smtpd[24521]: warning: host1[ip1]: SASL LOGIN authentication failed: authentication failure
postfix/smtpd[24521]: lost connection after AUTH from host1[ip1]
postfix/smtpd[24521]: disconnect from host1[ip1]

```

I have checked /etc/sasldb2 does exist (I chmod'd it 755 incase? :s):
```
:~$ ls -la /etc/ |  grep sasldb2
-rwxr-xr-x   1 root sasl    12288 2010-01-10 22:27 sasldb2

```

File: /etc/postfix/sasl/smtpd.conf
```
pwcheck_method: saslauthd
mech_list: plain login
```

^^ though I would like it not plain in the end - trying to walk before running though here ;)

File: /etc/default/saslauthd
```
START=yes
PWDIR="/var/spool/postfix/var/run/saslauthd"
PARAMS="-m ${PWDIR}"
PIDFILE="${PWDIR}/saslauthd.pid"
DESC="SASL Authentication Daemon"
NAME="saslauthd"
MECHANISMS="shadow"
MECH_OPTIONS=""
OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd"
```

File: /etc/postfix/main.cf
```
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
#smtpd_sasl_security_options = noanonymous,noplaintext
smtpd_sasl_security_options = noanonymous
smtpd_sasl_path = saslauthd
broken_sasl_auth_clients = yes

```

Think I'm going to head to bed now and look at this fresh tomorrow! Any suggestions though, please :)

Thanks,
Michelle

---

