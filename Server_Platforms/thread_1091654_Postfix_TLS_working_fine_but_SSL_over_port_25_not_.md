---
title: "Postfix TLS working fine but SSL over port 25 not working"
date: 2009-03-09
forum: Server Platforms
---

### Post by trileru808 on 2009-03-09
Hello. I have an Ubuntu Server 8.10 with postfix/courier installed. Everything works perfect, pop3 over 110 and 995, imap on 143 and 993, normal smtp and tls smtp on 25 work perfect. The only problem is on ssl smtp over port 25. It just doesn't work. Nor 465 or 587. I will put the postfix config files below:

root@server1:/home/hackish# cat /etc/postfix/main.cf
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific: Specifying a file name will cause the first
# line of that file to be used as the name. The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
#smtpd_tls_ask_ccert = yes
#smtpd_tls_req_ccert = no
smtp_tls_cert_file = /etc/postfix/ssl/smtp.crt
smtp_tls_key_file = /etc/postfix/ssl/smtp.key
smtp_tls_CAfile = /etc/postfix/ssl/cacertt.pem

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

mydomain = example.com
myhostname = mail.example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = /etc/postfix/local-host-names
relayhost =
mynetworks = 89.xxx.yyy.0/30, 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,rejec t_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 2
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
message_size_limit=102400000
virtual_maps = hash:/etc/postfix/virtusertable



root@server1:/home/hackish# cat /etc/postfix/master.cf
#
# Postfix master process configuration file. For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type private unpriv chroot wakeup maxproc command + args
# (yes) (yes) (yes) (never) (100)
# ==========================================================================
smtp inet n - - - - smtpd
#submission inet n - - - - smtpd
smtps inet n - - - - smtpd
# -o smtpd_tls_security_level=encrypt
# -o smtpd_sasl_auth_enable=yes
# -o smtpd_client_restrictions=permit_sasl_authenticated,reject
# -o milter_macro_daemon_name=ORIGINATING
# -o smtpd_tls_wrappermode=yes
# -o smtpd_sasl_auth_enable=yes
# -o smtpd_sasl_auth_enable=yes
# -o smtpd_client_restrictions=permit_sasl_authenticated,reject
# -o milter_macro_daemon_name=ORIGINATING
#628 inet n - - - - qmqpd
pickup fifo n - - 60 1 pickup
cleanup unix n - - - 0 cleanup
qmgr fifo n - n 300 1 qmgr
#qmgr fifo n - - 300 1 oqmgr
tlsmgr unix - - - 1000? 1 tlsmgr
rewrite unix - - - - - trivial-rewrite
bounce unix - - - - 0 bounce
defer unix - - - - 0 bounce
trace unix - - - - 0 bounce
verify unix - - - - 1 verify
flush unix n - - 1000? 0 flush
proxymap unix - - n - - proxymap
proxywrite unix - - n - 1 proxymap
smtp unix - - - - - smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay unix - - - - - smtp
-o smtp_fallback_relay=
# -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq unix n - - - - showq
error unix - - - - - error
retry unix - - - - - error
discard unix - - - - - discard
local unix - n n - - local
virtual unix - n n - - virtual
lmtp unix - - - - - lmtp
anvil unix - - - - 1 anvil
scache unix - - - - 1 scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent. See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop unix - n n - - pipe
flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp unix - n n - - pipe
flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail unix - n n - - pipe
flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp unix - n n - - pipe
flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix - n n - 2 pipe
flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman unix - n n - - pipe
flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
${nexthop} ${user}



Also if you could suggest any other tweaks or security upgrades you are very welcome. Thank you very much and have a nice day :)

---

### Post by hyper_ch on 2009-03-09
is there a reason why you prefer ssl over tls?

---

### Post by trileru808 on 2009-03-10
> **hyper_ch said:**
> is there a reason why you prefer ssl over tls?

Yes, some of the clients that use this email have Microsoft Outlook 2003 witch only know of ssl, not tls.

---

### Post by hyper_ch on 2009-03-10
what does mail.log say?

---

### Post by trileru808 on 2009-03-10
> **hyper_ch said:**
> what does mail.log say?

Mar 10 16:47:38 server1 postfix/smtpd[9297]: connect from unknown[86.xxx.yyy.zzz]
Mar 10 16:47:38 server1 postfix/smtpd[9297]: lost connection after UNKNOWN from unknown[86.xxx.yyy.zzz]
Mar 10 16:47:38 server1 postfix/smtpd[9297]: disconnect from unknown[86.xxx.yyy.zzz]
Mar 10 16:47:39 server1 postfix/smtpd[9297]: connect from unknown[86.xxx.yyy.zzz]
Mar 10 16:47:39 server1 postfix/smtpd[9297]: lost connection after UNKNOWN from unknown[86.xxx.yyy.zzz]
Mar 10 16:47:39 server1 postfix/smtpd[9297]: disconnect from unknown[86.xxx.yyy.zzz]

---

### Post by hyper_ch on 2009-03-10
and auth.log? well, I have no clue, I only use tls. never tried ssl to get running on postfix.

---

