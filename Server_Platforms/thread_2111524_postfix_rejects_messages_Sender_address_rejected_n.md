---
title: "postfix rejects messages: Sender address rejected: not owned by user"
date: 2013-02-02
forum: Server Platforms
---

### Post by EmilHem on 2013-02-02
So I have a mail-server setup where dovecot is taking care of the imap and postfix is receiving and sending emails.

Postfix is setup to use dovecot's sasl authentication.

OS: Ubuntu 12.04.1 LTS

What works so far:
I can login to dovecot from thunderbird and download messages.
Postfix can receive messages and put them in the correct place.

The exact error message I'm receiving from the log is:
```

Feb  2 11:02:38 [snip servername] postfix/smtpd[8099]: connect from ip-82-46-149-91.dialup.ice.net[91.149.46.82]
Feb  2 11:02:39 [snip servername] postfix/smtpd[8099]: Anonymous TLS connection established from ip-82-46-149-91.dialup.ice.net[91.149.46.82]: TLSv1 with cipher ECDHE-RSA-AES256-SHA (256/256 bits)
Feb  2 11:02:39 [snip servername] postfix/smtpd[8099]: NOQUEUE: reject: RCPT from ip-82-46-149-91.dialup.ice.net[91.149.46.82]: 553 5.7.1 <[snip local email]>: Sender address rejected: not owned by user emil; from=<[snip local email]> to=<[snip external email]> proto=ESMTP helo=<[192.168.1.144]>
Feb  2 11:02:41 [snip servername] postfix/smtpd[8099]: disconnect from ip-82-46-149-91.dialup.ice.net[91.149.46.82]
```
This is my /etc/postfix/main.cf

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
delay_warning_time = 4h
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command =
mailbox_size_limit = 0
mydestination = [snip server domain name], localhost, localhost.localdomain
myhostname = [snip server domain name]
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_cert_file = /etc/ssl/certs/[snip server domain name].crt
smtpd_tls_key_file = /etc/ssl/private/server.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

```This is my /etc/postfix/master.cf

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
#smtp      inet  n       -       -       -       1       postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
submission inet n       -       -       -       -       smtpd
  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_sasl_type=dovecot
  -o smtpd_sasl_path=private/auth
  -o smtpd_sasl_security_options=noanonymous
  -o smtpd_sasl_local_domain=$myhostname
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o smtpd_sender_login_maps=hash:/etc/postfix/virtual
  -o smtpd_sender_restrictions=reject_sender_login_mismatch
  -o smtpd_recipient_restrictions=reject_non_fqdn_recipient,reject_unknown_recipient_domain,permit_sasl_authenticat$
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
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

```

---

### Post by SeijiSensei on 2013-02-02
> ```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128

```

The default mynetworks specification only accepts mail from the localhost interface.  Read [this](http://www.postfix.org/BASIC_CONFIGURATION_README.html#relay_from) for details.

---

### Post by EmilHem on 2013-02-02
So should I just allow all IP's? If so how do I do it?
Like this? *.*.*.*

---

### Post by SeijiSensei on 2013-02-02
Did you read the documentation I linked to?  It's all spelled out there.

---

### Post by EmilHem on 2013-02-02
I did. It still doesn't make sense.

I just want me to be able to send emails from wherever I am in Thunderbird though this server. Even if I add my current IP address it still doesn't work!

---

### Post by SeijiSensei on 2013-02-02
A complete answer to your question is complex.

Let's suppose your server's IP address is 192.168.1.100.  You would need to add "192.168.1.0/24" to the list in mynetworks.  That will permit all addresses in the range 192.168.1.1-254 to connect to your server and should let you send mail from any machine on your local network.

However to send mail from "wherever" is a much more complicated issue.

First, your ISP may not allow you to do this at all since most residential Internet accounts like yours ban running servers in the Terms of Service.  Some ISPs enforce this by blocking inbound access to port 25, the SMTP port, on all their subscribers' machines.  Even if they allow inbound SMTP, you need to set up a "port-forwarding" rule on your router that sits between your local network and the Internet.  Every router has its own software for this, so I recommend visiting portforward.com to see how to do it on yours.  You need to forward external TCP port 25 back to port 25 on your server.  You may also need to add an exemption to the external firewall rules permitting inbound traffic on port 25.  You shouldn't need to change the mynetworks directive in this case, since the inbound traffic will be "masqueraded" to appear to be coming from the router's internal address, which should be in the same subnet as your computer.

Even if you get all this working, you may find that outbound mail cannot be sent.  That's because ISPs often block outbound SMTP traffic as well to keep their customers' computers that have been compromised and turned into spambots from flooding the Internet with spam.  Even if your ISP allows outbound SMTP traffic from your address, you may still find that remote servers will reject your mail since it is coming from a dialup network.  Again this is to protect against spambots. (My servers routinely block any machine like yours with "dialup" in its hostname.)  You might be able to use one of the ISP's server as a "relay" or "smart" host.  You'll need to read the Postfix documentation for that after talking to your ISP's technical support department.

---

