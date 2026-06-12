---
title: "After upgrade from Ubuntu 9.10 to 10.10 postfix defers all mail with timeout"
date: 2010-12-11
forum: Server Platforms
---

### Post by DantePasquale on 2010-12-11
Hi,

I just upgraded my server from 9.10 to 10.10 and everything is working very well except that postfix won't empty the mail queue because it's deferring all e-mail due to "timed out while receiving the initial server greeting). But if I 'telnet localhost 25' I get immediate response from smtp!

It seems to be something to do with** amavis**.

If I comment out the line in /etc/postfix/main.cf for amavis, then mail is delivered. Of course, now I have no spam/virus checking ;( I see a similar post and they upgraded amavis, but when I tried their instructions, the site for the ppa couldn't be found/resolved.

Here's the line in /etc/postfix/main.cf:

```
diff main.cf.orig main.cf
71c71
< content_filter = amavis:[127.0.0.1]:10024
---
> # content_filter = amavis:[127.0.0.1]:10024
```

Amavis is running on that port:

```
tcp        0      0 127.0.0.1:10024         0.0.0.0:*               LISTEN      2115/amavisd (maste
tcp        1      0 127.0.0.1:10024         127.0.0.1:51560         CLOSE_WAIT  -               
tcp        0      0 127.0.0.1:10024         127.0.0.1:55250         ESTABLISHED -               amavis    2115 99.8  0.6 195620 76796 ?        Rs   22:06  22:57 amavisd (master)
postfix   6314  0.0  0.0  50852  2880 ?        S    22:27   0:00 smtp -n amavis -t unix -u -c -o smtp_data_done_timeout=1200 -o smtp_send_xforward_command=yes
postfix   6315  0.0  0.0  50852  2880 ?        S    22:27   0:00 smtp -n amavis -t unix -u -c -o smtp_data_done_timeout=1200 -o smtp_send_xforward_command=yes
root      6361  0.0  0.0   7628   960 pts/1    S+   22:29   0:00 grep amavis


tcp        0      0 127.0.0.1:55251         127.0.0.1:10024         ESTABLISHED 6315/smtp       
tcp        1      0 127.0.0.1:10024         127.0.0.1:58023         CLOSE_WAIT  -               
tcp        1      0 127.0.0.1:10024         127.0.0.1:58022         CLOSE_WAIT  -               
tcp        1      0 127.0.0.1:10024         127.0.0.1:51761         CLOSE_WAIT  -               
tcp        0      0 127.0.0.1:58023         127.0.0.1:10024         FIN_WAIT2   -               
tcp        0      0 127.0.0.1:10024         127.0.0.1:55251         ESTABLISHED -               
tcp        1      0 127.0.0.1:10024         127.0.0.1:45032         CLOSE_WAIT  -               
tcp        1      0 127.0.0.1:10024         127.0.0.1:57909         CLOSE_WAIT  -               
tcp        1      0 127.0.0.1:10024         127.0.0.1:51762         CLOSE_WAIT  -               
tcp        1      0 127.0.0.1:10024         127.0.0.1:49483         CLOSE_WAIT  -               
tcp        1      0 127.0.0.1:10024         127.0.0.1:51559         CLOSE_WAIT  -               
tcp        1      0 127.0.0.1:10024         127.0.0.1:45033         CLOSE_WAIT  -               
tcp        1      0 127.0.0.1:10024         127.0.0.1:49482         CLOSE_WAIT  -               
tcp        0      0 127.0.0.1:55250         127.0.0.1:10024         ESTABLISHED 6314/smtp       
tcp        0      0 127.0.0.1:58022         127.0.0.1:10024         FIN_WAIT2   -               
tcp        1      0 127.0.0.1:10024         127.0.0.1:57908         CLOSE_WAIT  -       
```


Here's the mail log snippet:
```

Dec 11 21:27:34 inferno postfix/smtp[9832]: 036B0F626C: to=<dantepasquale@cocoanet.us>, relay=127.0.0.1[127.0.0.1]:10024, delay=300, delays=0.31/0.01/300/0, dsn=4.4.2, status=deferred (conversation with 127.0.0.1[127.0.0.1] timed out while receiving the initial server greeting)
Dec 11 21:27:46 inferno postfix/qmgr[8763]: 16CC9F6268: from=<notification+yeagrg2r@facebookmail.com>, size=2536, nrcpt=1 (queue active)
Dec 11 21:28:06 inferno postfix/smtpd[9865]: connect from h-74-1-46-166.sfldmidn.static.covad.net[74.1.46.166]
Dec 11 21:28:20 inferno postfix/smtpd[9865]: disconnect from h-74-1-46-166.sfldmidn.static.covad.net[74.1.46.166]
Dec 11 21:32:46 inferno postfix/smtp[9832]: 16CC9F6268: to=<dantepasquale@cocoanet.us>, relay=127.0.0.1[127.0.0.1]:10024, delay=2048, delays=1747/0/300/0, dsn=4.4.2, status=deferred (conversation with 127.0.0.1[127.0.0.1] timed out while receiving the initial server greeting)
```

postqueue -p:
```

68AD4F625E     2486 Sat Dec 11 19:24:12  dantebell@covad.net
(delivery temporarily suspended: conversation with 127.0.0.1[127.0.0.1] timed out while receiving the initial server greeting)
                                         DantePasquale@cocoanet.us

6487CF6266    95669 Sat Dec 11 20:33:10  coair-co.com@coair.com
(delivery temporarily suspended: conversation with 127.0.0.1[127.0.0.1] timed out while receiving the initial server greeting)
                                         DantePasquale@cocoanet.us

705D4F626A    40666 Sat Dec 11 21:04:26  coair-co.com@coair.com
(conversation with 127.0.0.1[127.0.0.1] timed out while receiving the initial server greeting)
                                         DantePasquale@cocoanet.us

04F46F6262     1944 Sat Dec 11 20:20:27  Tammy@kleo.com.ru
(delivery temporarily suspended: conversation with 127.0.0.1[127.0.0.1] timed out while receiving the initial server greeting)
                                         dantepasquale@cocoanet.us

036B0F626C      857 Sat Dec 11 21:22:34  Antonio@mbhognamfoxfdmgopwaoryhdnce.vsm.net
(conversation with 127.0.0.1[127.0.0.1] timed out while receiving the initial server greeting)
                                         dantepasquale@cocoanet.us
```

telnet localhost 25:

```
telnet 127.0.0.1 25
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
220 inferno.cocoanet.us ESMTP Postfix (Ubuntu)
ehlo
501 Syntax: EHLO hostname
ehlo www.cocoanet.us
250-inferno.cocoanet.us
250-PIPELINING
250-SIZE
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
quit
221 2.0.0 Bye
Connection closed by foreign host.
```

/etc/postfix/main.cf:

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

myhostname = inferno.cocoanet.us
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = inferno.cocoanet.us, localhost, localhost.localdomain
relayhost = 
mynetworks = 127.0.0.0/8 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains = 
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /var/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_recipient_access mysql:/etc/postfix/mysql-virtual_recipient.cf, reject_unauth_destination
smtpd_tls_security_level = may
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
virtual_create_maildirsize = yes
virtual_maildir_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
smtpd_sender_restrictions = check_sender_access mysql:/etc/postfix/mysql-virtual_sender.cf
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual_client.cf
maildrop_destination_concurrency_limit = 1
maildrop_destination_recipient_limit = 1
virtual_transport = maildrop
header_checks = regexp:/etc/postfix/header_checks
mime_header_checks = regexp:/etc/postfix/mime_header_checks
nested_header_checks = regexp:/etc/postfix/nested_header_checks
body_checks = regexp:/etc/postfix/body_checks
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
message_size_limit = 0
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
```

---

