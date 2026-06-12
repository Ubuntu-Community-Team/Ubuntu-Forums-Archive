---
title: "Postfix not receiving emails"
date: 2013-11-30
forum: Server Platforms
---

### Post by zkvvoob on 2013-11-30
Hello guys,

Many months ago I configured a Ubuntu 12.04 server following HowToForge's Perfect Server Guide for Apache, etc. Everything has been working just fine, until... Today I tried to figure out why the PHP contact forms did not send out messages. I tried several different solutions but then I decided just to check and send a message from an outside account and it still hasn't arrived 2 hours later.

So these are my two problems: not receiving emails and not being able to use the PHP Mail function. Could anyone please try to help me?

**/etc/postfix/main.cf**
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


myhostname = mydomain.eu
alias_maps = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
alias_database = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
myorigin = /etc/mailname
mydestination = mydomain.eu, localhost, localhost.localdomain
relayhost = 
mynetworks = 127.0.0.0/8 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains = 
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, proxy:mysql:/etc/postfix/mysql-virtual_email2email.cf, hash:/var/lib/mailman/data/virtual-mailman
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /var/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
inet_protocols = all
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_recipient_access mysql:/etc/postfix/mysql-virtual_recipient.cf, reject_unauth_destination
smtpd_tls_security_level = may
transport_maps = hash:/var/lib/mailman/data/transport-mailman, proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
smtpd_sender_restrictions = check_sender_access mysql:/etc/postfix/mysql-virtual_sender.cf
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual_client.cf
smtpd_client_message_rate_limit = 100
maildrop_destination_concurrency_limit = 1
maildrop_destination_recipient_limit = 1
virtual_transport = dovecot
header_checks = regexp:/etc/postfix/header_checks
mime_header_checks = regexp:/etc/postfix/mime_header_checks
nested_header_checks = regexp:/etc/postfix/nested_header_checks
body_checks = regexp:/etc/postfix/body_checks
owner_request_special = no
dovecot_destination_recipient_limit = 1
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
message_size_limit = 0



```

What else do you need?

EDIT: SOLVED IT! The cause was mydestination = **mydomain.eu**, localhost, localhost.localdomain. When I removed the bold string, everything started working again.

---

### Post by nerdtron on 2013-11-30
What does the /var/log/mail.log says when you are expecting to received an email? Does the email actually arrives on your server but get rejected or it doesn't arrived at all?
Also, can you telnet to you mail server at port 25?
```
telnet mail.mydomain.com 25
```

---

### Post by zkvvoob on 2013-11-30
Here's the mail.log


```
Dec  1 00:20:02 server sm-mta[7723]: NOQUEUE: SYSERR(root): hash map "access": missing map file /etc/mail/access.db: No such file or directoryDec  1 00:20:02 server sm-mta[7723]: ruleset=check_relay, arg1=localhost.localdomain, arg2=127.0.0.1, relay=localhost.localdomain [127.0.0.1], reject=451 4.3.0 Temporary system failure. Please try again later.
Dec  1 00:20:02 server dovecot: pop3-login: Disconnected (no auth attempts in 0 secs): user=<>, rip=127.0.0.1, lip=127.0.0.1, secured, session=<zccYWWzsXAB/AAAB>
Dec  1 00:20:02 server dovecot: imap-login: Disconnected (no auth attempts in 0 secs): user=<>, rip=127.0.0.1, lip=127.0.0.1, secured, session=<K9AYWWzsPAB/AAAB>
Dec  1 00:20:04 server sm-mta[7746]: rAUKe4VE019327: SYSERR(root): hash map "Alias0": missing map file /etc/mail/aliases.db: No such file or directory
Dec  1 00:20:04 server sm-mta[7746]: rAUKe4VF019327: to=<office@mydomain.eu>, delay=01:39:59, xdelay=00:00:00, mailer=esmtp, pri=930000, relay=mydomain.eu. [109.160.111.11], dsn=4.0.0, stat=Deferred: Connection refused by mydomain.eu.
Dec  1 00:20:05 server sm-mta[7746]: rAUJbM6b004589: to=<bz@mydomain.eu.mydomain.eu>, ctladdr=<root@server.mydomain.eu> (0/0), delay=02:42:43, xdelay=00:00:00, mailer=esmtp, pri=1650324, relay=mydomain.eu.mydomain.eu. [111.111.111.111], dsn=4.0.0, stat=Deferred: Connection refused by mydomain.eu.mydomain.eu.
Dec  1 00:20:05 server sm-mta[7746]: rAUIpbVU018792: to=<office@mydomain.eu>, ctladdr=<web3@server.mydomain.eu> (5004/5006), delay=03:28:28, xdelay=00:00:00, mailer=esmtp, pri=2100838, relay=mydomain.eu., dsn=4.0.0, stat=Deferred: Connection refused by mydomain.eu.
Dec  1 00:20:05 server sm-mta[7746]: rAUIodbG018764: to=<office@mydomain.eu>, ctladdr=<web3@server.mydomain.eu> (5004/5006), delay=03:29:26, xdelay=00:00:00, mailer=esmtp, pri=2100844, relay=mydomain.eu., dsn=4.0.0, stat=Deferred: Connection refused by mydomain.eu.
Dec  1 00:20:05 server sm-mta[7746]: rAUIimYa017842: to=<office@mydomain.eu>, ctladdr=<web3@server.mydomain.eu> (5004/5006), delay=03:35:17, xdelay=00:00:00, mailer=esmtp, pri=2190847, relay=mydomain.eu., dsn=4.0.0, stat=Deferred: Connection refused by mydomain.eu.
Dec  1 00:20:05 server sm-mta[7746]: rAUGa9aM014424: to=<bz@mydomain.eu>, ctladdr=<web3@server.mydomain.eu> (5004/5006), delay=05:43:56, xdelay=00:00:00, mailer=esmtp, pri=3360373, relay=mydomain.eu., dsn=4.0.0, stat=Deferred: Connection refused by mydomain.eu.
Dec  1 00:20:05 server sm-mta[7746]: rAUGc8jP014506: to=<info@mydomain.org>, ctladdr=<web9@server.mydomain.eu> (5007/5006), delay=05:41:57, xdelay=00:00:00, mailer=esmtp, pri=3360792, relay=rabotilnicazaizkustvo.org. [111.111.111.111], dsn=4.0.0, stat=Deferred: Connection refused by rabotilnicazaizkustvo.org.
Dec  1 00:20:05 server sm-mta[7746]: rAUGWtR4014204: to=<office@mydomain.eu>, ctladdr=<web3@server.mydomain.eu> (5004/5006), delay=05:47:10, xdelay=00:00:00, mailer=esmtp, pri=3360842, relay=mydomain.eu., dsn=4.0.0, stat=Deferred: Connection refused by mydomain.eu.
Dec  1 00:20:05 server sm-mta[7746]: rAUGVkll014181: to=<office@mydomain.eu>, delay=05:48:19, xdelay=00:00:00, mailer=esmtp, pri=3360910, relay=mydomain.eu., dsn=4.0.0, stat=Deferred: Connection refused by mydomain.eu.
```


office@ is just an alias, not an acutal mailbox, it should forward to my personal account. I don't know why it appears in the log, though, I tried to send a message to my own account (bz@).


I don't seem to be able to connect to mail.mydomain.eu via telnet


```
telnet: Unable to connect to remote host: Connection refused
```


But I think the reason for this is the port. As far as I can remember, the guide that I followed had me set up only secure connections. I can connect to localhost 25, though:


```
Trying 127.0.0.1...Connected to localhost.localdomain.
Escape character is '^]'.
220 server.mydomain.eu ESMTP Sendmail 8.14.4/8.14.4/Debian-2.1ubuntu1; Sun, 1 Dec 2013 00:24:18 +0200; (No UCE/UBE) logging access from: localhost.localdomain(OK)-localhost.localdomain [127.0.0.1]

```

---

