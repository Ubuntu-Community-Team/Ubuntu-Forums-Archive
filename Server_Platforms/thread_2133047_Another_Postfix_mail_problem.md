---
title: "Another Postfix mail problem"
date: 2013-04-06
forum: Server Platforms
---

### Post by chipwaza on 2013-04-06
Please can Someone Help me!
Here is the output of my /etc/postfix/main.cf


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
delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

#myhostname = lupetaz.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
#myorigin = /etc/mailname
myorigin = lupetaz.com
#mydestination = ns2.lupetaz.com, lupetaz.com, localhost.localdomain, localhost
mydestination =(localservername), localhost.(localservername), www.$mydomain, localhost,ns2.lupetaz.com
local_recipient_maps =
#mydestination =
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128,192.168.1.0/24
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
#***********************************************************************
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
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname,reject_invalid_hostname, permit
# Requirements for the sender details
#smtpd_sender_restrictions = permit_mynetworks, warn_if_reject, reject_non_fqdn_sender,reject_unknown_sender_domain,
#smtpd_data_restrictions = reject_unauth_pipelining
# require proper helo at connections
smtpd_helo_required = yes
# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes
# not sure of the difference of the next two
# but they are needed for local aliasing
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
# this specifies where the virtual mailbox folders will be located
virtual_mailbox_base = /var/spool/mail/virtual
content_filter = smtp-amavis:[127.0.0.1]:10024
# this is for the mailbox location for each user
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
# and this is for aliases
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
# and this is for domain lookups
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
# this is how to connect to the domains (all virtual, but the option is there)
# not used yet
# transport_maps = mysql:/etc/postfix/mysql_transport.cf
#************************************************************************************
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000

#**********************************************************
# SASL
smtpd_sasl_auth_enable = yes
# If your potential clients use Outlook Express or other older clients
# this needs to be set to yes
broken_sasl_auth_clients = yes
#*smtpd_sasl_security_options = noanonymous
#*smtpd_sasl_local_domain =
#*smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks,
#****smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks,
#smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated
#*****************************************************************************************
# TLS parameters
# smtp_use_tls = no
smtp_tls_security_level = may
#***
 #smtpd_use_tls=yes
smtpd_tls_security_level = may
# smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
# smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
# smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt

Here is my /etc/postfix/master.cf

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
#smtp      inet  n       -       -       -       1       postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
#submission inet n       -       -       -       -       smtpd
#  -o syslog_name=postfix/submission
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o syslog_name=postfix/smtps
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
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
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
#***************************************************************************
smtp-amavis     unix     -     -     -     -     2         smtp
    -o smtp_data_done_timeout=1200
    -o smtp_send_xforward_command=yes
    -o disable_dns_lookups=yes
    -o max_use=20

127.0.0.1:10025     inet     n     -     -     -     -     smtpd
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
    -o content_filter=
    -o receive_override_options=no_header_body_checks
#*****************************************************************************************
submission     inet     n     -     n     -     -     smtpd
    -o smtpd_sasl_auth_enable=yes
## if you do not want to restrict it encryption only, comment out next line<
    -o smtpd_tls_auth_only=yes
## -o smtpd_tls_security_level=encrypt
## -o header_checks=
## -o body_checks=<
    -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject
    -o smtpd_sasl_security_options=noanonymous,noplaintext
    -o smtpd_sasl_tls_security_options=noanonymous
## -o milter_macro_daemon_name=ORIGINATING<
smtps     inet     n     -     -     -     -     smtpd
    -o smtpd_tls_wrappermode=yes
    -o smtpd_sasl_auth_enable=yes
    -o smtpd_tls_auth_only=yes
    -o smtpd_client_restrictions=permit_sasl_authenticated,reject
    -o smtpd_sasl_security_options=noanonymous,noplaintext
    -o smtpd_sasl_tls_security_options=noanonymous
## -o milter_macro_daemon_name=ORIGINATING

Here is my /var/log/mail.log
Apr  6 18:28:53 ns2 postfix/qmgr[22147]: CECE0809A1: removed
Apr  6 18:28:53 ns2 postfix/local[32121]: DB5DD804DA:  to=<root@localhost>, orig_to=<info@lupetaz.com>,  relay=local, delay=0.26, delays=0.05/0.16/0/0.06, dsn=5.4.6,  status=bounced (mail forwarding loop for root@localhost)
Apr  6 18:28:53 ns2 postfix/qmgr[22147]: DB5DD804DA: removed
Apr  6 18:32:42 ns2 postfix/smtpd[32180]: connect from ns2.lupetaz.com[192.168.1.100]
Apr  6 18:32:42 ns2 postfix/smtpd[32180]: Anonymous TLS connection  established from ns2.lupetaz.com[192.168.1.100]: SSLv3 with cipher  DHE-RSA-CAMELLIA256-SHA (256/256 bits)
Apr  6 18:32:42 ns2 postfix/smtpd[32180]: NOQUEUE: reject: RCPT from  ns2.lupetaz.com[192.168.1.100]: 554 5.7.1  <ns2.lupetaz.com[192.168.1.100]>: Client host rejected: Access  denied; from=<chipwaza@lupetaz.com>  to=<chipwaza@lupetaz.com> proto=ESMTP helo=<[192.168.1.100]>
Apr  6 18:32:42 ns2 postfix/smtpd[32180]: lost connection after RCPT from ns2.lupetaz.com[192.168.1.100]
Apr  6 18:32:42 ns2 postfix/smtpd[32180]: disconnect from ns2.lupetaz.com[192.168.1.100]
Apr  6 18:32:44 ns2 postfix/smtpd[32180]: connect from ns2.lupetaz.com[192.168.1.100]
Apr  6 18:32:44 ns2 postfix/smtpd[32180]: Anonymous TLS connection  established from ns2.lupetaz.com[192.168.1.100]: SSLv3 with cipher  DHE-RSA-CAMELLIA256-SHA (256/256 bits)
Apr  6 18:32:44 ns2 postfix/smtpd[32180]: NOQUEUE: reject: RCPT from  ns2.lupetaz.com[192.168.1.100]: 554 5.7.1  <ns2.lupetaz.com[192.168.1.100]>: Client host rejected: Access  denied; from=<chipwaza@lupetaz.com>  to=<chipwaza@lupetaz.com> proto=ESMTP helo=<[192.168.1.100]>
Apr  6 18:32:44 ns2 postfix/smtpd[32180]: lost connection after RCPT from ns2.lupetaz.com[192.168.1.100]
Apr  6 18:32:44 ns2 postfix/smtpd[32180]: disconnect from ns2.lupetaz.com[192.168.1.100]
Apr  6 18:36:15 ns2 postfix/smtpd[32261]: connect from ns2.lupetaz.com[192.168.1.100]
Apr  6 18:36:15 ns2 postfix/smtpd[32261]: Anonymous TLS connection  established from ns2.lupetaz.com[192.168.1.100]: SSLv3 with cipher  DHE-RSA-CAMELLIA256-SHA (256/256 bits)
Apr  6 18:36:15 ns2 postfix/smtpd[32261]: NOQUEUE: reject: RCPT from  ns2.lupetaz.com[192.168.1.100]: 554 5.7.1  <ns2.lupetaz.com[192.168.1.100]>: Client host rejected: Access  denied; from=<chipwaza@lupetaz.com>  to=<cchipwaza23@gmail.com> proto=ESMTP  helo=<[192.168.1.100]>
Apr  6 18:36:15 ns2 postfix/smtpd[32261]: lost connection after RCPT from ns2.lupetaz.com[192.168.1.100]
Apr  6 18:36:15 ns2 postfix/smtpd[32261]: disconnect from ns2.lupetaz.com[192.168.1.100]
Apr  6 18:36:39 ns2 postfix/smtpd[32261]: connect from ns2.lupetaz.com[192.168.1.100]
Apr  6 18:36:39 ns2 postfix/smtpd[32261]: Anonymous TLS connection  established from ns2.lupetaz.com[192.168.1.100]: SSLv3 with cipher  DHE-RSA-CAMELLIA256-SHA (256/256 bits)
Apr  6 18:36:39 ns2 postfix/smtpd[32261]: NOQUEUE: reject: RCPT from  ns2.lupetaz.com[192.168.1.100]: 554 5.7.1  <ns2.lupetaz.com[192.168.1.100]>: Client host rejected: Access  denied; from=<chipwaza@lupetaz.com>  to=<cchipwaza23@gmail.com> proto=ESMTP  helo=<[192.168.1.100]>
Apr  6 18:36:39 ns2 postfix/smtpd[32261]: lost connection after RCPT from ns2.lupetaz.com[192.168.1.100]
Apr  6 18:36:39 ns2 postfix/smtpd[32261]: disconnect from ns2.lupetaz.com[192.168.1.100]

my /etc/hosts

127.0.0.1    localhost.lupetaz.com    localhost
192.168.1.100    ns2.lupetaz.com   ns2

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

results for dig lupetaz.com MX
; <<>> DiG 9.8.1-P1 <<>> lupetaz.com MX
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 40084
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;lupetaz.com.            IN    MX

;; ANSWER SECTION:
lupetaz.com.        604800    IN    MX    100 ns2.lupetaz.com.

;; AUTHORITY SECTION:
lupetaz.com.        604800    IN    NS    ns2.lupetaz.com.

;; ADDITIONAL SECTION:
ns2.lupetaz.com.    604800    IN    A    192.168.1.100

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Apr  6 19:09:31 2013
;; MSG SIZE  rcvd: 79

results for dig lupetaz.com any

;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 14699
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 1

;; QUESTION SECTION:
;lupetaz.com.            IN    ANY

;; ANSWER SECTION:
lupetaz.com.        604800    IN    SOA    ns2.lupetaz.com. info.lupetaz.com. 5 604800 86400 2419200 604800
lupetaz.com.        604800    IN    MX    100 ns2.lupetaz.com.
lupetaz.com.        604800    IN    NS    ns2.lupetaz.com.
lupetaz.com.        604800    IN    A    127.0.0.1
lupetaz.com.        604800    IN    AAAA    ::1

;; ADDITIONAL SECTION:
ns2.lupetaz.com.    604800    IN    A    192.168.1.100

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Apr  6 19:10:37 2013
;; MSG SIZE  rcvd: 164
```

Please I need you help to solve this.Thanks:smile:

---

### Post by AvengerX9 on 2013-04-06
You should use the bbcode tags for the content of your file and the logs.

---

### Post by smtp on 2013-04-06
postconf | grep -i "smtpd_recipient_restrictions"

and paste results here, please.

---

### Post by Iowan on 2013-04-06
I've moved your post to a separate thread to concentrate on YOUR problem.
As a side-benefit, you can mark it [SOLVED] when you get the solution.

---

### Post by chipwaza on 2013-04-07
here is the results of 


root@ns2:~# postconf | grep -i "smtpd_recipient_restrictions"
smtpd_recipient_restrictions = permit_mynetworks, reject_unauth_destination

---

### Post by chipwaza on 2013-04-07
This is the output
smtpd_recipient_restrictions = permit_mynetworks, reject_unauth_destination

---

### Post by chipwaza on 2013-04-07
thanks for notification, once it is clear i will inform you.

---

### Post by volkswagner on 2013-04-08
Please post your symptom/problem in the first post.  Also post your network details such as residential or commercial isp account (static or dynamic public ip ), etc.

---

### Post by smtp on 2013-04-11
Does the problem still exists?

---

