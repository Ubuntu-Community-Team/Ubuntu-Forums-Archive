---
title: "postfix sasl auth failure"
date: 2009-08-10
forum: Server Platforms
---

### Post by mikeHU on 2009-08-10
Hi,


 I set up a mail server based on this tutorial [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) on a VPS with Ubuntu 8.04 LTS. The main components: postfix-mysql + courier-imap + sasl + tls. When I try to connect from a remote host to send mail i got the error below. I spent days searching for solutions but I did not succeeded. I hope somebody could help me, it would be really great!


 Thanks in advance,


Mike


 ----


 The problem:


 mail.info:
 09:24:47 s-name postfix/smtpd[30120]: connect from 82.***.219.***[82.***.219.***]
09:24:49 s-name postfix/smtpd[30120]: setting up TLS connection from 82.***.219.***[82.***.219.***]
09:24:50 s-name postfix/smtpd[30120]: Anonymous TLS connection established from 82.***.219.***[82.***.219.***]: TLSv1 with cipher DHE-RSA-AES256-SHA (256/256 bits)
09:24:58 s-name postfix/smtpd[30120]: warning: SASL authentication failure: client response doesn't match what we generated
09:24:58 s-name postfix/smtpd[30120]: warning: 82.***.219.***[82.***.219.***]: SASL DIGEST-MD5 authentication failed: authentication failure
09:25:00 s-name postfix/smtpd[30120]: warning: SASL authentication failure: client response doesn't match what we generated
09:25:00 s-name postfix/smtpd[30120]: warning: 82.***.219.***[82.***.219.***]: SASL DIGEST-MD5 authentication failed: authentication failure
09:25:01 s-name postfix/smtpd[30120]: disconnect from 82.***.219.***[82.***.219.***]


 The config:


 main.cf:


 myorigin = ****.hu
 smtpd_banner = $myhostname ESMTP $mail_name
biff = no
 append_dot_mydomain = no
readme_directory = no
 myhostname = ****.hu
myorigin = /etc/mailname
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
 inet_interfaces = all
mynetworks_style = host
 local_recipient_maps =
mydestination = 
 content_filter = amavis:[127.0.0.1]:10024
 delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12
 # Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
# Requirements for the sender details
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
# Requirement for the recipient address
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit
smtpd_data_restrictions = reject_unauth_pipelining
 smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
# smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_path = smtpd
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = 
 # require proper helo at connections
smtpd_helo_required = yes
# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes
 alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
 # TLS parameters
smtp_use_tls = yes
smtp_tls_security_level = may
smtpd_use_tls=yes
smtpd_tls_security_level = may
#smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_tls_cert_file=/etc/postfix/postfix.cert
smtpd_tls_key_file=/etc/postfix/postfix.key
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
 

master.cf:
 ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
==========================================================================
smtp      inet  n       -       -       -       -       smtpd
2025      inet  n       -       -       -       -       smtpd
submission inet n       -       -       -       -       smtpd
  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_tls_auth_only=yes
#  -o smtpd_tls_security_level=encrypt
#  -o header_checks=
#  -o body_checks=
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination, reject
  -o smtpd_sasl_security_options=noanonymous,noplaintext
  -o smtpd_sasl_tls_security_options=noanonymous
#  -o milter_macro_daemon_name=ORIGINATING
smtps     inet  n       -       -       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_tls_auth_only=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o smtpd_sasl_security_options=noanonymous,noplaintext
  -o smtpd_sasl_tls_security_options=noanonymous
#  -o milter_macro_daemon_name=ORIGINATING
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
        -o content_filter=
        -o receive_override_options=no_header_body_checks
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
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
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
    -o smtp_fallback_relay=
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
amavis    unix  -       -       -       -       2       smtp
        -o smtp_data_done_timeout=1200
        -o smtp_send_xforward_command=yes
        -o disable_dns_lookups=yes
        -o max_use=20
127.0.0.1:10025 inet  n  -      -       -       -       smtpd
        -o content_filter=
        -o local_recipient_maps=
        -o relay_recipient_maps=
        -o smtpd_restriction_classes=
        -o smtpd_delay_reject=no
        -o smtpd_client_restrictions=permit_mynetworks,reject
        -o smtpd_helo_restrictions=
        -o smtpd_sender_restrictions=
        -o smtpd_recipient_restrictions=permit_mynetworks,reject
        -o smtpd_data_restrictions=reject_unauth_pipelining
        -o smtpd_end_of_data_restrictions=
        -o mynetworks=127.0.0.0/8
        -o smtpd_error_sleep_time=0
        -o smtpd_soft_error_limit=1001
        -o smtpd_hard_error_limit=1000
        -o smtpd_client_connection_count_limit=0
        -o smtpd_client_connection_rate_limit=0
        -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks

---

### Post by noway2 on 2009-08-10
First, turn on password debugging.  You may need to do this in multiple places, i.e. postfix and courier.

Second, it looks like you are attempting to use virtual mailboxes.  Did you create a user account and select the correct hashing method for the password?

Third, if you are still running into trouble, try seeing if you can do some plain text authorizations (turn off the security encryption) and possibly even down a level and use telnet to connect directly to the SMTP and POP/IMAP servers.

---

