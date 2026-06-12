---
title: "Postfix and SASL"
date: 2008-02-28
forum: Server Platforms
---

### Post by Palcrypt on 2008-02-28
I'm having some serious problems with sending mail. I have Webmin/Virtualmin/Usermin installed on my server to help in the creation of virtual domains. If I log into Usermin and send mail from one of the virtual domains that way everything is fine except that the mail shows up on the other end as being from my machinename instead of the domain name. 

I can receive mail just fine in a client program. However, when sending from a client the smtp server continuously rejects my password. I've tried telnetting in and using AUTH PLAIN and the base64 encoded string and it's still rejected. I'm going to post my post my postfix main.cf file and the messages from my error logs. I really need help on this.

postfix main.cf file
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
smtpd_sasl_local_domain =
myhostname = lonewolf
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = lonewolf, localhost.localdomain, , localhost
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
virtual_alias_maps = hash:/etc/postfix/virtual
smtpd_recipient_restrictions = permit_mynetworks permit_inet_interfaces permit_sasl_authenticated permit_mx_backup reject_unauth_destination
mynetworks = 127.0.0.0/8
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
myorigin = $mydomain

```

/var/log/mail.log file on one send attempt
```
Feb 28 13:45:21 lonewolf postfix/smtpd[6293]: connect from 97-81-109-22.dhcp.athn.ga.charter.com[97.81.109.22]
Feb 28 13:45:25 lonewolf postfix/smtpd[6293]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Feb 28 13:45:25 lonewolf postfix/smtpd[6293]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Feb 28 13:45:25 lonewolf postfix/smtpd[6293]: warning: SASL authentication failure: no secret in database
Feb 28 13:45:25 lonewolf postfix/smtpd[6293]: warning: 97-81-109-22.dhcp.athn.ga.charter.com[97.81.109.22]: SASL CRAM-MD5 authentication failed: authentication failure
Feb 28 13:45:25 lonewolf postfix/smtpd[6293]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Feb 28 13:45:25 lonewolf postfix/smtpd[6293]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Feb 28 13:45:25 lonewolf postfix/smtpd[6293]: warning: SASL authentication failure: no secret in database
Feb 28 13:45:25 lonewolf postfix/smtpd[6293]: warning: 97-81-109-22.dhcp.athn.ga.charter.com[97.81.109.22]: SASL NTLM authentication failed: authentication failure
Feb 28 13:45:25 lonewolf postfix/smtpd[6293]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Feb 28 13:45:25 lonewolf last message repeated 4 times
Feb 28 13:45:25 lonewolf postfix/smtpd[6293]: warning: SASL authentication failure: Password verification failed
Feb 28 13:45:25 lonewolf postfix/smtpd[6293]: warning: 97-81-109-22.dhcp.athn.ga.charter.com[97.81.109.22]: SASL PLAIN authentication failed: authentication failure
Feb 28 13:45:25 lonewolf postfix/smtpd[6293]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Feb 28 13:45:25 lonewolf last message repeated 5 times
Feb 28 13:45:25 lonewolf postfix/smtpd[6293]: warning: 97-81-109-22.dhcp.athn.ga.charter.com[97.81.109.22]: SASL LOGIN authentication failed: authentication failure
```

/var/log/auth.log file message from a send attempt
```

Feb 28 13:45:25 lonewolf postfix/smtpd[6293]: NTLM server step 1 
Feb 28 13:45:25 lonewolf postfix/smtpd[6293]: client flags: ffff8207
Feb 28 13:45:25 lonewolf postfix/smtpd[6293]: NTLM server step 2 
Feb 28 13:45:25 lonewolf postfix/smtpd[6293]: client user: paul.paulromerproductions

```

---

### Post by Palcrypt on 2008-02-29
Ok. It appears, and I might be wrong, that my problem is that it is trying to use sasl2db to authenticate when i want it to use saslauthd. I can't figure out how to tell it to use saslauthd though.

---

### Post by Mr. C. on 2008-02-29
Show output of postconf -n and saslfinger:

[http://postfix.state-of-mind.de/patrick.koetter/saslfinger/](http://postfix.state-of-mind.de/patrick.koetter/saslfinger/)

MrC

---

### Post by Palcrypt on 2008-02-29
results of saslfinger -s

```

saslfinger - postfix Cyrus sasl configuration Fri Feb 29 09:43:00 EST 2008
version: 1.0.2
mode: server-side SMTP AUTH

-- basics --
Postfix: 2.4.7
System: Ubuntu 7.10 \n \l

-- smtpd is linked to --
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0xb7d4b000)

-- active SMTP AUTH and TLS parameters for smtpd --
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes


-- listing of /usr/lib/sasl2 --
total 840
drwxr-xr-x   2 root root  4096 2008-02-28 13:22 .
drwxr-xr-x 165 root root 53248 2008-02-28 12:08 ..
-rw-r--r--   1 root root 13640 2007-10-02 09:58 libanonymous.a
-rw-r--r--   1 root root   862 2007-10-02 09:58 libanonymous.la
-rw-r--r--   1 root root 13208 2007-10-02 09:58 libanonymous.so
-rw-r--r--   1 root root 13208 2007-10-02 09:58 libanonymous.so.2
-rw-r--r--   1 root root 13208 2007-10-02 09:58 libanonymous.so.2.0.22
-rw-r--r--   1 root root 15974 2007-10-02 09:58 libcrammd5.a
-rw-r--r--   1 root root   848 2007-10-02 09:58 libcrammd5.la
-rw-r--r--   1 root root 15672 2007-10-02 09:58 libcrammd5.so
-rw-r--r--   1 root root 15672 2007-10-02 09:58 libcrammd5.so.2
-rw-r--r--   1 root root 15672 2007-10-02 09:58 libcrammd5.so.2.0.22
-rw-r--r--   1 root root 47348 2007-10-02 09:58 libdigestmd5.a
-rw-r--r--   1 root root   871 2007-10-02 09:58 libdigestmd5.la
-rw-r--r--   1 root root 43916 2007-10-02 09:58 libdigestmd5.so
-rw-r--r--   1 root root 43916 2007-10-02 09:58 libdigestmd5.so.2
-rw-r--r--   1 root root 43916 2007-10-02 09:58 libdigestmd5.so.2.0.22
-rw-r--r--   1 root root 13650 2007-10-02 09:58 liblogin.a
-rw-r--r--   1 root root   842 2007-10-02 09:58 liblogin.la
-rw-r--r--   1 root root 14036 2007-10-02 09:58 liblogin.so
-rw-r--r--   1 root root 14036 2007-10-02 09:58 liblogin.so.2
-rw-r--r--   1 root root 14036 2007-10-02 09:58 liblogin.so.2.0.22
-rw-r--r--   1 root root 30516 2007-10-02 09:58 libntlm.a
-rw-r--r--   1 root root   836 2007-10-02 09:58 libntlm.la
-rw-r--r--   1 root root 29876 2007-10-02 09:58 libntlm.so
-rw-r--r--   1 root root 29876 2007-10-02 09:58 libntlm.so.2
-rw-r--r--   1 root root 29876 2007-10-02 09:58 libntlm.so.2.0.22
-rw-r--r--   1 root root 13938 2007-10-02 09:58 libplain.a
-rw-r--r--   1 root root   842 2007-10-02 09:58 libplain.la
-rw-r--r--   1 root root 14036 2007-10-02 09:58 libplain.so
-rw-r--r--   1 root root 14036 2007-10-02 09:58 libplain.so.2
-rw-r--r--   1 root root 14036 2007-10-02 09:58 libplain.so.2.0.22
-rw-r--r--   1 root root 22150 2007-10-02 09:58 libsasldb.a
-rw-r--r--   1 root root   863 2007-10-02 09:58 libsasldb.la
-rw-r--r--   1 root root 18356 2007-10-02 09:58 libsasldb.so
-rw-r--r--   1 root root 18356 2007-10-02 09:58 libsasldb.so.2
-rw-r--r--   1 root root 18356 2007-10-02 09:58 libsasldb.so.2.0.22
-rw-r--r--   1 root root 23812 2007-10-02 09:58 libsql.a
-rw-r--r--   1 root root   971 2007-10-02 09:58 libsql.la
-rw-r--r--   1 root root 23352 2007-10-02 09:58 libsql.so
-rw-r--r--   1 root root 23352 2007-10-02 09:58 libsql.so.2
-rw-r--r--   1 root root 23352 2007-10-02 09:58 libsql.so.2.0.22
-rw-r--r--   1 root root    49 2008-02-29 00:23 smtpd.conf




-- content of /usr/lib/sasl2/smtpd.conf --
pwcheck_method: saslauthd
mech_list: plain login


-- active services in /etc/postfix/master.cf --
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
smtp      inet  n       -       -       -       -       smtpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      unix  -       -       -       -       -       smtp
relay     unix  -       -       -       -       -       smtp
        -o smtp_fallback_relay=
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

-- mechanisms on localhost --
250-AUTH LOGIN NTLM DIGEST-MD5 PLAIN CRAM-MD5
250-AUTH=LOGIN NTLM DIGEST-MD5 PLAIN CRAM-MD5


-- end of saslfinger output --
```

results of saslfinger -c

```

saslfinger - postfix Cyrus sasl configuration Fri Feb 29 09:45:08 EST 2008
version: 1.0.2
mode: client-side SMTP AUTH

-- basics --
Postfix: 2.4.7
System: Ubuntu 7.10 \n \l

-- smtp is linked to --
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0xb7ce1000)

-- active SMTP AUTH and TLS parameters for smtp --
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache


-- listing of /usr/lib/sasl2 --
total 840
drwxr-xr-x   2 root root  4096 2008-02-28 13:22 .
drwxr-xr-x 165 root root 53248 2008-02-28 12:08 ..
-rw-r--r--   1 root root 13640 2007-10-02 09:58 libanonymous.a
-rw-r--r--   1 root root   862 2007-10-02 09:58 libanonymous.la
-rw-r--r--   1 root root 13208 2007-10-02 09:58 libanonymous.so
-rw-r--r--   1 root root 13208 2007-10-02 09:58 libanonymous.so.2
-rw-r--r--   1 root root 13208 2007-10-02 09:58 libanonymous.so.2.0.22
-rw-r--r--   1 root root 15974 2007-10-02 09:58 libcrammd5.a
-rw-r--r--   1 root root   848 2007-10-02 09:58 libcrammd5.la
-rw-r--r--   1 root root 15672 2007-10-02 09:58 libcrammd5.so
-rw-r--r--   1 root root 15672 2007-10-02 09:58 libcrammd5.so.2
-rw-r--r--   1 root root 15672 2007-10-02 09:58 libcrammd5.so.2.0.22
-rw-r--r--   1 root root 47348 2007-10-02 09:58 libdigestmd5.a
-rw-r--r--   1 root root   871 2007-10-02 09:58 libdigestmd5.la
-rw-r--r--   1 root root 43916 2007-10-02 09:58 libdigestmd5.so
-rw-r--r--   1 root root 43916 2007-10-02 09:58 libdigestmd5.so.2
-rw-r--r--   1 root root 43916 2007-10-02 09:58 libdigestmd5.so.2.0.22
-rw-r--r--   1 root root 13650 2007-10-02 09:58 liblogin.a
-rw-r--r--   1 root root   842 2007-10-02 09:58 liblogin.la
-rw-r--r--   1 root root 14036 2007-10-02 09:58 liblogin.so
-rw-r--r--   1 root root 14036 2007-10-02 09:58 liblogin.so.2
-rw-r--r--   1 root root 14036 2007-10-02 09:58 liblogin.so.2.0.22
-rw-r--r--   1 root root 30516 2007-10-02 09:58 libntlm.a
-rw-r--r--   1 root root   836 2007-10-02 09:58 libntlm.la
-rw-r--r--   1 root root 29876 2007-10-02 09:58 libntlm.so
-rw-r--r--   1 root root 29876 2007-10-02 09:58 libntlm.so.2
-rw-r--r--   1 root root 29876 2007-10-02 09:58 libntlm.so.2.0.22
-rw-r--r--   1 root root 13938 2007-10-02 09:58 libplain.a
-rw-r--r--   1 root root   842 2007-10-02 09:58 libplain.la
-rw-r--r--   1 root root 14036 2007-10-02 09:58 libplain.so
-rw-r--r--   1 root root 14036 2007-10-02 09:58 libplain.so.2
-rw-r--r--   1 root root 14036 2007-10-02 09:58 libplain.so.2.0.22
-rw-r--r--   1 root root 22150 2007-10-02 09:58 libsasldb.a
-rw-r--r--   1 root root   863 2007-10-02 09:58 libsasldb.la
-rw-r--r--   1 root root 18356 2007-10-02 09:58 libsasldb.so
-rw-r--r--   1 root root 18356 2007-10-02 09:58 libsasldb.so.2
-rw-r--r--   1 root root 18356 2007-10-02 09:58 libsasldb.so.2.0.22
-rw-r--r--   1 root root 23812 2007-10-02 09:58 libsql.a
-rw-r--r--   1 root root   971 2007-10-02 09:58 libsql.la
-rw-r--r--   1 root root 23352 2007-10-02 09:58 libsql.so
-rw-r--r--   1 root root 23352 2007-10-02 09:58 libsql.so.2
-rw-r--r--   1 root root 23352 2007-10-02 09:58 libsql.so.2.0.22
-rw-r--r--   1 root root    49 2008-02-29 00:23 smtpd.conf


Cannot find the smtp_sasl_password_maps parameter in main.cf.
Client-side SMTP AUTH cannot work without this parameter!

```

results of postconf -n

```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = lonewolf, localhost.localdomain, , localhost
myhostname = lonewolf
mynetworks = 127.0.0.0/8
myorigin = $mydomain
recipient_delimiter = +
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks permit_inet_interfaces permit_sasl_authenticated permit_mx_backup reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_alias_maps = hash:/etc/postfix/virtual

```

---

### Post by Mr. C. on 2008-02-29
> **Palcrypt said:**
> ...everything is fine except that the mail shows up on the other end as being from my machinename instead of the domain name. 

```
mydestination = lonewolf, localhost.localdomain, , localhost
```

Your mydestination is using an unqualified doain name "lonewolf", and also has an extraneous comma.  Change this to a fully qualified domain name.

```

myhostname = lonewolf
```

Your myhostname is also unqualified - change this the a full qualfied hostname (eg. lonewolf.mydomain.com)

Let's see the contents of : /etc/postfix/virtual

Your SASL mech list shows only two types of SASL methods:

pwcheck_method: saslauthd
mech_list: plain login

Therefore, your client can only use **plain** or **login**.  The **login** mech is only from MS Outlook * clients, and if your client is Outlook, **login** is your only choice.  **Plain** is plain text.  If your client is not Outlook, then you must use **plain** text, or modify your **mech_list** to support the style your client demands.

Your TLS is opportunistic, meaning, not required.  Is that what you want?  This means, if the client fails to chose TLS, it will fall back to unencrypted mode, and when using the plain mechanism, your password crosses the wire unecrypted.

---

### Post by drhiii on 2008-02-29
What if you have a mix of clients that use Outlook, and use other clients?  What syntax do you use then?

I am getting 'relay access not allowed' in my logs and am pulling myhair out trying to figure this out.

---

### Post by Mr. C. on 2008-02-29
> **drhiii said:**
> What if you have a mix of clients that use Outlook, and use other clients?  What syntax do you use then?
That's fine - all mech's will be attempted until one matches.
> **drhiii said:**
> 
I am getting 'relay access not allowed' in my logs and am pulling myhair out trying to figure this out.

The "relay access not allowed" message is not a postfix internal message.  Show the complete log line.

This means that the remote server is not allowing you to use their systems to relay (probably unauthenticated) mail.

---

### Post by Palcrypt on 2008-02-29
> **Mr. C. said:**
> ```
mydestination = lonewolf, localhost.localdomain, , localhost
```

Your mydestination is using an unqualified doain name "lonewolf", and also has an extraneous comma.  Change this to a fully qualified domain name.

```

myhostname = lonewolf
```

Your myhostname is also unqualified - change this the a full qualfied hostname (eg. lonewolf.mydomain.com)


I'm not sure why this matters. I'm sending the mails from a viruttual host.

> 
Let's see the contents of : /etc/postfix/virtual

Your SASL mech list shows only two types of SASL methods:

pwcheck_method: saslauthd
mech_list: plain login

Therefore, your client can only use **plain** or **login**.  The **login** mech is only from MS Outlook * clients, and if your client is Outlook, **login** is your only choice.  **Plain** is plain text.  If your client is not Outlook, then you must use **plain** text, or modify your **mech_list** to support the style your client demands.

Your TLS is opportunistic, meaning, not required.  Is that what you want?  This means, if the client fails to chose TLS, it will fall back to unencrypted mode, and when using the plain mechanism, your password crosses the wire unecrypted.

At this point I've found that my server keeps trying to use sasldb2 to authenticate when I want it to use saslauthd. I can't seem to find the right place to change that.

---

### Post by Mr. C. on 2008-02-29
> **Palcrypt said:**
> I'm not sure why this matters. I'm sending the mails from a viruttual host.
It matters, and should always be an FQDN.  Avoid hidden gotchas.

> **Palcrypt said:**
> 
At this point I've found that my server keeps trying to use sasldb2 to authenticate when I want it to use saslauthd. I can't seem to find the right place to change that.

Your mech_list shows otherwise:
```
-- content of /usr/lib/sasl2/smtpd.conf --
pwcheck_method: saslauthd
mech_list: plain login

```

---

### Post by Mr. C. on 2008-02-29
I see you have a chroot smptd.  See:

[http://www.kloopy.com/344_Postfix__SASL2__unable_to_open_Berkeley_db](http://www.kloopy.com/344_Postfix__SASL2__unable_to_open_Berkeley_db)

---

### Post by Palcrypt on 2008-02-29
/etc/postfix/virtual file
```

paulromerproductions@paulromerproductions.com	paulromerproductions
paulromerproductions.com	paulromerproductions.com
postmaster@paulromerproductions.com	paulromerproductions@paulromerproductions.com
abuse@paulromerproductions.com	paulromerproductions@paulromerproductions.com
webmaster@paulromerproductions.com	paulromerproductions@paulromerproductions.com
hostmaster@paulromerproductions.com	paulromerproductions@paulromerproductions.com
paul@paulromerproductions.com	paul.paulromerproductions
ben@paulromerproductions.com	ben.paulromerproductions
```

I made the other changes, but I still can't authenticate. The responsese now from my auth file is that the user can't be found. It's because it can now find the sasldb2 file. However nothing is there. It's usuing that instead of teh saslauthd, . I'm not sure how to disable sasldb2 and make it check the list of created usersrs  instead of the sasldb2 file.

---

### Post by drhiii on 2008-02-29
As requested, a log entry that shows the error...


The message could not be sent because one of the recipients was rejected by the server. The rejected e-mail address was 'xxxx5366@msn.com'. Subject 'test  1 email', Account: 'abcdefg.com', Server: 'abcdefg.com', Protocol: SMTP, Server Response: '554 5.7.1 <xxxx5366@msn.com>: Relay access denied', Port: 25, Secure(SSL): No, Server Error: 554, Error Number: 0x800CCC79


You suggest this may not be a postfix generated error?  




> **Mr. C. said:**
> That's fine - all mech's will be attempted until one matches.


The "relay access not allowed" message is not a postfix internal message.  Show the complete log line.

This means that the remote server is not allowing you to use their systems to relay (probably unauthenticated) mail.

---

### Post by Mr. C. on 2008-02-29
> **drhiii said:**
> As requested, a log entry that shows the error...


The message could not be sent because one of the recipients was rejected by the server. The rejected e-mail address was 'xxxx5366@msn.com'. Subject 'test  1 email', Account: 'abcdefg.com', Server: 'abcdefg.com', Protocol: SMTP, Server Response: '554 5.7.1 <xxxx5366@msn.com>: Relay access denied', Port: 25, Secure(SSL): No, Server Error: 554, Error Number: 0x800CCC79


You suggest this may not be a postfix generated error?

No, this would be part of a response.  You've cropped and removed important information from the log line.  It is best to show the entire lines, rather than you interpreting for us what you think is best to show.

This is your smtp CLIENT try to send email via hotmail servers.  They do not allow you to relay, because you are not authenticated.

At the bottom of your saslfinger -c output, the message:

> Cannot find the smtp_sasl_password_maps parameter in main.cf.
Client-side SMTP AUTH cannot work without this parameter!

appears.  Did you think this not important?

There is a SASL client and server - are you aware of the differences, and what is required of each?

---

### Post by Palcrypt on 2008-02-29
k. so i think the problem is that the server is running cram-md5 and digest-md5. saslauthd apparantly can't use these, which makes it default to sasldb2. I can't seem to find where to kill these though. They're not listed in teh smtpd.conf, but when i login to the smtp server and run an ehlo command. They're listed in the auth lines.

---

### Post by Mr. C. on 2008-02-29
The error message you showed, was from a response received by the postfix SMTP **client** (eg. postfix/smtp), not the SMTP **server** daemon (postfix/smtp**d**).

The postfix SMTP client does not use authdaemon - it uses its own internal database for passwords to authenticate with remote sites... as mentioned in the error message I called out from saslfinger -c.

Client here means "postfix program that acts like an MUA, which makes contact with a remote SMTP server to send mail".

Server here means "postfix programs that *receives* mail from remote hosts.

Forget sasldb2 - that's a red herring.

---

### Post by Palcrypt on 2008-02-29
oh, sorry. i didn't realize when you mentioned that it was meant for me. I see the issue you mean now. How do i tell the client to map to my users?

---

### Post by Mr. C. on 2008-02-29
```
man -P 'less +/smtp_sasl_password_maps' 5 postconf
```

---

### Post by Palcrypt on 2008-02-29
ok, so i need to insert a smtp_sasl_password_maps into my main.cf. What do I assign to the path? I just know it needs to be able to read the passwords for the emails in my virtual hosts. Oh, and by the way. Thanks for you help. I'm at least getting a better understanding of this little by little.

---

### Post by Mr. C. on 2008-02-29
Put it in /etc/postfix, and give it the filename you want.  As the docs say, the file is read *before* a chroot, so you'll not be affected.

This confuses me: "I just know it needs to be able to read the passwords for the emails in my virtual hosts."

Hmmm... there are no "virtual hosts" for the SMTP client.  Virtual domains tell postfix which email addresses to consider *accepting* for email, not for sending. Recall, *receiving* mail == SMTP server == smtpd.

---

### Post by Palcrypt on 2008-02-29
ok. did that. Still can't send any mail from thunderbird. I can recieve just fine though (which has always been the case).

---

### Post by Mr. C. on 2008-02-29
You're doing to many things at once.  You need to work out one thing at a time.  We've been working on the postfix smtp client authentication.  Does that work?

---

### Post by Palcrypt on 2008-03-01
well. i get this error when i run saslfinger -c
```

You have set smtp_sasl_password_maps = /etc/postfix/sasl_passwd
in main.cf, but /etc/postfix/sasl_passwd does not seem to be there.
Please check and run saslfinger again.

```

---

### Post by Palcrypt on 2008-03-01
ok, read a bit more and added one account to the sasl_passwd db. now my saslfinger-c reads like this:
```

saslfinger - postfix Cyrus sasl configuration Sat Mar  1 00:15:53 EST 2008
version: 1.0.2
mode: client-side SMTP AUTH

-- basics --
Postfix: 2.4.7
System: Ubuntu 7.10 \n \l

-- smtp is linked to --
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0xb7d5d000)

-- active SMTP AUTH and TLS parameters for smtp --
smtp_sasl_password_maps = /etc/postfix/sasl_passwd
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache


-- listing of /usr/lib/sasl2 --
total 840
drwxr-xr-x   2 root root  4096 2008-02-28 13:22 .
drwxr-xr-x 165 root root 53248 2008-02-28 12:08 ..
-rw-r--r--   1 root root 13640 2007-10-02 09:58 libanonymous.a
-rw-r--r--   1 root root   862 2007-10-02 09:58 libanonymous.la
-rw-r--r--   1 root root 13208 2007-10-02 09:58 libanonymous.so
-rw-r--r--   1 root root 13208 2007-10-02 09:58 libanonymous.so.2
-rw-r--r--   1 root root 13208 2007-10-02 09:58 libanonymous.so.2.0.22
-rw-r--r--   1 root root 15974 2007-10-02 09:58 libcrammd5.a
-rw-r--r--   1 root root   848 2007-10-02 09:58 libcrammd5.la
-rw-r--r--   1 root root 15672 2007-10-02 09:58 libcrammd5.so
-rw-r--r--   1 root root 15672 2007-10-02 09:58 libcrammd5.so.2
-rw-r--r--   1 root root 15672 2007-10-02 09:58 libcrammd5.so.2.0.22
-rw-r--r--   1 root root 47348 2007-10-02 09:58 libdigestmd5.a
-rw-r--r--   1 root root   871 2007-10-02 09:58 libdigestmd5.la
-rw-r--r--   1 root root 43916 2007-10-02 09:58 libdigestmd5.so
-rw-r--r--   1 root root 43916 2007-10-02 09:58 libdigestmd5.so.2
-rw-r--r--   1 root root 43916 2007-10-02 09:58 libdigestmd5.so.2.0.22
-rw-r--r--   1 root root 13650 2007-10-02 09:58 liblogin.a
-rw-r--r--   1 root root   842 2007-10-02 09:58 liblogin.la
-rw-r--r--   1 root root 14036 2007-10-02 09:58 liblogin.so
-rw-r--r--   1 root root 14036 2007-10-02 09:58 liblogin.so.2
-rw-r--r--   1 root root 14036 2007-10-02 09:58 liblogin.so.2.0.22
-rw-r--r--   1 root root 30516 2007-10-02 09:58 libntlm.a
-rw-r--r--   1 root root   836 2007-10-02 09:58 libntlm.la
-rw-r--r--   1 root root 29876 2007-10-02 09:58 libntlm.so
-rw-r--r--   1 root root 29876 2007-10-02 09:58 libntlm.so.2
-rw-r--r--   1 root root 29876 2007-10-02 09:58 libntlm.so.2.0.22
-rw-r--r--   1 root root 13938 2007-10-02 09:58 libplain.a
-rw-r--r--   1 root root   842 2007-10-02 09:58 libplain.la
-rw-r--r--   1 root root 14036 2007-10-02 09:58 libplain.so
-rw-r--r--   1 root root 14036 2007-10-02 09:58 libplain.so.2
-rw-r--r--   1 root root 14036 2007-10-02 09:58 libplain.so.2.0.22
-rw-r--r--   1 root root 22150 2007-10-02 09:58 libsasldb.a
-rw-r--r--   1 root root   863 2007-10-02 09:58 libsasldb.la
-rw-r--r--   1 root root 18356 2007-10-02 09:58 libsasldb.so
-rw-r--r--   1 root root 18356 2007-10-02 09:58 libsasldb.so.2
-rw-r--r--   1 root root 18356 2007-10-02 09:58 libsasldb.so.2.0.22
-rw-r--r--   1 root root 23812 2007-10-02 09:58 libsql.a
-rw-r--r--   1 root root   971 2007-10-02 09:58 libsql.la
-rw-r--r--   1 root root 23352 2007-10-02 09:58 libsql.so
-rw-r--r--   1 root root 23352 2007-10-02 09:58 libsql.so.2
-rw-r--r--   1 root root 23352 2007-10-02 09:58 libsql.so.2.0.22
-rw-r--r--   1 root root    49 2008-02-29 00:23 smtpd.conf


-- permissions for /etc/postfix/sasl_passwd --
-rw------- 1 root root 26 2008-03-01 00:14 /etc/postfix/sasl_passwd

-- permissions for /etc/postfix/sasl_passwd.db --
-rw------- 1 root root 12288 2008-03-01 00:15 /etc/postfix/sasl_passwd.db

/etc/postfix/sasl_passwd.db is up to date.

-- active services in /etc/postfix/master.cf --
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
smtp      inet  n       -       -       -       -       smtpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      unix  -       -       -       -       -       smtp
relay     unix  -       -       -       -       -       smtp
        -o smtp_fallback_relay=
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

-- mechanisms on localhost --
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN



-- end of saslfinger output --

```

---

### Post by Palcrypt on 2008-03-01
now mail sent to my server gets returned. It returns this error:
Host or domain name not found. Name service error
    for name=localdomain type=A: Host not found

---

### Post by Palcrypt on 2008-03-01
ok fixed that. it was something i did a while ago and didn't know about. so, starting over because i think there's confusion.

Let me make sure I understand this, and you can tell me if I'm wrong.
Postfix's SMTP Client is what is responsible for sending mail to other locations. In other words, when I send a bit of mail from Outlook or Thunderbird I'm actually using Postfix's SMTP Client.

Postfix's SMTP Server is what is responsible for delivering mail to the various users on my server. So, when Joe Blow sends an email to one of the domains associated with my server the SMTP Server is what receives it and puts it in the proper box.

So. If I have that all correct, then SASL authentication for the Client is what I need to be able to work out in order to be able to send mail from a program like Thunderbird.

So, have I got a grasp on this now?

---

### Post by drhiii on 2008-03-01
This is the first time I've experienced this kind of behavior in Ubuntu forums.  I would appreciate the help, but not the sarcasm.  I will go elsewhere for help.  Your tone is at the least, off-putting...



> **Mr. C. said:**
> No, this would be part of a response.  You've cropped and removed important information from the log line.  It is best to show the entire lines, rather than you interpreting for us what you think is best to show.

This is your smtp CLIENT try to send email via hotmail servers.  They do not allow you to relay, because you are not authenticated.

At the bottom of your saslfinger -c output, the message:



appears.  Did you think this not important?

There is a SASL client and server - are you aware of the differences, and what is required of each?

---

### Post by Mr. C. on 2008-03-01
Show the exact and entire error message or log line  if you want help - it is too difficult if you interpret for me.

You may also take a moment to reflect on my post #9.

---

### Post by Mr. C. on 2008-03-01
> **drhiii said:**
> This is the first time I've experienced this kind of behavior in Ubuntu forums.  I would appreciate the help, but not the sarcasm.  I will go elsewhere for help.  Your tone is at the least, off-putting...

My price for spending a significant amount of my time helping someone, asking questions to gain insight into the user's system, is for the person I'm assisting to pay attention and respond to the information requested.  There has been too much back and forth here, because much has been ignored.

---

### Post by Palcrypt on 2008-03-01
> **Mr. C. said:**
> Show the exact and entire error message or log line  if you want help - it is too difficult if you interpret for me.

You may also take a moment to reflect on my post #9.

Ok. Here's what I get out of my mail log:

```

ar  1 01:38:27 lonewolf dovecot: imap-login: Login: user=<paul.paulromerproductions>, method=PLAIN, rip=97.81.109.22, lip=216.24.175.76
Mar  1 01:38:29 lonewolf postfix/smtpd[9763]: connect from 97-81-109-22.dhcp.athn.ga.charter.com[97.81.109.22]
Mar  1 01:38:35 lonewolf postfix/smtpd[9763]: warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory
Mar  1 01:38:35 lonewolf postfix/smtpd[9763]: warning: SASL authentication failure: Password verification failed
Mar  1 01:38:35 lonewolf postfix/smtpd[9763]: warning: 97-81-109-22.dhcp.athn.ga.charter.com[97.81.109.22]: SASL PLAIN authentication failed: generic failure
Mar  1 01:38:35 lonewolf postfix/smtpd[9763]: warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory
Mar  1 01:38:35 lonewolf postfix/smtpd[9763]: warning: 97-81-109-22.dhcp.athn.ga.charter.com[97.81.109.22]: SASL LOGIN authentication failed: generic failure
```

---

### Post by drhiii on 2008-03-01
As mentioned, your tone is not becoming Ubuntu standards.  First I get chided for double posting.  Then I receive a sarcasm laced post.  Now a second slightly less sarcastic post admonishing me for not posting enough information.  The contempt you hold for us idiot users is glaring.  You also appear to be mixing users based on your responses.  As mentioned, will seek help elsewhere where the spirit to aid those who ask is met with in-kind willingness because neither your help or my presence in this thread is wanted.  I ask that if I reappear in some other forum with questions, please stay away.  I am not interested in your help if this is how it is tendered.  No further response wanted or needed because it would just be wasting bandwidth..  


> **Mr. C. said:**
> My price for spending a significant amount of my time helping someone, asking questions to gain insight into the user's system, is for the person I'm assisting to pay attention and respond to the information requested.  There has been too much back and forth here, because much has been ignored.

---

### Post by Mr. C. on 2008-03-01
Apologies for the noise Palcrypt.  After re-reading this thread, I see that the other user hijacked your issue and I hadn't noticed the change in user; the same user was asking help elsewhere, and there was cross post confusion.  When answering a number of questions that are very similar, I don't always notice when a thread is overtaken.

---

### Post by Mr. C. on 2008-03-01
> **Palcrypt said:**
> ok fixed that. it was something i did a while ago and didn't know about. so, starting over because i think there's confusion.
Right-O!

> **Palcrypt said:**
> 
Let me make sure I understand this, and you can tell me if I'm wrong.
Postfix's SMTP Client is what is responsible for sending mail to other locations. In other words, when I send a bit of mail from Outlook or Thunderbird I'm actually using Postfix's SMTP Client.

Only half credit here; the first part.  The client sends to other systems - yes.  But, your MUA (Mail User Agent) connects to the SMTP SERVER.  The server listens for incoming connections.  The confusion people have here is thinking in terms of WAN->LAN and LAN->WAN.  Remember, postfix accepts email from ANY valid SMTP client, and an MUA acts like a client.  So your MUA connects to the postfix smtpd server.  The smtpd server is responsible for accepting email connections into the postfix system, regardless of from whence they came (MUA, another SMTP server, an LMTP server, etc.)

> **Palcrypt said:**
> 
Postfix's SMTP Server is what is responsible for delivering mail to the various users on my server. So, when Joe Blow sends an email to one of the domains associated with my server the SMTP Server is what receives it and puts it in the proper box.


This is the right concept, but not quite correct in terms of postfix organization and architecture.  The smtpd server accepts mail connections, and if they pass, hands off to qmgr, which manages the queue of messages for disposition, and then qmgr tries to call upon a relay or delivery agent (MDA !) to *deliver* the mail to you user's mailbox.

This is not just a pedantic distinction - it is **critical** to understanding the log messages and the flow of email.

Yes, when Joe Blow sends an email, his mail server's make a connection to your SMTP server (smtpd).  You can see this in the logs; watch a log while you connect from another terminal.  Type this in one terminal and double click the last log line so you can see it move:

```
tail -f /var/log/mail.log
```

Then, in another window, type these commands (replacing yourdomain.com as appropriate), and as you do so, watch the log lines in the other window.  You'll see the transaction that occurs as you enter commands:

```
telnet localhost 25
EHLO yourdomain.com
MAIL FROM:<user@yourdomain.com>
RCPT TO:<user@yourdomain.com>
DATA
Subject: Hello

that's it.
.
quit

```

You should be able to see now what postfix agent is being called.  You can do the same with Thunderbird - watching the logs while you try to connect.  And then finally, do the same with postfix attempt to send out mail from your system.

> **Palcrypt said:**
> 
So. If I have that all correct, then SASL authentication for the Client is what I need to be able to work out in order to be able to send mail from a program like Thunderbird.

So, have I got a grasp on this now?

Almost, again, the same confusion as above.  Again, Thunderbird is an MUA (mail user agent).  It is sends mail using its internal SMTP engine (its just a language/protocol) and connects to your postfix server.  As you're keenly aware now, it is smtpd (the postfix server) that is listening patiently for connections from any SMTP engine (your MUA, another MTA).

So, the SASL that you have to work out with Thunderbird is the server side (postfix's smtpd) and the SASL you have to work out for having postfix send mail to another MTA (via smtp) are different.  The former uses SASL (via saslauthd or whatever you've configured) and the later uses the built-into postfix/smtp client SASL authentication code.  Take focus on the parameters in main.cf and man 5 postconf - the difference between those that start with smtp_ and smtp**d**_

Got Postfix?

---

### Post by Palcrypt on 2008-03-01
ok. i understand now. thanks for all that. my issue now seems to be that the system can't authenticate via saslauthd because the directory it's trying to read the mux files from is empty. Thus getting this error:

```

Mar  1 09:33:17 lonewolf postfix/smtpd[13232]: connect from 97-81-109-22.dhcp.athn.ga.charter.com[97.81.109.22]
Mar  1 09:33:22 lonewolf postfix/smtpd[13232]: warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory
Mar  1 09:33:22 lonewolf postfix/smtpd[13232]: warning: SASL authentication failure: Password verification failed
Mar  1 09:33:22 lonewolf postfix/smtpd[13232]: warning: 97-81-109-22.dhcp.athn.ga.charter.com[97.81.109.22]: SASL PLAIN authentication failed: generic failure
Mar  1 09:33:22 lonewolf postfix/smtpd[13232]: warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory
Mar  1 09:33:22 lonewolf postfix/smtpd[13232]: warning: 97-81-109-22.dhcp.athn.ga.charter.com[97.81.109.22]: SASL LOGIN authentication failed: generic failure
```

my /etc/default/saslauthd looks like this:

```

#
# Settings for saslauthd daemon
#

# Should saslauthd run automatically on startup? (default: no)
START=yes
PWDIR="/var/spool/postfix/var/run/saslauthd"
PARAMS="-m ${PWDIR}"
PIDFILE="${PWDIR}/saslauthd.pid"

# Which authentication mechanisms should saslauthd use? (default: pam)
#
# Available options in this Debian package:
# getpwent  -- use the getpwent() library function
# kerberos5 -- use Kerberos 5
# pam       -- use PAM
# rimap     -- use a remote IMAP server
# shadow    -- use the local shadow password file
# sasldb    -- use the local sasldb database file
# ldap      -- use LDAP (configuration is in /etc/saslauthd.conf)
#
# Only one option may be used at a time. See the saslauthd man page
# for more information.
#
# Example: MECHANISMS="pam"
MECHANISMS="pam"

# Additional options for this mechanism. (default: none)
# See the saslauthd man page for information about mech-specific options.
MECH_OPTIONS=""

# How many saslauthd processes should we run? (default: 5)
# A value of 0 will fork a new process for each connection.
THREADS=5

# Other options (default: -c)
# See the saslauthd man page for information about these options.
#
# Example for postfix users: "-c -m /var/spool/postfix/var/run/saslauthd"
# Note: See /usr/share/doc/sasl2-bin/README.Debian
OPTIONS="-c"
```

i have also made sure the whole path referenced in PWDIR is owned by root and group sasl with postfix being a part of sasl, with 755 permissions.

---

### Post by Palcrypt on 2008-03-01
Ok. it all works now. I found out the reason the mux files weren't being created is because I was missing something in my /etc/default/saslauthd

the last line of it read:
OPTIONS="-c"

for this install, in order for saslauthd to create all the files in the write location it needed the last line to read as such:
OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd"

So. Thanks again for all your help. I have a better understanding of how the mail server works, and I feel more comfortable debugging my own problems from now on.

---

### Post by Mr. C. on 2008-03-01
Excellent!

---

