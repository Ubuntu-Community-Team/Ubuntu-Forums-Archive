---
title: "postfix/dovecot does not deliver (external) mails to accounts"
date: 2009-04-12
forum: Server Platforms
---

### Post by randomstuff on 2009-04-12
I have a postfix/dovecot setup on 8.10 running.

- Sending mails over SMTP to external/internal accounts works. 
- Fetching mails over IMAP works

However, when I send an email from my old server (or yahoo/gmail) to my new mail server, the mails do not get delivered to the respective accounts (I have two accounts, one for each domain).

After fixing some problems with the virtual domains, I don't even get any entries in /var/log/mail.log when receiving emails for h1111111.stratoserver.net (the actual hostname), and not for the domain either. I send a mail from my yahoo account, addressed to an account on one of the domains, as well as the hostname itself (somename@h1111111.stratoserver.net). But the mail.log file does not show anything for this email.

EDIT: after a while I get the following in my mail.log:
> Apr 12 14:17:23 h1434680 postfix/qmgr[7496]: 1FD0C60CEC9: from=<double-bounce@h1111111.stratoserver.net>, size=1387, nrcpt=1 (queue active)
Apr 12 14:17:23 h1111111 deliver(nobody): stat(/root/Maildir/cur) failed: Permission denied
Apr 12 14:17:23 h1111111 deliver(nobody): stat(/root/Maildir/cur) failed: Permission denied
Apr 12 14:17:23 h1111111 deliver(nobody): msgid=<20090411155838.1FD0C60CEC9@h1111111.stratoserver.net>: Couldn't open mailbox INBOX: Internal error occurred. Refer to server log for more information. [2009-04-12 14:17:23]
Apr 12 14:17:23 h1434680 postfix/local[7586]: 1FD0C60CEC9: to=<root@h1111111.stratoserver.net>, orig_to=<postmaster>, relay=local, delay=73126, delays=73126/0.02/0/0.04, dsn=4.3.0, status=deferred (temporary failure)

Can somebody tell me what is wrong?

**master.cf**

> #
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
#smtp      inet  n       -       -       -       -       smtpd
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
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
smtp      unix  -       -       -       -       -       smtp -v
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
dovecot   unix  -       n       n       -       -       pipe
  flags=DRhu user=mail:mail argv=/usr/lib/dovecot/deliver -f ${sender} -d ${user}@${nexthop}

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


**main.cf**

> # See /usr/share/postfix/main.cf.dist for a commented, more complete version


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
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = h1111111.stratoserver.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = h1111111.stratoserver.net, mail.h1111111.stratoserver.net, localhost.stratoserver.net, localhost
relayhost = 
mynetworks = 127.0.0.0/8, 88.188.188.22
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth-client
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 4
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

#virtual_mailbox_domains = mydomain.net, anotherdomain.de
#virtual_mailbox_base = /home/
#virtual_mailbox_maps = hash:/etc/postfix/vmailbox
#virtual_minimum_uid = 100
#virtual_uid_maps = static:5000
#virtual_gid_maps = static:5000
virtual_alias_domains = mydomain.net, anotherdomain.de
virtual_alias_maps = hash:/etc/postfix/virtual
mailbox_command = /usr/lib/dovecot/deliver
dovecot_destination_recipient_limit = 1
virtual_transport = dovecot 



**/etc/postfix/virtual**

> @mydomain.net account1
@anotherdomain.de account2

---

### Post by dannyboy1121 on 2009-04-12
Well .. the mail.log is showing an attempted delivery to root which I think postfix won't allow (you will need to set up an alias if you've not done so already).

I don't think it fixes your issue but it could be a starting point.

---

### Post by randomstuff on 2009-04-13
Thank you, I figured as much already, but I thought that it was only a symptom of the underlying issue.

But just to at least fix this particular part of the problem, how/where would I set up such an alias? I don't think it should go in the /etc/postfix/virtual, but where would it go?

Thanks in advance.

---

### Post by wsonar on 2009-04-15
I'm new and trying to figure this out also 
but I think aliases go in here

/etc/aliases

---

