---
title: "Email server sends mail but does not receive"
date: 2020-05-07
forum: Server Platforms
---

### Post by Robert_Boutin on 2020-05-07
Ubuntu 18.04 VBox guest in 16.04 host.  Email was working great with no problems until my ISP had issues with my static ip block and I lost connectivity (ARP table needed to be flushed).  I thought it was my server and in trying to find the problem, I messed something up and now my mail server will not receive external email.  It sends successfully to my gmail account and it will receive email sent within my network but I've googled everything I could find and I can't find a reason why external email isn't receiving.  UFW is not blocking 25, nor is my hardware firewall.  Router isn't blocking any ports.

tail -f /var/log/mail.log shows no activity when I send an email from gmail.

This is a business internet account so port 25 isn't blocked by my ISP.  I can telnet to port 25 of the public ip of the server and it connects.  I think it's just one little tweak to fix this, I just can't figure out what that tweak is.  Any suggestions are greatly appreciated.  Thanks

```
_**telnet X.X.X.11 25**_

user@mail:~$ telnet X.X.X.11 25
Trying 50.4.127.11...
Connected to X.X.X.11.
Escape character is '^]'.
220 mail.tld.com ESMTP Postfix
ehlo visitor.com
250-mail.domain.com
250-PIPELINING
250-SIZE
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN



**_main.cf_**

smtpd_banner = $myhostname ESMTP $mail_name
biff = no


# appending .domain is the MUA's job.
append_dot_mydomain = no


# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h


readme_directory = /usr/share/doc/postfix


# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


#SPF timeout
#policyd-spf_time_limit = 3600
policy-spf_time_limit = 3600s
#
smtpd_relay_restrictions = permit_mynetworks, permit_sasl_authenticated, defer_unauth_destination
myhostname = mail.domain.com
alias_maps = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
alias_database = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
mydestination = localhost, localhost.localdomain
relayhost =
mynetworks = 127.0.0.0/8 [::1]/128 192.168.1.0/24
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains =
virtual_alias_maps = hash:/var/lib/mailman/data/virtual-mailman, proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, proxy:mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /var/vmail
virtual_uid_maps = mysql:/etc/postfix/mysql-virtual_uids.cf
virtual_gid_maps = mysql:/etc/postfix/mysql-virtual_gids.cf
sender_bcc_maps = proxy:mysql:/etc/postfix/mysql-virtual_outgoing_bcc.cf
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_restriction_classes = greylisting
greylisting = check_policy_service inet:127.0.0.1:10023
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_client_access hash:/etc/postfix/rbl_override, reject_unauth_destination, reject_rbl_client zen.spamhaus.org, check_recipient_access mysql:/etc/pos$
        check_policy_service unix:private/policy-spf,
        check_client_access hash:/etc/postfix/rbl_override,
        reject_rbl_client multi.uribl.com,
        reject_rbl_client dul.dnsbl.sorbs.net,
        reject_rbl_client list.dsbl.org,
        reject_rbl_client dnsbl.sorbs.net,
smtpd_tls_security_level = may
transport_maps = hash:/var/lib/mailman/data/transport-mailman, proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
smtpd_sender_login_maps = proxy:mysql:/etc/postfix/mysql-virtual_sender_login_maps.cf
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $sender_bcc_maps $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canoni$
smtpd_delay_reject = yes
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_sasl_authenticated, permit_mynetworks, check_helo_access regexp:/etc/postfix/helo_access, reject_invalid_hostname, reject_non_fqdn_hostname, reject_invalid_helo_hostname, reject_unknown_helo_hostn$
smtpd_sender_restrictions = check_sender_access regexp:/etc/postfix/tag_as_originating.re , permit_mynetworks, permit_sasl_authenticated, check_sender_access mysql:/etc/postfix/mysql-virtual_sender.cf, check_sender_access regexp:$
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual_client.cf
smtpd_client_message_rate_limit = 100
maildrop_destination_concurrency_limit = 1
maildrop_destination_recipient_limit = 1
virtual_transport = dovecot
header_checks = regexp:/etc/postfix/header_checks
mime_header_checks = regexp:/etc/postfix/mime_header_checks
nested_header_checks = regexp:/etc/postfix/nested_header_checks
body_checks = regexp:/etc/postfix/body_checks
owner_request_special = no
smtp_tls_security_level = may
smtpd_tls_mandatory_protocols = !SSLv2, !SSLv3
smtpd_tls_protocols = !SSLv2,!SSLv3
smtp_tls_protocols = !SSLv2,!SSLv3
smtpd_tls_exclude_ciphers = RC4, aNULL
smtp_tls_exclude_ciphers = RC4, aNULL
dovecot_destination_recipient_limit = 1
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
message_size_limit = 0



**_master.cf_**

# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (no)    (never) (100)
# ==========================================================================
smtp       inet  n       -       y       -       -       smtpd
#smtp      inet  n       -       y       -       1       postscreen
#smtpd     pass  -       -       y       -       -       smtpd
#dnsblog   unix  -       -       y       -       0       dnsblog
#tlsproxy  unix  -       -       y       -       0       tlsproxy
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=
#  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
submission inet  n       -       y       -       -       smtpd
    -o syslog_name=postfix/submission
    -o smtpd_tls_security_level=encrypt
    -o smtpd_sasl_auth_enable=yes
    -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=
#  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       y       -       -       qmqpd
smtps      inet  n       -       y       -       -       smtpd
    -o syslog_name=postfix/smtps
    -o smtpd_tls_wrappermode=yes
    -o smtpd_sasl_auth_enable=yes
    -o smtpd_client_restrictions=permit_sasl_authenticated,reject
pickup    unix  n       -       y       60      1       pickup
cleanup   unix  n       -       y       -       0       cleanup
qmgr      unix  n       -       n       300     1       qmgr
#qmgr     unix  n       -       n       300     1       oqmgr
tlsmgr    unix  -       -       y       1000?   1       tlsmgr
rewrite   unix  -       -       y       -       -       trivial-rewrite
bounce    unix  -       -       y       -       0       bounce
defer     unix  -       -       y       -       0       bounce
trace     unix  -       -       y       -       0       bounce
verify    unix  -       -       y       -       1       verify
flush     unix  n       -       y       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       y       -       -       smtp
relay     unix  -       -       y       -       -       smtp
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       y       -       -       showq
error     unix  -       -       y       -       -       error
retry     unix  -       -       y       -       -       error
discard   unix  -       -       y       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       y       -       -       lmtp
anvil     unix  -       -       y       -       1       anvil
scache    unix  -       -       y       -       1       scache
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
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d vmail ${extension} ${recipient} ${user} ${nexthop} ${sender}
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
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}


dovecot   unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail:vmail argv=/usr/lib/dovecot/deliver -f ${sender} -d ${user}@${nexthop}


amavis     unix  -       -       y       -       2       smtp
    -o smtp_data_done_timeout=1200
    -o smtp_send_xforward_command=yes
127.0.0.1:10025 inet n - n - - smtpd
        -o content_filter=
        -o local_recipient_maps=
        -o relay_recipient_maps=
        -o smtpd_restriction_classes=
        -o smtpd_client_restrictions=
        -o smtpd_helo_restrictions=
        -o smtpd_sender_restrictions=
        -o smtpd_recipient_restrictions=permit_mynetworks,reject
        -o mynetworks=127.0.0.0/8
        -o strict_rfc821_envelopes=yes
        -o receive_override_options=no_unknown_recipient_checks,no_header_body_checks
        -o smtp_send_xforward_command=yes
        -o disable_dns_lookups=yes




127.0.0.1:10027 inet n - n - - smtpd
        -o content_filter=
        -o local_recipient_maps=
        -o relay_recipient_maps=
        -o smtpd_restriction_classes=
        -o smtpd_client_restrictions=
        -o smtpd_helo_restrictions=
        -o smtpd_sender_restrictions=
        -o smtpd_recipient_restrictions=permit_mynetworks,reject
        -o mynetworks=127.0.0.0/8
        -o strict_rfc821_envelopes=yes
        -o receive_override_options=no_unknown_recipient_checks,no_header_body_checks
        -o smtp_send_xforward_command=yes
            -o milter_default_action=accept
        -o milter_macro_daemon_name=ORIGINATING
        -o disable_dns_lookups=yes
# 2016-09-14 Added sender policy framework
# policyd-spf  unix  -       n       n       -       0       spawn
#     user=policyd-spf argv=/usr/bin/policyd-spf
policy-spf  unix  -       n       n       -       -       spawn
     user=nobody argv=/usr/bin/policyd-spf
```

---

### Post by wildmanne39 on 2020-05-07
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by SeijiSensei on 2020-05-08
```
mydestination = localhost, localhost.localdomain
```

If you want to receive mail as [email]someone@domain.name[/email], domain.name must be in the mydestination list.  As it stands now, it will only accept mail for someone@localhost or [email]someone@localhost.locald[/email]omain.

If you telnet to the SMTP port, you can simulate an SMTP session after an EHLO and the various 250 replies like this:
```


MAIL FROM: seijisensei@example.com
250 2.1.0 seijisensei@example.com ... Sender ok
RCPT TO: seijisensei@ubuntuforums.com
250 2.1.5 seijisensei@ubuntuforums.com ... Recipient ok
DATA
354 Enter mail, end with "." on a line by itself
Type some random message.
.

```
(You don't need to capitalize in practice; it's case-insensitive.)  

If there is a problem, the error messages might help you diagnose why.  Also /var/log/mail.log can help.

---

### Post by Robert_Boutin on 2020-05-12
Thanks, it actually was a more simple fix... I thought my router firewall had everything open, it didn't.  As soon as I added a rule to accept all port 25 traffic, it started working correctly.

---

