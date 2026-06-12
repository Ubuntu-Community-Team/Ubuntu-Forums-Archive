---
title: "Unable to start postfix"
date: 2009-05-01
forum: Server Platforms
---

### Post by satimis on 2009-05-01
Hi folks,

Ubuntu 8.04
Postfix.

On running;

/# /etc/init.d/postfix start ```

 * Starting Postfix Mail Transport Agent postfix                                        postconf: fatal: /etc/postfix/main.cf, line 91: missing '=' after attribute name: "aliasing alias_maps = hash:/etc/postfix/aliases "
postconf: fatal: /etc/postfix/main.cf, line 91: missing '=' after attribute name: "aliasing alias_maps = hash:/etc/postfix/aliases "

```

Line 91```

aliasing alias_maps = hash:/etc/postfix/aliases

```

# cat /etc/postfix/main.cf```

#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
#smtpd_use_tls=yes
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = vz2.satimis.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
#myorigin = /etc/mailname
myorigin = satimis.com
#mydestination = vz2.satimis.com, localhost.satimis.com, , localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
local_recipient_maps = 
mydestination =

# how long if undelivered before sending warning update to sender 
delay_warning_time = 4h 
# will it be a permanent error or temporary 
unknown_local_recipient_reject_code = 450 
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
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit 
# Requirements for the connecting server 
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org 
# Requirement for the recipient address 
# smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit smtpd_data_restrictions = reject_unauth_pipelining
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit

# require proper helo at connections 
smtpd_helo_required = yes 
# waste spammers time before rejecting them 
smtpd_delay_reject = yes 
disable_vrfy_command = yes

# not sure of the difference of the next two 
# but they are needed for local 
aliasing alias_maps = hash:/etc/postfix/aliases 
alias_database = hash:/etc/postfix/aliases 
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

content_filter = amavis:[127.0.0.1]:10024

```


# cat /etc/postfix/master.cf```

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
smtp      inet  n       -       n       -       -       smtpd
amavis      unix  -       -       -       -       2       smtp
 -o smtp_data_done_timeout=1200 
 -o smtp_send_xforward_command=yes 
 -o disable_dns_lookups=yes 
 -o max_use=20
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
 -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject
 -o smtpd_sasl_security_options=noanonymous,noplaintext
 -o smtpd_sasl_tls_security_options=noanonymous
#  -o milter_macro_daemon_name=ORIGINATING
smtps     inet  n       -       -       -       -       smtpd
 -o smtpd_tls_wrappermode=yes
 -o smtpd_sasl_auth_enable=yes
# if you do not want to restrict it encryption only, comment out next line
 -o smtpd_tls_auth_only=yes
 -o smtpd_client_restrictions=permit_sasl_authenticated,reject
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
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

127.0.0.1:10025 inet n - - - - smtpd
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

```

Please advise.  TIA


B.R.
satimis

---

### Post by ephmanjmm on 2009-05-01
I would try removing the word aliasing from line 91.  Actually, I would comment out the entire line (add a # to the beginning) and add a line directly beneath that was identical minus the word aliasing.  That will make it easier to undo the change if it doesn't work.

---

