---
title: "Cannot send mail with Postfix"
date: 2013-12-01
forum: Server Platforms
---

### Post by forsakenrider on 2013-12-01
So I built a mail server on my ubuntu 12.04 server following this guide:
[http://www.pixelinx.com/2013/09/creating-a-mail-server-on-ubuntu-postfix-courier-ssltls-spamassassin-clamav-amavis/](http://www.pixelinx.com/2013/09/creating-a-mail-server-on-ubuntu-postfix-courier-ssltls-spamassassin-clamav-amavis/)

My ISP blocks port 25 so I am using a mail forward service from [dynu here]("http://www.dynu.com/default.aspx?page=email&type=Email%20Store/Forward") It is setup to use 2525.

I can receive mail but I am unable to send out mail. Here is the errors from mail.log

```
Dec  1 16:25:31 dwhackserv postfix/cleanup[17809]: 4C37B6E02B0: message-id=<60143bdef19aaa656c21bd9ee2c586c1@waterlowphotography.com>
Dec  1 16:25:31 dwhackserv postfix/qmgr[17744]: 4C37B6E02B0: from=<admin@waterlowphotography.com>, size=1351, nrcpt=1 (queue active)
Dec  1 16:25:31 dwhackserv amavis[4520]: (04520-01) FWD via SMTP: <admin@waterlowphotography.com> -> <forsakenrider@hotmail.com>,BODY=7BIT 250 2.0.0 from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 4C37B6E02B0
Dec  1 16:25:31 dwhackserv amavis[4520]: (04520-01) Passed CLEAN, LOCAL [127.0.0.1] [127.0.0.1] <admin@waterlowphotography.com> -> <forsakenrider@hotmail.com>, Message-ID: <60143bdef19aaa656c21bd9ee2c586c1@waterlowphotography.com>, mail_id: nZvKu8N8kDoQ, Hits: -1, size: 844, queued_as: 4C37B6E02B0, 2935 ms
Dec  1 16:25:31 dwhackserv postfix/smtp[17810]: 48EAB6E01CE: to=<forsakenrider@hotmail.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=3.2, delays=0.15/0.05/0.82/2.2, dsn=2.0.0, status=sent (250 2.0.0 from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 4C37B6E02B0)
Dec  1 16:25:31 dwhackserv postfix/qmgr[17744]: 48EAB6E01CE: removed
Dec  1 16:25:31 dwhackserv amavis[4581]: Net::Server: Accept failed with 28 tries left: Invalid argument
Dec  1 16:25:32 dwhackserv postfix/smtpd[17839]: connect from MTRLPQ4362W-LP130-03-1177918378.dsl.bell.ca[some.ip.i.removed]
Dec  1 16:25:32 dwhackserv postfix/smtpd[17839]: NOQUEUE: reject: RCPT from MTRLPQ4362W-LP130-03-1177918378.dsl.bell.ca[some.ip.i.removed]: 554 5.7.1 <forsakenrider@hotmail.com>: Relay access denied; from=<admin@waterlowphotography.com> to=<forsakenrider@hotmail.com> proto=ESMTP helo=<mail.waterlowphotography.com>
Dec  1 16:25:32 dwhackserv postfix/smtp[17838]: 4C37B6E02B0: to=<forsakenrider@hotmail.com>, relay=mail.waterlowphotography.com[some.ip.i.removed]:2525, delay=1.1, delays=0.08/0.03/0.93/0.1, dsn=5.7.1, status=bounced (host mail.waterlowphotography.comsome.ip.i.removed] said: 554 5.7.1 <forsakenrider@hotmail.com>: Relay access denied (in reply to RCPT TO command))
Dec  1 16:25:32 dwhackserv postfix/smtpd[17839]: disconnect from MTRLPQ4362W-LP130-03-1177918378.dsl.bell.ca[some.ip.i.removed]
Dec  1 16:25:32 dwhackserv postfix/cleanup[17809]: 6B52D6E02B1: message-id=<20131201212532.6B52D6E02B1@mail.waterlowphotography.com>
Dec  1 16:25:32 dwhackserv postfix/bounce[17841]: 4C37B6E02B0: sender non-delivery notification: 6B52D6E02B1
Dec  1 16:25:32 dwhackserv postfix/qmgr[17744]: 6B52D6E02B1: from=<>, size=3579, nrcpt=1 (queue active)
Dec  1 16:25:32 dwhackserv postfix/qmgr[17744]: 4C37B6E02B0: removed
Dec  1 16:25:32 dwhackserv amavis[4581]: Net::Server: Accept failed with 27 tries left: Invalid argument
Dec  1 16:25:32 dwhackserv postfix/virtual[17842]: 6B52D6E02B1: to=<admin@waterlowphotography.com>, relay=virtual, delay=0.18, delays=0.05/0.03/0/0.1, dsn=2.0.0, status=sent (delivered to maildir)
Dec  1 16:25:32 dwhackserv postfix/qmgr[17744]: 6B52D6E02B1: removed
```

Here is my postfix main:
```
myorigin = /etc/mailname
smtpd_banner = $myhostname ESMTP $mail_name
biff = no
append_dot_mydomain = no
readme_directory = no
mydestination =
relayhost = waterlowphotography.com:2525
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mynetworks_style = host
mailbox_size_limit = 0
virtual_mailbox_limit = 0
recipient_delimiter = +
inet_interfaces = all
message_size_limit = 0
myhostname = mail.waterlowphotography.com


# SMTP Authentication (SASL)

smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =

# Encrypted transfer (SSL/TLS)

smtp_use_tls = yes
smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/ssl/private/mail.waterlowphotography.com.crt
smtpd_tls_key_file = /etc/ssl/private/mail.waterlowphotography.com.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# Basic SPAM prevention

smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes
#smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination

# Force incoming mail to go through Amavis

content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings

# Virtual user mappings

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/maps/user.cf
virtual_uid_maps = static:5000
virtual_gid_maps =  static:5000
virtual_alias_maps = mysql:/etc/postfix/maps/alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/maps/domain.cf
#smtpd_relay_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination

smtpd_relay_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination


```

And my postfix Master:

```
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
2525     inet  n       -       -       -       -       smtpd
smtps     inet  n       -       -       -       -       smtpd
   -o smtpd_tls_wrappermode=yes
submission inet n       -       -       -       -       smtpd
# -o smtpd_sasl_auth_enable=yes
# -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject
# -o smtpd_sasl_security_options=noanonymous,noplaintext
# -o smtpd_sasl_tls_security_options=noanonymous

pickup    fifo  n       -       -       60      1       pickup
  -o content_filter=
  -o receive_override_options=no_header_body_checks
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
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
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
amavis    unix -        -       -       -       2       smtp
  -o smtp_data_done_timeout=1200
  -o smtp_send_xforward_command=yes
  -o disable_dns_lookups=yes
  -o max_use=20
127.0.0.1:10025 inet n  -       -       -       -       smtpd
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


Any Ideas what Is wrong?
Could it be something to do with TLS?

---

### Post by kustomjs on 2013-12-02
you have to setup relaying to do this.

---

### Post by forsakenrider on 2013-12-04
Isnt that what My dyno mail forward service does? Incoming mail goes through them, but I cant seems to get outgoing mail to work.

---

### Post by kustomjs on 2013-12-04
No you have to set the relaying information inside of your postfix/main.cf   

like this:

myhostname = mail.domain.com
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
myorigin = mail.domain.com
mydestination = $myhostname, localhost, localhost.localdomain, localhost.$myhostname
relayhost = 192.168.60.20:587   <------ this is where you want to put the other host name at.
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0

Also if you have firewall your going need to open port 2525

or change out 2525 to 587 that would solve all your problems.

---

### Post by forsakenrider on 2013-12-04
I believe thats what I have it setup as in my main. I have attached the setting on the  dynu e-mail port forward page as well. It seems as if my outbound mail does not go through them. inbound mail clearly comes from their server.

---

### Post by kustomjs on 2013-12-04
does ur isp block port 587?

---

### Post by forsakenrider on 2013-12-04
I dont think so. just 21 and 25 I think. I will have to try that when I get home. should I change the port to 587 in my dynu.com configuration aswell?

---

### Post by kustomjs on 2013-12-04
no just on your mail server and forget about using dynu.com after the change

---

### Post by forsakenrider on 2013-12-04
Also, dont mail servers listen on port 25? So if I send it out on port 587 then how will that work? 

I guess I have a lot to learn!

---

### Post by kustomjs on 2013-12-04
well mail servers can listen on any port but the default ports are 25 and 587 all port 587 is an submission/secure port.

---

