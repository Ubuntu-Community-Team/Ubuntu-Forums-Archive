---
title: "virtual mailbox user problem"
date: 2008-11-20
forum: Server Platforms
---

### Post by Feisei on 2008-11-20
I'm running postfix and courier-imap with virtual mailboxes. For some reason my mail program won't display the mail folders for a virtual user (let's say his name is Jack).

I can send an email to Jack from another (non virtual) account just fine. When I check the actual file system I see the newly arrived email sitting there in the mail folder. So the postfix part of the mail system is working fine.

I checked my mail logs and it shows that the virtual user was authenticated succesfully by the courier authentication daemon. Seems all good to me.

But for some reason I just cannot see the email in my mail program. When I ask it (Thunderbird) to search for imap folders it just gives me an empty result.

Any idea what could be wrong?

Here are some of my config files:

```
/etc/courier/authdaemonrc

authmodulelist="authuserdb authpam"
authmodulelistorig="authuserdb authpam authpgsql authldap authmysql authcustom authpipe"
daemons=5
authdaemonvar=/var/run/courier/authdaemon
DEBUG_LOGIN=1
DEFAULTOPTIONS=""
LOGGEROPTS=""

```

```

/etc/postfix/main.cf

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
readme_directory = no
myhostname = server.local
mydestination = localhost
mynetworks = 127.0.0.0/8, 192.168.1.0/24
virtual_mailbox_domains = example.com
virtual_mailbox_base = /var/mail/vhosts
virtual_mailbox_maps = hash:/etc/postfix/vmailbox
virtual_minimum_uid = 100
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_alias_maps = hash:/etc/postfix/virtual

smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtp_tls_key_file = /etc/ssl/private/smtpd.key
smtp_tls_CAfile = /etc/ssl/certs/cacert.pem
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_tls_note_starttls_offer = yes
tls_random_source = dev:/dev/urandom

smtpd_sasl_local_domain = $myhostname
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_tls_security_options = noanonymous
```

```

/etc/postfix/vmailbox

jack@example.com        example/jack/
```

```
mail.log

Nov 20 17:19:11 webserver imapd-ssl: Connection, ip=[::ffff:192.168.1.21]
Nov 20 17:19:11 webserver authdaemond: received auth request, service=imap, authtype=login
Nov 20 17:19:11 webserver authdaemond: authuserdb: trying this module
Nov 20 17:19:11 webserver authdaemond: userdb: opened /etc/courier/userdb.dat
Nov 20 17:19:11 webserver authdaemond: userdb: looking up 'jack'
Nov 20 17:19:11 webserver authdaemond: userdb: home=/var/mail/vhosts/example/jack, uid=0, gid=0, shell=<unset>, mail=/var/mail/vhosts/example/jack, quota=<unset>, gecos=<unset>, options=<unset>
Nov 20 17:19:11 webserver authdaemond: found systempw in userdbshadow
Nov 20 17:19:11 webserver authdaemond: authuserdb: sysusername=<null>, sysuserid=0, sysgroupid=0, homedir=/var/mail/vhosts/example/jack, address=jack, fullname=<null>, maildir=/var/mail/vhosts/example/jack, quota=<null>, options=<null>
Nov 20 17:19:11 webserver authdaemond: password matches successfully
Nov 20 17:19:11 webserver authdaemond: Authenticated: sysusername=<null>, sysuserid=0, sysgroupid=0, homedir=/var/mail/vhosts/example/jack, address=jack, fullname=<null>, maildir=/var/mail/vhosts/example/jack, quota=<null>, options=<null>

```

---

### Post by MJN on 2008-11-20
Have you told Courier where to find mail for virtual users? I don't use it so cannot help with the specifics, but given you have confirmed the mail exists in the filesystem the next logical step is to ensure Courier knows where to find it.
 
Mathew

---

### Post by Feisei on 2008-11-20
The following code is the result of "sudo userd -show jack"

```
uid=vmail
systempw=---some_encoded_password---
mail=/var/mail/vhosts/example/jack
home=/var/mail/vhosts/example/jack
gid=vmail
```

This makes me believe that Courier should be able to find the mail.

The directory in question is owned by the user "vmail". Here's the result of an "sudo ls -ltr /var/mail/vhosts/example/jack"

```
drwx--S--- 2 vmail vmail 4096 2008-11-20 16:59 tmp
drwx--S--- 2 vmail vmail 4096 2008-11-20 16:59 new
drwx--S--- 2 vmail vmail 4096 2008-11-20 16:59 cur

```

and "sudo ls -ltr /var/mail/vhosts/example/jack/new"

```
-rw------- 1 vmail vmail 862 2008-11-20 16:59 1227167971.V805I14c1b8M367300.example.com

```

---

