---
title: "fetchmail from gmail"
date: 2012-04-16
forum: Server Platforms
---

### Post by ranggadablues on 2012-04-16
hi guys,

I'm new on mail server, I have local mail server and I want my local mail fetch from gmail and here my [COLOR=Red]/etc/fetchmailrc
[/COLOR]```

set daemon 90
set syslog
set postmaster user

 poll pop.gmail.com with proto POP3 and options no dns
  user 'user@d-bodhi.com' with pass "userpass  is 'rangga' here options keep ssl sslcertck  sslcertpath '/home/ranggadablues/certs/.certs' sslfingerprint 'B8:AF:A7:80:CD:E2:31:50:6F:ED:0E:4F:C8:04:D6:CD'
   smtphost localhost

```and here my log's
```

Apr 16 16:33:38 ranggadablues fetchmail[7504]: 1 message (1 seen) for rangga@d-bodhi.com at pop.gmail.com (2352 octets).
Apr 16 16:35:02 ranggadablues pop3d: Connection, ip=[::ffff:127.0.0.1]
Apr 16 16:35:02 ranggadablues imapd: Connection, ip=[::ffff:127.0.0.1]
Apr 16 16:35:02 ranggadablues pop3d: Disconnected, ip=[::ffff:127.0.0.1]
Apr 16 16:35:02 ranggadablues imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0
Apr 16 16:35:02 ranggadablues postfix/smtpd[8695]: connect from localhost.localdomain[127.0.0.1]
Apr 16 16:35:02 ranggadablues postfix/smtpd[8695]: lost connection after CONNECT from localhost.localdomain[127.0.0.1]
Apr 16 16:35:02 ranggadablues postfix/smtpd[8695]: disconnect from localhost.localdomain[127.0.0.1]
Apr 16 16:35:13 ranggadablues fetchmail[7504]: 1 message (1 seen) for rangga@d-bodhi.com at pop.gmail.com (2352 octets).
Apr 16 16:36:47 ranggadablues fetchmail[7504]: 1 message (1 seen) for rangga@d-bodhi.com at pop.gmail.com (2352 octets).

```I can see 1 message in my log but I can't see any received email on squirellmail for my webmail

please help, thank you

---

### Post by ranggadablues on 2012-04-16
update

I try to move fetchmailrc to /home/ranggadablues/.fetchmailrc and chown, after that restart fetchmail than when I see my log
```

Apr 16 17:00:19 ranggadablues fetchmail[9120]: POP3< +OK send PASS
Apr 16 17:00:19 ranggadablues fetchmail[9120]: POP3> PASS *
Apr 16 17:00:20 ranggadablues fetchmail[9120]: POP3< +OK Welcome.
Apr 16 17:00:20 ranggadablues fetchmail[9120]: POP3> STAT
Apr 16 17:00:20 ranggadablues fetchmail[9120]: POP3< +OK 0 0
Apr 16 17:00:20 ranggadablues fetchmail[9120]: No mail for rangga@d-bodhi.com at pop.gmail.com
Apr 16 17:00:20 ranggadablues fetchmail[9120]: POP3> QUIT
Apr 16 17:00:21 ranggadablues fetchmail[9120]: POP3< +OK Farewell.
Apr 16 17:00:21 ranggadablues fetchmail[9120]: 6.3.19 querying pop.gmail.com (protocol POP3) at Mon 16 Apr 2012 05:00:21 PM WIT: poll completed
Apr 16 17:00:21 ranggadablues fetchmail[9120]: sleeping at Mon 16 Apr 2012 05:00:21 PM WIT for 90 seconds

```
but stil cannot see my email in webmail inbox?

when I try
```

[COLOR=Black]#fetchmail -d0 -v pop.gmail.com[/COLOR]
fetchmail: can't poll specified hosts with another fetchmail running at 9120

```

---

### Post by viperce on 2012-04-16
my /etc/fetchmailrc looks like this

> 
defaults
        proto imap
poll pop.gmail.com
        proto pop3
        user "viperce@gmail.com"
        pass "password"
        is viperce
        keep
        ssl


i battled to get mine going as well but this was my final config that worked for me.

---

### Post by ranggadablues on 2012-04-16
```
defaults
        proto imap
poll pop.gmail.com
        proto pop3
        user "viperce@gmail.com"
        pass "password"
        is viperce
        keep
        ssl 			 		
```

I have change to your config, and result is same so I try this
```
ranggadablues@ranggadablues:~$ fetchmail -d0 -v pop.gmail.com
Enter password for ranggadablues@pop.gmail.com: 
fetchmail: 6.3.19 querying pop.gmail.com (protocol auto) at Tue 17 Apr 2012 08:55:47 AM WIT: poll started
fetchmail: 6.3.19 querying pop.gmail.com (protocol IMAP) at Tue 17 Apr 2012 08:55:47 AM WIT: poll started
Trying to connect to 209.85.225.108/143...connection failed.
fetchmail: connection to pop.gmail.com:imap [209.85.225.108/143] failed: Connection timed out.
Trying to connect to 209.85.225.109/143...fetchmail: timeout after 300 seconds waiting to connect to server pop.gmail.com.
fetchmail: socket error while fetching from ranggadablues@pop.gmail.com
fetchmail: 6.3.19 querying pop.gmail.com (protocol IMAP) at Tue 17 Apr 2012 09:00:47 AM WIT: poll completed
fetchmail: 6.3.19 querying pop.gmail.com (protocol POP3) at Tue 17 Apr 2012 09:00:47 AM WIT: poll started
Trying to connect to 209.85.225.109/110...connection failed.
fetchmail: connection to pop.gmail.com:pop3 [209.85.225.109/110] failed: Connection timed out.
Trying to connect to 209.85.225.108/110...fetchmail: timeout after 300 seconds waiting to connect to server pop.gmail.com.
fetchmail: socket error while fetching from ranggadablues@pop.gmail.com
fetchmail: 6.3.19 querying pop.gmail.com (protocol POP3) at Tue 17 Apr 2012 09:05:47 AM WIT: poll completed
fetchmail: 6.3.19 querying pop.gmail.com (protocol auto) at Tue 17 Apr 2012 09:05:47 AM WIT: poll completed
fetchmail: Query status=2 (SOCKET)
fetchmail: normal termination, status 2

```
what the problem is it? please advice? I already connect to internet
thank you

---

### Post by viperce on 2012-04-17
paste the config the way you have it please.

---

### Post by ranggadablues on 2012-04-17
> **viperce said:**
> paste the config the way you have it please.

what config you asking about?

here my fetchmailrc
```

set postmaster root
set no bouncemail

defaults:
timeout 180
antispam -1
batchlimit 100

poll pop.gmail.com protocol POP3 user "user@gmail.com" there with password "pass" is ranggadablues here

```

postfix main.cf
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

myhostname = ranggadablues.server.com
alias_maps = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
alias_database = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
mydestination = ranggadablues.server.com, localhost, localhost.localdomain
#mydestination = $myhostname, localhost.$mydomain, localhost,$mydomain
relayhost = [smtp.gmail.com]:587
smtpd_tls_CAfile = /etc/postfix/cacert.pem
smtpd_use_tls = yes
mynetworks = 127.0.0.0/8 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
html_directory = /usr/share/doc/postfix/html

virtual_alias_domains = 
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, proxy:mysql:/etc/postfix/mysql-virtual_email2email.cf, hash:/var/lib/mailman/data/virtual-mailman
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /var/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000

# client TLS parameters #
smtp_tls_loglevel=1
smtp_sasl_auth_enable = yes
smtp_tls_security_level = may
#smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_password_maps = hash:/etc/postfix/sasl/passwd
smtp_sasl_security_options = noanonymous

# map username@localhost to usernam@gmail.com #
smtp_generic_maps=hash:/etc/postfix/generic

broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_recipient_access mysql:/etc/postfix/mysql-virtual_recipient.cf, reject_unauth_destination

transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
smtpd_sender_restrictions = check_sender_access mysql:/etc/postfix/mysql-virtual_sender.cf
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual_client.cf
smtpd_client_message_rate_limit = 100
maildrop_destination_concurrency_limit = 1
maildrop_destination_recipient_limit = 1
virtual_transport = maildrop
header_checks = regexp:/etc/postfix/header_checks
mime_header_checks = regexp:/etc/postfix/mime_header_checks
nested_header_checks = regexp:/etc/postfix/nested_header_checks
body_checks = regexp:/etc/postfix/body_checks
owner_request_special = no
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
message_size_limit = 0
```

---

### Post by viperce on 2012-04-17
> virtual_alias_domains = 
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, proxy:mysql:/etc/postfix/mysql-virtual_email2email.cf, hash:/var/lib/mailman/data/virtual-mailman
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /var/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000

are you using virtual mailboxes?

---

### Post by viperce on 2012-04-17
My postfix /etc/postfix/main.cf

> smtpd_banner = mydomain.com ESMTP mydomain.com (Ubuntu)
biff = no
append_dot_mydomain = no
readme_directory = no
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
alias_maps = hash:/etc/aliases
myorigin = mydomain.com
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
fallback_relay = smtp.myisp.net
relayhost = smtp.myisp.net
mydomain = smtp.myisp.net
mynetworks = 127.0.0.0/8 192.168.254.0/24
inet_protocols = all
mailbox = Maildir/
home_mailbox = Maildir/
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = no
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination


Dovecot is default.

---

### Post by ranggadablues on 2012-04-17
> **viperce said:**
> are you using virtual mailboxes?

I don't know, it's from default configuration I have when installed fetchmail. could you explain what it's virtual mailboxes use?
because in this case I want my external mail server from gmail direct to my local mail server

Ok, if I delete all config on my main.cf and change with your main.cf it's affected with my fetchmail config or not, or maybe with another configuration?

_update_
I try you postfix /etc/postfix/main.cf
than I create for Maildir at /home/ranggadablues/Maildir chmod 755 and restart postfix
test send email, and my /var/log/mail.log like this
```

ranggadablues@ranggadablues:~$ tail /var/log/mail.log
Apr 17 16:13:59 ranggadablues imapd: LOGOUT, user=rangga@server.com, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=87, sent=391, time=0
Apr 17 16:14:45 ranggadablues fetchmail[3190]: 1 message for rangga@d-bodhi.com at pop.gmail.com (2355 octets).
Apr 17 16:14:46 ranggadablues postfix/smtpd[12178]: connect from localhost.localdomain[127.0.0.1]
Apr 17 16:14:46 ranggadablues postfix/smtpd[12178]: 97A7944C93: client=localhost.localdomain[127.0.0.1]
Apr 17 16:14:46 ranggadablues postfix/cleanup[12182]: 97A7944C93: message-id=<CA+qxw4RRhz-qWSi2MGwTyDuO7ZGO2drgDBhw87x53p-=4GewaQ@mail.gmail.com>
Apr 17 16:14:46 ranggadablues fetchmail[3190]: reading message rangga@d-bodhi.com@iy-in-f108.1e100.net:1 of 1 (2355 octets) flushed
Apr 17 16:14:46 ranggadablues postfix/qmgr[12069]: 97A7944C93: from=<rangga.hendradita@gmail.com>, size=2770, nrcpt=1 (queue active)
Apr 17 16:14:46 ranggadablues postfix/local[12183]: 97A7944C93: to=<ranggadablues@localhost>, relay=local, delay=0.17, delays=0.12/0.01/0/0.05, dsn=2.0.0, status=sent (delivered to maildir)
Apr 17 16:14:46 ranggadablues postfix/qmgr[12069]: 97A7944C93: removed
Apr 17 16:14:47 ranggadablues postfix/smtpd[12178]: disconnect from localhost.localdomain[127.0.0.1]

```
it is good new or not?because I still not find any received email from external mail to my local mail server

thank you

---

### Post by viperce on 2012-04-17
If you check the /home/ranggadablues/Maildir/new/ are there no mails 
> to=<ranggadablues@localhost>, relay=local, delay=0.17, delays=0.12/0.01/0/0.05, dsn=2.0.0, status=sent **(delivered to maildir)**

---

### Post by geudrik on 2012-04-17
You should check out postfix instead of sendmail.  For gmail configuration options, start here
[https://calomel.org/postfix.html](https://calomel.org/postfix.html)

For fetchmail (at least a good description of what each option is)
[https://calomel.org/fetchmailrc.html](https://calomel.org/fetchmailrc.html)

Cheers man, and apologies for not being much more help with fetchmail :/

---

### Post by ranggadablues on 2012-04-18
> **viperce said:**
> If you check the /home/ranggadablues/Maildir/new/ are there no mails

no I don't see any new mail in /home/ranggadablues/Maildir/new

any suggestion?
thank you

---

### Post by ranggadablues on 2012-04-18
> **geudrik said:**
> You should check out postfix instead of sendmail.  For gmail configuration options, start here
[https://calomel.org/postfix.html](https://calomel.org/postfix.html)

For fetchmail (at least a good description of what each option is)
[https://calomel.org/fetchmailrc.html](https://calomel.org/fetchmailrc.html)

Cheers man, and apologies for not being much more help with fetchmail :/

thank you geudrik I'll try it first and then I will reviews

---

