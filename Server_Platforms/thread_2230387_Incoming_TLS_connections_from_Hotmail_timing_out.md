---
title: "Incoming TLS connections from Hotmail timing out"
date: 2014-06-19
forum: Server Platforms
---

### Post by andrew_s2 on 2014-06-19
Running Ubuntu 12.04 LTS with postfix 2.9.6

This is a problem that began at the start of this month and despite everything I tried, I still can't hammer it out.

Basically what's happening is the server I'm maintaining is not completing an INCOMING TLS connection (Outgoing is fine). Now this only seems to happen with certain hotmail servers. My personal hotmail address seems to be unaffected for now as it only connects using non-TLS methods.

The error messages they receive on the other end is that the email has been delayed. Nothing else. It tries every 10 minutes for a few days before giving up.

Anyway, here's the entire transaction, including the (strange looking) TLS transaction. (Some data has been changed or masked)

```
Jun 12 18:19:27 [servername] postfix/smtpd[4839]: initializing the server-side TLS engine
Jun 12 18:19:27 [servername] postfix/smtpd[4839]: connect from snt004-omc1s40.hotmail.com[65.54.61.77]
Jun 12 18:19:28 [servername] postfix/smtpd[4839]: setting up TLS connection from snt004-omc1s40.hotmail.com[65.54.61.77]
Jun 12 18:19:28 [servername] postfix/smtpd[4839]: snt004-omc1s40.hotmail.com[65.54.61.77]: TLS cipher list "aNULL:-aNULL:ALL:+RC4:@STRENGTH"
Jun 12 18:19:28 [servername] postfix/smtpd[4839]: SSL_accept:before/accept initialization
Jun 12 18:19:28 [servername] postfix/smtpd[4839]: read from 7F04A4A693C0 [7F04A4A6F420] (11 bytes => -1 (0xFFFFFF4345FFFFFFF))
Jun 12 18:19:28 [servername] postfix/smtpd[4839]: read from 7F04A4A693C0 [7F04A4A6F420] (11 bytes => 11 (0xB))
Jun 12 18:19:28 [servername] postfix/smtpd[4839]: 0000 16 03 03 00 7c 01 00 00|78 03 03                 ....|... x..
Jun 12 18:19:28 [servername] postfix/smtpd[4839]: read from 7F04A4A693C0 [7F04A4A6F42E] (118 bytes => 47 (0x2F))
Jun 12 18:19:28 [servername] postfix/smtpd[4839]: 0000 53 99 62 99 99 58 5e fa|7e e3 bf 80 15 0e f8 ac  S.b..X^. ~.......
Jun 12 18:19:28 [servername] postfix/smtpd[4839]: xxx 2a 9a 32 e3 6d 71 5e 40|dc e1 e0 0b 70 4a 17 46  xxxq^@ ....pJ.F
Jun 12 18:19:28 [servername] postfix/smtpd[4839]: 0020 00 00 26 00 3c 00 3d 00|2f 00 35 00 05 00 0a     ..&.<.=. /.5....
Jun 12 18:19:28 [servername] postfix/smtpd[4839]: read from 7F04A4A693C0 [7F04A4A6F45D] (71 bytes => -1 (0xFFFFFFFFFFFFFFFF))
Jun 12 18:19:28 [servername] postfix/smtpd[4839]: read from 7F04eee3C0 [7F04A4A6F45D] (71 bytes => 37 (0x25))
Jun 12 18:19:28 [servername] postfix/smtpd[4839]: 0000 c0 2c ff 24 c0 27 c0 0a|c0 09 c0 14 c0 13 c0 2b  .,zzzzzz .......+
Jun 12 18:19:28 [servername] postfix/smtpd[4839]: 0010 c0 23 00 6a 00 40 00 13|00 04 01 00 00 29 ff 01  .#.j.@.. .....)..
Jun 12 18:19:28 [servername] postfix/smtpd[4839]: 0020 00 01 00 00 0a                                   .....
Jun 12 18:19:28 [servername] postfix/smtpd[4839]: read from 7F04A4A693C0 [7F04A4A6F482] (34 bytes => -1 (0xFFFFFFFFFFFFFFFF))

---Five minute interval---

Jun 12 18:24:28 [servername] postfix/smtpd[4839]: SSL_accept error from snt004-omc1s40.hotmail.com[65.54.61.77]: Connection timed out
Jun 12 18:24:28 [servername] postfix/smtpd[4839]: lost connection after STARTTLS from snt004-omc1s40.hotmail.com[65.54.61.77]
Jun 12 18:24:28 [servername] postfix/smtpd[4839]: disconnect from snt004-omc1s40.hotmail.com[65.54.61.77]
```

I've tried disabling certain cyphers, restricting protocols (smtpd_tls_protocols = !SSLv2, !TLSv1.1, !TLSv1.2) but no go.
I'm able to recieve the emails without any issues when TLS is set to none in main.cf

Here is my main.cf (A mess I know. The TLS log level is on 2 at the moment on purpose. The # lines are some of the things I've tried) Also, the certificates I'm using are StartSSL Class 1 (free) certificates. Before the problem occured, I was using the stock "snakeoil" stuff which came with Ubuntu:

main.cf
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version

# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 120s
smtpd_recipient_limit = 50
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes
readme_directory = no

# SASL
smtpd_sasl_auth_enable = yes
# If your potential clients use Outlook Express or other older clients
# this needs to be set to yes
broken_sasl_auth_clients = yes
smtpd_sasl_security_options = noanonymous

# TLS parameters
#smtp_use_tls = yes
#smtpd_use_tls = yes
smtp_tls_security_level = may
#smtpd_tls_security_level = may
smtpd_tls_security_level = none
smtpd_tls_ask_ccert = no
#smtpd_tls_auth_only = no
smtp_tls_loglevel = 0
smtpd_tls_loglevel = 2
smtpd_tls_received_header = no
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_helo_required = no
#smtpd_tls_ccert_verifydepth = 2

#smtpd_tls_mandatory_ciphers = low
#smtpd_tls_exclude_ciphers = kEDH+aRSA

#smtp_tls_protocols = !SSLv2, !TLSv1.1, !TLSv1.2
#smtp_tls_mandatory_protocols = !SSLv2, !TLSv1.1, !TLSv1.2
#smtpd_tls_protocols = !SSLv2, !TLSv1.1, !TLSv1.2
#smtpd_tls_mandatory_protocols = !SSLv2, !TLSv1.1, !TLSv1.2

smtpd_tls_cert_file=/etc/ssl/private/sslxxxx/mail.server.com.au.crt
smtpd_tls_key_file=/etc/ssl/private/sslxxxx/mail.server.com.au.key
# smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
# smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_tls_CApath = /etc/ssl/certs/
smtpd_tls_CAfile = /etc/ssl/certs/startssl-ca-bundle.pem
#smtpd_tls_CAfile = /etc/ssl/private/sslxxxx/sub.class1.server.ca.pem
smtp_tls_CAfile = $smtpd_tls_CAfile
smtp_tls_CApath = $smtpd_tls_CApath


# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
# Requirements for the sender details
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, permit
# Requirement for the recipient address
smtpd_recipient_restrictions = permit_sasl_authenticated, reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit
smtpd_data_restrictions = reject_unauth_pipelining

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.server.com.au
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
virtual_mailbox_base = /raid/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
myorigin = /etc/mailname
mydestination =
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 204857600000
recipient_delimiter = +
inet_interfaces = all
local_recipient_maps =
mynetworks_style = host
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
message_size_limit = 72914560
virtual_mailbox_limit = 204857600000

#recipient_bcc_maps = hash:/etc/postfix/recipient_bcc
#virtual_alias_maps = hash:/etc/postfix/vmaps
#autoresponder_destination_recipient_limit = 1
```

And master.cf

```
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#   -o receive_override_options=no_address_mappings
#   -o content_filter=autoresponder:dummy
#smtp      inet  n       -       -       -       1       postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
submission inet n       -       -       -       -       smtpd
#  -o syslog_name=postfix/submission
#  -o smtpd_tls_security_level=encrypt
   -o smtpd_sasl_auth_enable=yes
   -o smtpd_tls_auth_only=yes
   -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject
   -o smtpd_sasl_security_options=noanonymous,noplaintext
   -o smtpd_sasl_tls_security_options=noanonymous
#  -o milter_macro_daemon_name=ORIGINATING
smtps     inet  n       -       -       -       -       smtpd
#  -o syslog_name=postfix/smtps
   -o smtpd_tls_wrappermode=yes
   -o smtpd_sasl_auth_enable=yes
   -o smtpd_tls_auth_only=yes
   -o smtpd_client_restrictions=permit_sasl_authenticated,reject
   -o smtpd_sasl_security_options=noanonymous,noplaintext
   -o smtpd_sasl_tls_security_options=noanonymous
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       n       300     1       oqmgr
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
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop}
${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
#autoresponder unix - n n - - pipe
#  flags=Fq user=autoresponse argv=/usr/local/sbin/autoresponse -s ${sender} -r
${recipient} -S ${sasl_username} -C ${client_address}
```


If anyone can help out with this, I'd appreciate it greatly. Also, if you need any extra info, please let me know as I'm not quite sure what other pieces of info are needed for diagnosis.

Lastly, this happened around the same time an upgrade to the package "iproute" was applied. Don't know if it's related but it seems like a strange coincidence.

---

### Post by andrew_s2 on 2014-06-23
Solved.

looks like the hardware firewall was corrupting the TLS handshake.
Switched off port 25 scanning and all is good again.

---

### Post by andy119 on 2015-01-27
Same here re firewall corrupting TLS handshake. Went round in circles for nearly a month on this until we turned off SMTPS filtering on our Netgear UTM5. Immediate result, all works fine now.

> **andrew_s2 said:**
> Solved.

looks like the hardware firewall was corrupting the TLS handshake.
Switched off port 25 scanning and all is good again.

---

