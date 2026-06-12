---
title: "Postfix/Amavis Problems (Too many hops...)"
date: 2008-07-22
forum: Server Platforms
---

### Post by LPomfrey on 2008-07-22
Every mail I try to send through postfix is being returned with an error of "Too many hops..." 

It seems like mail is bouncing between postfix and amavis for a time and then being rejected.

I've googled around but I can't seem to find a solutions that a) works and b) I haven't tried. 

Here's my /etc/postfix/main.cf:
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

# will it be a permanent error or temporary 
unknown_local_recipient_reject_code = 450 

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/postfix.cert
smtpd_tls_key_file = /etc/postfix/ssl/postfix.key
smtpd_use_tls = yes
smtp_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_tls_loglevel = 1

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

mydomain = lukepomfrey.org
myhostname = mail.lukepomfrey.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = mail.lukepomfrey.org
mydestination = 
relayhost = mail.lukepomfrey.org:587
relay_domains = $myhostname,$mydomain,localhost,mail.lukepomfrey.org,lukepomfrey.org,mail.northfleeteaglesfc.org,northfleeteaglesfc.org
mynetworks = 
mynetworks_style = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
masquerade_domains = mail.lukepomfrey.org,mail.northfleeteaglesfc.org


# how long to keep message on queue before return as failed. 
# some have 3 days, I have 16 days as I am backup server for some people 
# whom go on holiday with their server switched off. 
maximal_queue_lifetime = 7d 

# max and min time in seconds between retries if connection failed 
minimal_backoff_time = 1000s 
maximal_backoff_time = 8000s 

# how long to wait when servers connect before receiving rest of data 
smtp_helo_timeout = 60s 

# how many address can be used in one message. 
# effective stopper to mass spammers, accidental copy in whole address list 
# but may restrict intentional mail shots. 
smtpd_recipient_limit = 16 

# how many error before back off. 
smtpd_soft_error_limit = 3 

# how many max errors before blocking it. 
smtpd_hard_error_limit = 12

# Requirements for the HELO statement 
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit 

# Requirements for the sender details 
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit 

# Requirements for the connecting server 
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org, permit 

# Requirement for the recipient address 
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_auth_destination, reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, check_policy_service inet:127.0.0.1:60000, reject_unauth_destination, permit

# Requirement for data restrictions
#smtpd_data_restrictions = reject_unauth_pipelining

# require proper helo at connections 
smtpd_helo_required = yes 

# waste spammers time before rejecting them 
smtpd_delay_reject = yes 
disable_vrfy_command = yes 

# this specifies where the virtual mailbox folders will be located 
virtual_mailbox_base = /var/spool/mail/virtual 

# this is for the mailbox location for each user 
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf 

# and their user id 
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf 

# and group id 
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf 

# and this is for aliases 
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf 

# and this is for domain lookups 
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf 

# this is how to connect to the domains (all virtual, but the option is there) 
# not used yet 
# transport_maps = mysql:/etc/postfix/mysql_transport.cf

content_filter = smtp-amavis:[127.0.0.1]:10024
smtp-amavis_destination_concurrency_limit = 2
#receive_override_options = no_address_mappings


# SASL SUPPORT FOR CLIENTS
#
# The following options set parameters needed by Postfix to enable
# Cyrus-SASL support for authentication of mail clients.
#

smtpd_sasl_authenticated_header = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
broken_sasl_auth_clients = yes
smtpd_tls_auth_only = no
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2

```

And here's my /etc/postfix/master.cf:
```
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
587      inet  n       -       -       -       -       smtpd
   -o cleanup_service_name=pre-cleanup
submission inet n       -       -       -       -       smtpd
  -o smtpd_enforce_tls=yes
  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
smtps     inet  n       -       -       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
   #-o content_filter=
   -o receive_override_options=no_header_body_checks
cleanup   unix  n       -       -       -       0       cleanup
   -o mime_header_checks=
   -o nested_header_checks=
   -o body_checks=
   -o header_checks=
qmgr      fifo  n       -       -       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
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
scache	  unix	-	-	-	-	1	scache
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
maildrop  unix  -       n       -       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       -       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       -       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       -       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix	-	-	-	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       -       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
smtp-amavis     unix    -       -       -       -       2       smtp
    -o smtp_data_done_timeout=1200
    -o smtp_send_xforward_command=yes
    -o disable_dns_lookups=yes
    -o max_use=20
127.0.0.1:10025 inet    n       -       -       -       -       smtpd
    -o content_filter=
    -o local_recipient_maps=
    -o relay_recipient_maps=
    -o smtpd_restriction_classes=
    -o smtpd_delay_reject=no
    -o smtpd_client_restrictions=
    -o smtpd_helo_restrictions=
    -o smtpd_sender_restrictions=
    -o smtpd_recipient_restrictions=permit_mynetworks,permit_sasl_authenticated,permit_auth_destination,reject
    -o smtpd_data_restrictions=
    -o smtpd_end_of_data_restrictions=
    -o mynetworks=127.0.0.0/8
    -o smtpd_error_sleep_time=0
    -o smtpd_soft_error_limit=1001
    -o smtpd_hard_error_limit=1000
    -o smtpd_client_connection_count_limit=0
    -o smtpd_client_connection_rate_limit=0
    -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks
pre-cleanup unix       n       -       -       -       0       cleanup
   -o virtual_alias_maps=
   -o canonical_maps=
   -o sender_canonical_maps=
   -o recipient_canonical_maps=
   -o masquerade_domains=

```

EDIT: This might have something to do with my SASL set up. For some reason although I can send mail internally it's almost as if Postfix doesn't recognise when people are authenticated with SASL. I've copied /etc/sasldb2 to /var/spool/postfix/etc/sasldb2, linked the contents of /usr/lib/sasl2 in /var/spool/postfix/usr/lib/sasl2, and linked /etc/pam.d/smtp in /var/spool/postfix/etc/pam.d/smtp, but I'm still getting messages saying that relay access is denied in mail.log along with the occasional "Too many hops" message. :confused:

---

