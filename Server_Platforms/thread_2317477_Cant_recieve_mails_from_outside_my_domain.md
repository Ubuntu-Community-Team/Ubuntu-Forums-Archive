---
title: "Cant recieve mails from outside my domain"
date: 2016-03-16
forum: Server Platforms
---

### Post by lukas34 on 2016-03-16
Hi
Suddenly I can't receive mails from outside my domain anymore.
Mails from accounts within the server are sent and recieved normally.
Mail accounts on the server can recieve mails from mails outside.

```
$TTL 86400
@   IN SOA ns1.first-ns.de. postmaster.robot.first-ns.de. (
    2016031606   ; serial
    14400        ; refresh
    1800         ; retry
    604800       ; expire
    86400 )      ; minimum
 
@                        IN NS      robotns3.second-ns.com.
@                        IN NS      robotns2.second-ns.de.
@                        IN NS      ns1.first-ns.de.
 
@                        IN A       136.243.54.13
localhost                IN A       127.0.0.1
webmail                  IN A       136.243.54.13
www                      IN A       136.243.54.13
ftp                      IN CNAME   www
imap                     IN CNAME   webmail
loopback                 IN CNAME   localhost
pop                      IN CNAME   webmail
relay                    IN CNAME   webmail
smtp                     IN CNAME   webmail
@                        IN MX 10   webmail
```
postfix main.cf
```

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

append_dot_mydomain = no

readme_directory = no

mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mydestination = webmail.marketstrategy.de
mailbox_size_limit = 0
message_size_limit = 51200000
recipient_delimiter = 51200000
inet_interfaces = all
myorigin = hetzner.marketstrategy.de
inet_protocols = all


##### TLS parameters ######

#smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

smtpd_tls_cert_file=/var/www/webmail/custom_luggie/ssl/webmail.crt
smtpd_tls_key_file=/var/www/webmail/custom_luggie/ssl/webmail.key

smtpd_use_tls=yes

#smtpd_tls_security_level = may
#smtp_tls_security_level = may
smtpd_tls_mandatory_protocols = !SSLv2, !SSLv3
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

###### SASL Auth ######
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes

###### Use Dovecot LMTP Service to deliver Mails to Dovecot ######
virtual_transport = lmtp:unix:private/dovecot-lmtp

##### Only allow mail transport if client is authenticated or in own network (PHP Scripts, ...) ######
#smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, reject_rbl_client
#smtpd_relay_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination

###### MySQL Connection ######
virtual_alias_maps = mysql:/etc/postfix/virtual/mysql-aliases.cf
virtual_mailbox_maps = mysql:/etc/postfix/virtual/mysql-maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/virtual/mysql-domains.cf
local_recipient_maps = $virtual_mailbox_maps
myhostname = webmail.marketstrategy.de

#########
#smtpd_sender_login_maps = mysql:/etc/postfix/virtual/sender-login-maps.cf
#smtpd_sender_restrictions = permit_mynetworks, reject_non_fqdn_sender, reject_sender_login_mismatch, permit_sasl_authenticated

```
postfix master.cf
```

#bash: c: command not found
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master" or
 # on-line: [http://www.postfix.org/master.5.html](http://www.postfix.org/master.5.html)).
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
#smtp      inet  n       -       -       -       -       smtpd
#smtp      inet  n       -       -       -       1       postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy

submission inet n       -       -       -       -       smtpd -v
  -o syslog_name=postfix/submission
  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_type=dovecot
  -o smtpd_sasl_path=private/auth
  -o smtpd_sasl_security_options=noanonymous
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject

#smtps     inet  n       -       -       -       -       smtpd
#  -o syslog_name=postfix/smtps
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=
#  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    unix  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      unix  n       -       n       300     1       qmgr
#qmgr     unix  n       -       n       300     1       oqmgr
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
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# ====================================================================
#
# Recent Cyrus versions can use the existing "lmtp" master.cf entry.
#
# Specify in cyrus.conf:
#   lmtp    cmd="lmtpd -a" listen="localhost:lmtp" proto=tcp4
#
# Specify in main.cf one or more of the following:
#  mailbox_transport = lmtp:inet:localhost
#  virtual_transport = lmtp:inet:localhost
#
# ====================================================================
#
# Cyrus 2.1.5 (Amos Gouaux)
# Also specify in main.cf: cyrus_destination_recipient_limit=1
#
#cyrus     unix  -       n       n       -       -       pipe
#  user=cyrus argv=/cyrus/bin/deliver -e -r ${sender} -m ${extension} ${user}
#
# ====================================================================
# Old example of delivery via Cyrus.
#
#old-cyrus unix  -       n       n       -       -       pipe
#  flags=R user=cyrus argv=/cyrus/bin/deliver -e -m ${extension} ${user}
#
# ====================================================================
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}


```

hostname -f : hetzner.marketstrategy.de

mxtoolbox / telnet  136.243.54.13 25 : failed to connect

periodicly mail.log creates hetzner.marketstrategy.de: ```
status=bounced (Host or domain name not found. Name service error for name=hetzner.marketstrategy.de type=AAAA: Host not found)
```

The Port 25 is not open for some reaspn.

I'm absolutly out of ideas. pls help :[

---

### Post by SeijiSensei on 2016-03-16
> mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128

The server is only listening on the localhost interface.  You need to use 0.0.0.0/0 to accept mail from all IP addresses, or if the machine is behind a router with portforwarding enabled, add the internal IP address of the router.

This is the default Ubuntu configuration for Postfix.  I can't tell you why it changed.

---

### Post by lukas34 on 2016-03-16
nah, this is not true. default is 127.0.0.1/8 this option doesn't indicate which network postfix is listening to.
It worked with this values set for some days without problems.

reinstalled postfix and dovecot. now it works again ...

---

