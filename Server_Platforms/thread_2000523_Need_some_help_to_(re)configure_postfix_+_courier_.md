---
title: "Need some help to (re)configure postfix + courier (SSL)"
date: 2012-06-09
forum: Server Platforms
---

### Post by clement.analogue on 2012-06-09
Hello,

I've got some problem with postfix + courier.

**What's going ?**

I try to add an account with thunderbird or evolution. The mail server (MTA and MDA) is mail.forumanalogue.fr. Thunderbird try to find the right parameters and fail. I setup manually the parameters and retry, but it still don't work. IMAP and SMTP using STARTTLS ok in the local network, but without SSL. Although it's ok, the authentication fail. It doesn't work if I try to add a new account from internet.

I'd like postfix as courier works both with SSL. It worked with courier-imap-ssl for a while. But it doesn't work since I did something, where something could be the upgrade from 10.04 to 12.04, add of certifications STARTSSL, disable IPv6 in /etc/hosts, remove gamin and install fam instead, etc.

The following are quit the same from local network or internet, just the IP changes.

**Postfix logs:**

_Authentication with STARTTLS:_

```
Jun  7 16:21:42 clement-desktop imapd: Connection, ip=[::ffff:192.168.1.3]
Jun  7 16:21:43 clement-desktop imapd: Connection, ip=[::ffff:192.168.1.3]
Jun  7 16:21:43 clement-desktop imapd: couriertls: read: error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca
Jun  7 16:21:43 clement-desktop imapd: Disconnected, ip=[::ffff:192.168.1.3], time=1, starttls=1
Jun  7 16:21:43 clement-desktop imapd: couriertls: read: error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca
Jun  7 16:21:43 clement-desktop imapd: Disconnected, ip=[::ffff:192.168.1.3], time=0, starttls=1
```_IMAP SSL:_

The following message repeats itself:

```
Jun  7 16:25:29 clement-desktop imapd-ssl: Connection, ip=[::ffff:192.168.1.3]
Jun  7 16:25:29 clement-desktop postfix/smtpd[19515]: connect from unknown[192.168.1.3]
Jun  7 16:25:29 clement-desktop imapd-ssl: couriertls: read: error:14094416:SSL routines:SSL3_READ_BYTES:sslv3 alert certificate unknown
Jun  7 16:25:29 clement-desktop imapd-ssl: Disconnected, ip=[::ffff:192.168.1.3], time=0, starttls=1
Jun  7 16:25:29 clement-desktop postfix/smtpd[19515]: disconnect from unknown[192.168.1.3]
Jun  7 16:25:29 clement-desktop postfix/smtpd[19515]: connect from unknown[192.168.1.3]
Jun  7 16:25:29 clement-desktop postfix/smtpd[19515]: lost connection after CONNECT from unknown[192.168.1.3]
Jun  7 16:25:29 clement-desktop postfix/smtpd[19515]: disconnect from unknown[192.168.1.3]
```[U]

SMTP SSL:[/U]

```
Jun  7 16:28:59 clement-desktop imapd: Connection, ip=[::ffff:192.168.1.3]
Jun  7 16:28:59 clement-desktop imapd: Disconnected, ip=[::ffff:192.168.1.3], time=0
```**Configuration**:

```
$ postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command =
mailbox_size_limit = 0
mailman_destination_recipient_limit = 1
message_size_limit = 0
mydestination = mail.forumanalogue.fr, localhost.localdomain, localhost, forumanalogue.fr
myhostname = mail.forumanalogue.fr
mynetworks = 127.0.0.0/8, 192.168.1.0/24
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relay_domains = mail.forumanalogue.fr
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =
smtp_tls_CAfile = $smtpd_tls_CAfile
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/postfix/ssl/ca-bundle.crt
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/ssl.crt
smtpd_tls_key_file = /etc/postfix/ssl/ssl.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
transport_maps = hash:/etc/postfix/transport
```_postfinger:_

```
postfinger - postfix configuration on Thu Jun  7 16:33:31 CEST 2012
version: 1.30

Warning: postfinger output may show private configuration information,
such as ip addresses and/or domain names which you do not want to show
to the public.  If this is the case it is your responsibility to modify
the output to hide this private information.  [Remove this warning with
the --nowarn option.]

--System Parameters--
mail_version = 2.9.1
hostname = clement-desktop
uname = Linux clement-desktop 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

--Packaging information--
looks like this postfix comes from deb package: postfix-2.9.1-5

--main.cf non-default parameters--
alias_maps = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
home_mailbox = Maildir/
mailbox_size_limit = 0
mailman_destination_recipient_limit = 1
message_size_limit = 0
mydestination = mail.forumanalogue.fr, localhost.localdomain, localhost, forumanalogue.fr
myhostname = mail.forumanalogue.fr
mynetworks = 127.0.0.0/8, 192.168.1.0/24
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relay_domains = mail.forumanalogue.fr
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_tls_CAfile = /etc/postfix/ssl/ca-bundle.crt
smtpd_tls_cert_file = /etc/postfix/ssl/ssl.crt
smtpd_tls_key_file = /etc/postfix/ssl/ssl.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =
smtp_tls_CAfile = $smtpd_tls_CAfile
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
transport_maps = hash:/etc/postfix/transport

--master.cf--
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
proxywrite unix -       -       n       -       1       proxymap
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
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

-- end of postfinger output --
```_SASL:_

```
$ saslfinger -s
saslfinger - postfix Cyrus sasl configuration jeudi 7 juin 2012, 16:37:04 (UTC+0200)
version: 1.0.4
mode: server-side SMTP AUTH

-- basics --
Postfix: 2.9.1
System: Ubuntu 12.04 LTS \n \l

-- smtpd is linked to --
    libsasl2.so.2 => /usr/lib/x86_64-linux-gnu/libsasl2.so.2 (0x00007f9476462000)

-- active SMTP AUTH and TLS parameters for smtpd --
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/postfix/ssl/ca-bundle.crt
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/ssl.crt
smtpd_tls_key_file = /etc/postfix/ssl/ssl.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes


-- listing of /usr/lib/sasl2 --
total 140
drwxr-xr-x   2 root root   4096 mai   17 10:58 .
drwxr-xr-x 284 root root 126976 juin   7 13:05 ..
-rw-r--r--   1 root root      1 avril 29 22:22 berkeley_db.active
-rw-r--r--   1 root root      1 mai    4 06:15 berkeley_db.txt

-- listing of /etc/postfix/sasl --
total 12
drwxr-xr-x 2 root root 4096 mai    5  2010 .
drwxr-xr-x 4 root root 4096 juin   7 13:53 ..
-rw-r--r-- 1 root root   49 mai    5  2010 smtpd.conf




-- content of /etc/postfix/sasl/smtpd.conf --
pwcheck_method: saslauthd
mech_list: plain login

-- content of /etc/postfix/sasl/smtpd.conf --
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
proxywrite unix -       -       n       -       1       proxymap
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
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

-- mechanisms on localhost --
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN


-- end of saslfinger output --
``````
$ sudo saslfinger -c
saslfinger - postfix Cyrus sasl configuration jeudi 7 juin 2012, 16:38:53 (UTC+0200)
version: 1.0.4
mode: client-side SMTP AUTH

-- basics --
Postfix: 2.9.1
System: Ubuntu 12.04 LTS \n \l

-- smtp is linked to --
    libsasl2.so.2 => /usr/lib/x86_64-linux-gnu/libsasl2.so.2 (0x00007feb1fd48000)

-- active SMTP AUTH and TLS parameters for smtp --
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =
smtp_tls_CAfile = $smtpd_tls_CAfile
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes


-- listing of /usr/lib/sasl2 --
total 140
drwxr-xr-x   2 root root   4096 mai   17 10:58 .
drwxr-xr-x 284 root root 126976 juin   7 13:05 ..
-rw-r--r--   1 root root      1 avril 29 22:22 berkeley_db.active
-rw-r--r--   1 root root      1 mai    4 06:15 berkeley_db.txt

-- listing of /etc/postfix/sasl --
total 12
drwxr-xr-x 2 root root 4096 mai    5  2010 .
drwxr-xr-x 4 root root 4096 juin   7 13:53 ..
-rw-r--r-- 1 root root   49 mai    5  2010 smtpd.conf


-- permissions for /etc/postfix/sasl_passwd --
-rw------- 1 root root 126 mai   13  2010 /etc/postfix/sasl_passwd

-- permissions for /etc/postfix/sasl_passwd.db --
-rw------- 1 root root 12288 mai   13  2010 /etc/postfix/sasl_passwd.db

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
proxywrite unix -       -       n       -       1       proxymap
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
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

-- mechanisms on [193.252.22.72]:submission --

-- mechanisms on [mail.fabien-loison.fr]:submission --


-- end of saslfinger output --
```Any help is welcome ^^ thanks.

---

### Post by nowashburn on 2012-07-20
did you ever figure this out? i am getting the same error. i setup everything based off of this tutorial:

[http://www.pixelinx.com/2010/10/creating-a-mail-server-on-ubuntu-using-postfix-courier-ssltls-spamassassin-clamav-and-amavis/#comment-1794](http://www.pixelinx.com/2010/10/creating-a-mail-server-on-ubuntu-using-postfix-courier-ssltls-spamassassin-clamav-and-amavis/#comment-1794)

---

### Post by clement.analogue on 2012-10-11
Hi,
I didn't have time to take care of it until now.
Unfortunately, I still don't figure out what's wrong with postfix + SSL/TLS. It's a problem because in France the port 25 is blocked by most of ISPs.

For IMAP issues, I just fix that for both imap + starttls and imaps. It was a problem of certificat. It is really tricky :
[https://forum.startcom.org/viewtopic.php?f=15&t=1398](https://forum.startcom.org/viewtopic.php?f=15&t=1398)
So if you have signed certificate, you should take a look to the link above.

I don't use virtual mailbox like it's done in the tutorial you give.

The last issue is anyone can send mail from my server. I want people have to authenticate to use my mail server. How to do that ?

---

