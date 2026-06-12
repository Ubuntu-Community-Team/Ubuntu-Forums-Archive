---
title: "No mail, incoming or outgoing..."
date: 2012-12-11
forum: Server Platforms
---

### Post by DM061 on 2012-12-11
Hello, (Sorry if this is posted in the wrong area, or already being covered elsewhere, but i am new to ubuntu server, and this issue is driving me mad)

I thank you for any light you may be able to shed on this issue.

I am having trouble with my mail server, i can send and receive mail locally with telnet or netcat via port 25 e.g telnet localhost, i can even telnet mail.example on port 25.

But i can't mail out to hotmail, my mail.log says connection timed out.

Now here is the confusing part, it times out on every port i try...

I have phoned my ISP and they assure me, port 25 is not blocked, it is open on my router and the firewall is not blocking it.

I use postfix and courier (pop and imap)
Is there something else i need?

I am happy to provide additional info, i know it must be something soooo simple i am missing.....

Again, i thank you for any help you can provide.

DM061

---

### Post by nebileix on 2012-12-12
Please post your postfix conf. Please do replace your sensitive information like domain, ip etc..

---

### Post by DM061 on 2012-12-12
Thanks for your reply, i don't have a postfix.conf by here are the main and master cf files.
 
This is my main.cf
 
> # Debian specific: Specifying a file name will cause the first
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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
myhostname = mail.example.co.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.example.co.uk, example.co.uk, localhost.example.co.uk, localhost
relayhost =
mynetworks = 127.0.0.0/8, xxx.xxx.x.x/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
mailbox_command =
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
 
And here is the master.cf
 
> #
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
#smtp inet n - - - 1 postscreen
#smtpd pass - - - - - smtpd
#dnsblog unix - - - - 0 dnsblog
#tlsproxy unix - - - - 0 tlsproxy
submission inet n - - - - smtpd
# -o syslog_name=postfix/submission
# -o smtpd_tls_security_level=encrypt
# -o smtpd_sasl_auth_enable=yes
# -o smtpd_client_restrictions=permit_sasl_authenticated,reject
# -o milter_macro_daemon_name=ORIGINATING
#smtps inet n - - - - smtpd
# -o syslog_name=postfix/smtps
# -o smtpd_tls_wrappermode=yes
# -o smtpd_sasl_auth_enable=yes
# -o smtpd_client_restrictions=permit_sasl_authenticated,reject
# -o milter_macro_daemon_name=ORIGINATING
#628 inet n - - - - qmqpd
pickup fifo n - - 60 1 pickup
cleanup unix n - - - 0 cleanup
qmgr fifo n - n 300 1 qmgr
#qmgr fifo n - n 300 1 oqmgr
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
relay unix - - - - - smtp
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
# ====================================================================
#
# Recent Cyrus versions can use the existing "lmtp" master.cf entry.
#
# Specify in cyrus.conf:
# lmtp cmd="lmtpd -a" listen="localhost:lmtp" proto=tcp4
#
# Specify in main.cf one or more of the following:
# mailbox_transport = lmtp:inet:localhost
# virtual_transport = lmtp:inet:localhost
#
# ====================================================================
#
# Cyrus 2.1.5 (Amos Gouaux)
# Also specify in main.cf: cyrus_destination_recipient_limit=1
#
#cyrus unix - n n - - pipe
# user=cyrus argv=/cyrus/bin/deliver -e -r ${sender} -m ${extension} ${user}
#
# ====================================================================
# Old example of delivery via Cyrus.
#
#old-cyrus unix - n n - - pipe
# flags=R user=cyrus argv=/cyrus/bin/deliver -e -m ${extension} ${user}
#
# ====================================================================
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

---

### Post by petarpetrovic on 2012-12-12
I'm not sure that this will solve your problem, but it may point you in the right direction. Namely, it seems that you have to add a Courier parameters in your master.cf file. I don't know what that is for Courier since I use Dovecot instead, but you can try Googling it.

---

### Post by DM061 on 2012-12-12
I didn't think of that, i will have a google and see what i can find, thanks for the idea.

---

### Post by DM061 on 2012-12-13
Looked around bu, there doesn't seem to be anything about adding courier settings to main.cf
 
...hmm doesn't seem to make sense. Can anyone see if there is something wrong with my earlier posts?
 
Thanks.

---

### Post by DM061 on 2012-12-13
Still nothing...

I have purged postfix and courier and re-configured following tutorials...

And local mail delivers fine, but incoming and outgoing to and from an external source like gmail and hotmail just don't seem to work...

And again, that doesn't matter what port i try it on...

---

