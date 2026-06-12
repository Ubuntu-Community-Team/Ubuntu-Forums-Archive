---
title: "testsaslauthd failure in postfix+cyrus+postfixadmin"
date: 2014-11-30
forum: Server Platforms
---

### Post by man7 on 2014-11-30
hi,
I installed postfix, postfixadmin and cyrus for smtp auth .I got the error when test saslauth:

 testsaslauthd -u root -p 1  -f /var/spool/postfix/var/run/saslauthd/mux -s smtp
[COLOR=#b22222]0: NO "authentication failed"[/COLOR]
 testsaslauthd -u root -p 1  -f /var/spool/postfix/var/run/saslauthd/mux
[COLOR=#b22222]0: OK "Success."[/COLOR]
 testsaslauthd -u [EMAIL="farmani@test.com"]user1@test.com[/EMAIL]  -p 1  -f /var/spool/postfix/var/run/saslauthd/mux -s smtp
[COLOR=#b22222]0: NO "authentication failed"[/COLOR]


 my config files is like this:
postconf -n:

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
enable_original_recipient = no
header_checks = regexp:/etc/postfix/header_checks
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = ipv4
mailbox_size_limit = 0
mydestination =
mydomain = test.com
myhostname = test.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 172.0.0.0/8
myorigin = /etc/hostname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks reject_sender_login_mismatch permit_sasl_authenticated reject_unauth_destination smtpd_sender_login_maps = hash:/etc/postfix/controlled_envelope_senders smtpd_recipient_restrictions = reject_sender_login_mismatch permit_sasl_authenticated
smtpd_relay_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_tls_security_options = $smtpd_sasl_security_options
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf, mysql:/etc/postfix/mysql_virtual_alias_domainaliases_maps.cf
virtual_gid_maps = static:8
virtual_mailbox_base = /var/vmail
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf, mysql:/etc/postfix/mysql_virtual_mailbox_domainaliases_maps.cf
virtual_transport = dovecot
virtual_uid_maps = static:150


/etc/default/sasauthd

START=yes
DESC="SASL Authentication Daemon"
NAME="saslauthd"
MECHANISMS="pam"
MECH_OPTIONS=""
THREADS=5
OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd -r"

/etc/postfix/sasl/smtpd

pwcheck_method: saslauthd
mech_list: PLAIN LOGIN
log_level: 5


/etc/postfix/master.cf

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
smtp       inet  n       -       n       -       -       smtpd
#smtp      inet  n       -       -       -       1       postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
#submission inet n       -       -       -       -       smtpd
#  -o syslog_name=postfix/submission
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=
#  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
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
  flags=DRhu user=vmail argv=/usr/lib/dovecot/dovecot-lda -d $(recipient)
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

#127.0.0.1:10025 inet    n       -       -       -       -       smtpd
 # -o content_filter=
  #-o local_recipient_maps=
  #-o relay_recipient_maps=
  #-o smtpd_restriction_classes=
  #-o smtpd_delay_reject=no
#  -o smtpd_client_restrictions=permit_mynetworks,reject
#  -o sm#tpd_helo_restrictions=
 # -o smtpd_sender_restrictions=
 # -o smtpd_recipient_restrictions=permit_mynetworks,reject
 # -o smtpd_data_restrictions=reject_unauth_pipelining
#  -o smtpd_end_of_data_restrictions=
 # -o mynetworks=127.0.0.0/8
 # -o smtpd_error_sleep_time=0
#  -o smtpd_soft_error_limit=1001
 # -o smtpd_hard_error_limit=1000
#  -o smtpd_client_connection_count_limit=0
 # -o smtpd_client_connection_rate_limit=0
#  -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks

# Integration with Dovecot - hand mail over to it for local delivery, and
# run the process under the vmail user and mail group.
dovecot      unix   -        n      n       -       -   pipe
  flags=DRhu user=vmail:mail argv=/usr/lib/dovecot/dovecot-lda -d $(recipient)



/etc/pam.d/

auth       required       pam_mysql.so user=admin passwd=123 host=127.0.0.1 db=postfixadmin table=mailbox usercolumn=username  passwdcolumn=password verbose=1 crypt=1 md5=1
account  sufficient   pam_mysql.so user=admin passwd=123 host=127.0.0.1 db=postfixadmin table=mailbox usercolumn=username  passwdcolumn=password verbose=1 crypt=1 md5=1

---

### Post by man7 on 2014-11-30
I dont know what happend but finally I got success  in sasl test.
testsaslauthd -u [email]user1@test.com[/email]  -p 1  -f /var/spool/postfix/var/run/saslauthd/mux -s smtp
0: OK "Success."

while get this message in telnet .
root@behpardakht:~# telnet 172.18.100.254 25
Trying 172.18.100.254...
Connected to 172.18.100.254.
Escape character is '^]'.
220 test.com ESMTP Postfix (Ubuntu)
EHLO localhost
250-test.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
AUTH PLAIN dkdobFkQGJlafdgdbQBBUXdlcdkkKBBHs=
535 5.7.8 Error: authentication failed: generic failure


/var/log/mail.log

warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory
Nov 30 14:31:52 test postfix/smtpd[1923]: warning: SASL authentication failure: Password verification failed
Nov 30 14:31:52 test postfix/smtpd[1923]: warning: unknown[172.18.100.254]: SASL PLAIN authentication failed: generic failure

---

