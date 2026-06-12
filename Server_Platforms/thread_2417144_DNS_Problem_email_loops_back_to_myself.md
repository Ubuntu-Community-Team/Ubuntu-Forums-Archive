---
title: "DNS Problem email loops back to myself"
date: 2019-04-21
forum: Server Platforms
---

### Post by tomdf on 2019-04-21
Hi Guys,

i have the problem, that an email is not sent to the mail account but to the server itself.
the message in the logfile is the mail loops back to myself. 

rkhunter wants to send this email to warn me about issues. 

here is the log file:

```

[COLOR=#202124][FONT=Roboto]Apr 20 22:17:30 server1 postfix/smtp[18295]: 007E2A81C69: to=<root@server1.cli-net>, relay=127.0.0.1[127.0.0.1]:10024, delay=5.3, delays=3.2/0.01/0.02/2.1, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as AF8F4A81C02)[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Apr 20 22:17:30 server1 postfix/qmgr[24704]: 007E2A81C69: removed[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Apr 20 22:17:30 server1 postfix/smtp[18300]: AF8F4A81C02: to=<root@cl-i.net>, relay=none, delay=0.04, delays=0.02/0.02/0/0, dsn=5.4.6, status=bounced (mail for [/FONT][/COLOR][cl-i.net]("http://cl-i.net/")[COLOR=#202124][FONT=Roboto] loops back to myself)[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Apr 20 22:17:31 server1 postfix/cleanup[18277]: 9469CA81C6A: message-id=<20190420201731.9469CA81C6A@server1.cl-i.net>[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Apr 20 22:17:31 server1 postfix/bounce[18302]: AF8F4A81C02: sender non-delivery notification: 9469CA81C6A[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Apr 20 22:17:31 server1 postfix/qmgr[24704]: 9469CA81C6A: from=<>, size=3189, nrcpt=1 (queue active)[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Apr 20 22:17:31 server1 postfix/qmgr[24704]: AF8F4A81C02: removed[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Apr 20 22:17:31 server1 postfix/local[18304]: 9469CA81C6A: to=<root@server1.cl-i.net>, relay=local, delay=0.02, delays=0.01/0.01/0/0, dsn=2.0.0, status=sent (delivered to mailbox)[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Apr 20 22:17:31 server1 postfix/qmgr[24704]: 9469CA81C6A: removed[/FONT][/COLOR]


```

The server name is : server1.cl-i.net this is the ip: 173.249.25.125
The domain and the mail service is on the ip: [COLOR=#333333][FONT=&amp]68.66.248.21

email receiver is [email]root@cl-i.net[/email] but the domain does not arrive. 

Why does the server loops back the email and
how can i send the email from that server to the mail system on 68.66.......

thanks for your kind help [/FONT][/COLOR]

---

### Post by SeijiSensei on 2019-04-21
You probably don't have cl-i.net in the list for "mydestination" in Postfix.  The "loops back to itself" error occurs when the email server cannot identify the destination for mail for that domain.

---

### Post by tomdf on 2019-04-21
thanks for your fast answer.
if i understand right, "mydestination" is used for deliver an email locally instead of sending to another server.
But this is not want i want. the server is server1.cl-i.net but the email is on another server with another ip so i would like to send the email to the other server and not locally.
Do you have any idea how i can do that?

sorry if i did not explain well before ;)
thanks for helping me again


Can it be that because the domain cl-i.net is in mydestination, that all emails to cl-i.net will be delivered to this server and not to the mail server on the other ip?

```

myhostname = server1.cl-i.net
alias_maps = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
alias_database = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
myorigin = /etc/mailname
mydestination = server1.cl-i.net, localhost, localhost.localdomain



```

---

### Post by SeijiSensei on 2019-04-23
For that, you indeed do not want ci-i.net in mydestination.  You need to use the "relayhost" parameter instead.

```

relayhost = [host.to.send.to]

```

The brackets matter. From [http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html)

> 
relayhost (default: empty)

    The next-hop destination of non-local mail; overrides non-local domains in recipient addresses. This information is overruled with relay_transport, sender_dependent_default_transport_maps, default_transport, sender_dependent_relayhost_maps and with the transport(5) table.

    On an intranet, specify the organizational domain name. If your internal DNS uses no MX records, specify the name of the intranet gateway host instead.

    In the case of SMTP, specify a domain name, hostname, hostname:port, [hostname]:port, [hostaddress] or [hostaddress]:port. The form [hostname] turns off MX lookups.

    If you're connected via UUCP, see the UUCP_README file for useful information.

    Examples:

    relayhost = $mydomain
    relayhost = [gateway.example.com]
    relayhost = uucphost
    relayhost = [an.ip.add.ress]


---

### Post by tomdf on 2019-05-14
Hello,

thanks a lot for your answer.
I use this link for configure relayhost
[https://www.linode.com/docs/email/postfix/configure-postfix-to-send-mail-using-gmail-and-google-apps-on-debian-or-ubuntu/](https://www.linode.com/docs/email/postfix/configure-postfix-to-send-mail-using-gmail-and-google-apps-on-debian-or-ubuntu/)

first i configure sasl_passwd:
```

[mail.cl-i.net]:587 root@cl-i.net:password



```

then i change the /etc/postfix/main.cf like that: 
```

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = server1.cl-i.net
alias_maps = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
alias_database = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
myorigin = /etc/mailname
mydestination = server1.cl-i.net, localhost, localhost.localdomain
relayhost = [mail.cl-i.net]:587 
mynetworks = 127.0.0.0/8 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains = 
virtual_alias_maps = hash:/var/lib/mailman/data/virtual-mailman, proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, proxy:mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /var/vmail
virtual_uid_maps = mysql:/etc/postfix/mysql-virtual_uids.cf
virtual_gid_maps = mysql:/etc/postfix/mysql-virtual_gids.cf
sender_bcc_maps = proxy:mysql:/etc/postfix/mysql-virtual_outgoing_bcc.cf
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_restriction_classes = greylisting
greylisting = check_policy_service inet:127.0.0.1:10023
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, reject_rbl_client zen.spamhaus.org, check_recipient_access mysql:/etc/postfix/mysql-virtual_recipient.cf, check_recipient_access mysql:/etc/postfix/mysql-virtual_policy_greylist.cf
smtpd_tls_security_level = may
transport_maps = hash:/var/lib/mailman/data/transport-mailman, proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
smtpd_sender_login_maps = proxy:mysql:/etc/postfix/mysql-virtual_sender_login_maps.cf
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $sender_bcc_maps $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $smtpd_sender_login_maps
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_sasl_authenticated, permit_mynetworks, check_helo_access regexp:/etc/postfix/helo_access, reject_invalid_hostname, reject_non_fqdn_hostname, reject_invalid_helo_hostname, reject_unknown_helo_hostname, check_helo_access regexp:/etc/postfix/blacklist_helo
smtpd_sender_restrictions = check_sender_access regexp:/etc/postfix/tag_as_originating.re , permit_mynetworks, permit_sasl_authenticated, check_sender_access mysql:/etc/postfix/mysql-virtual_sender.cf, check_sender_access regexp:/etc/postfix/tag_as_foreign.re
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
smtp_tls_security_level = may
smtpd_tls_mandatory_protocols = !SSLv2, !SSLv3
smtpd_tls_protocols = !SSLv2,!SSLv3
smtp_tls_protocols = !SSLv2,!SSLv3
smtpd_tls_exclude_ciphers = RC4, aNULL
smtp_tls_exclude_ciphers = RC4, aNULL
dovecot_destination_recipient_limit = 1
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings






```

i can find enable sasl 
but password-maps i dont find in main.cf
```

[COLOR=#228B22]# Enable SASL authentication[/COLOR]
[COLOR=#00688B]smtp_sasl_auth_enable[/COLOR] = yes
[COLOR=#228B22]# Disallow methods that allow anonymous authentication[/COLOR]
[COLOR=#00688B]smtp_sasl_security_options[/COLOR] = noanonymous
[COLOR=#228B22]# Location of sasl_passwd[/COLOR]
[COLOR=#00688B]smtp_sasl_password_maps[/COLOR] = hash:/etc/postfix/sasl/sasl_passwd
[COLOR=#228B22]# Enable STARTTLS encryption[/COLOR]
[COLOR=#00688B]smtp_tls_security_level[/COLOR] = encrypt
[COLOR=#228B22]# Location of CA certificates[/COLOR]
[COLOR=#00688B]smtp_tls_CAfile[/COLOR] = /etc/ssl/certs/ca-certificates.crt
```
when i send an email with:

```

sendmail root@cl-i.net
From: root@cl-i.net
Subject: Test mail
This is a test email
```

i see in the syslog :
```

May 14 21:57:45 server1 postfix/qmgr[2350]: 2692DA8254F: removed
May 14 21:57:45 server1 postfix/smtp[5866]: 5F881A824EC: to=<root@cl-i.net>, relay=mail.cl-i.net[68.66.248.21]:587, delay=0.4, delays=0.01/0.01/0.31/0.06, dsn=5.0.0, status=bounced (host mail.cl-i.net[68.66.248.21] said: 550 SMTP AUTH is required for message submission on port 587 (in reply to RCPT TO command))
May 14 21:57:45 server1 postfix/cleanup[5855]: BFFEFA82554: message-id=<20190514195745.BFFEFA82554@server1.cl-i.net>
May 14 21:57:45 server1 postfix/bounce[5867]: 5F881A824EC: sender non-delivery notification: BFFEFA82554
May 14 21:57:45 server1 postfix/qmgr[2350]: BFFEFA82554: from=<>, size=2763, nrcpt=1 (queue active)
May 14 21:57:45 server1 postfix/qmgr[2350]: 5F881A824EC: removed
May 14 21:57:45 server1 postfix/local[5868]: BFFEFA82554: to=<root@server1.cl-i.net>, relay=local, delay=0.02, delays=0.01/0.01/0/0, dsn=2.0.0, status=sent (delivered to mailbox)
May 14 21:57:45 server1 postfix/qmgr[2350]: BFFEFA82554: removed



```

but the email does not arrive.

Do you have any idea what is going wrong?

thanks in advance

---

### Post by SeijiSensei on 2019-05-15
Well, the log says it bounced. Can you see the logs on mail.cl-i.net[68.66.248.21]? They should tell you something about why the message bounced.

I've never used SASL. I just accept that email has the same level of security as postcards and use the clear-text ports like 25.

---

