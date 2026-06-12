---
title: "Postfix: mail transport unavailable"
date: 2011-05-31
forum: Server Platforms
---

### Post by Wader_WS on 2011-05-31
Hi there,

I've just moved to a new dedi using ubuntu 10.04.2 following linodes setup guide for ISPConfig. [http://library.linode.com/web-applications/control-panels/ispconfig/ubuntu-10.04-lucid](http://library.linode.com/web-applications/control-panels/ispconfig/ubuntu-10.04-lucid)

Everything seems to be working as intended other than my mail server. Firstly i had issues with ClamAV to which i disabled, however now i seem to be receiving the error "mail transport unavaliable". I have about 80 emails waiting in the mailqueue.

Here is the output from "postconf -n"

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
body_checks = regexp:/etc/postfix/body_checks
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
header_checks = regexp:/etc/postfix/header_checks
html_directory = /usr/share/doc/postfix/html
inet_interfaces = all
mailbox_size_limit = 0
mime_header_checks = regexp:/etc/postfix/mime_header_checks
mydestination = iwader.co.uk, localhost, localhost.localdomain
myhostname = iwader.co.uk
mynetworks = 127.0.0.0/8 [::1]/128
myorigin = /etc/mailname
nested_header_checks = regexp:/etc/postfix/nested_header_checks
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virt                                                                                                 ual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipien                                                                                                 t_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonica                                                                                                 l_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
readme_directory = /usr/share/doc/postfix
recipient_delimiter = +
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual                                                                                                 _client.cf
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, che                                                                                                 ck_recipient_access mysql:/etc/postfix/mysql-virtual_recipient.cf, reject_unauth                                                                                                 _destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sender_restrictions = check_sender_access mysql:/etc/postfix/mysql-virtual                                                                                                 _sender.cf
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysq                                                                                                 l:/etc/postfix/mysql-virtual_email2email.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/vmail
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_transport = maildrop
virtual_uid_maps = static:5000

```

As far as i know all my dns is exactly the same as before (updated to the new ip ofcourse)

---

### Post by tapi0n on 2011-06-01
I had a similar problem some time ago.

Did you make sure the permissions on your mailboxes are ok?

What is the output of your logs?

---

### Post by Wader_WS on 2011-06-01
Well i've not touched the permissions since i installed it, so im guessing they should be right, i'll double check them though.

Here is my mail log

```
Jun 1 06:52:57 velocity postfix/qmgr[6674]: E0BFC24E46: from=,e size=3143, nrcpt=1 (queue active)
Jun 1 06:52:57 velocity postfix/qmgr[6674]: warning: connect to transport private/amavis: Connection refused
Jun 1 06:52:57 velocity postfix/error[21429]: E0BFC24E46: to=, relay=none, delay=46681, delays=46681/0.01/0/0.01, dsn=4.3.0, status=deferred (mail transport unavailable)
Jun 1 06:55:02 velocity pop3d: Connection, ip=[::ffff:127.0.0.1]
Jun 1 06:55:02 velocity pop3d: Disconnected, ip=[::ffff:127.0.0.1]
Jun 1 06:55:02 velocity imapd: Connection, ip=[::ffff:127.0.0.1]
Jun 1 06:55:02 velocity imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0
Jun 1 06:55:02 velocity postfix/smtpd[21500]: connect from localhost.localdomain[127.0.0.1]
Jun 1 06:55:02 velocity postfix/smtpd[21500]: lost connection after CONNECT from localhost.localdomain[127.0.0.1]
Jun 1 06:55:02 velocity postfix/smtpd[21500]: disconnect from localhost.localdomain[127.0.0.1]
Jun 1 06:57:57 velocity postfix/qmgr[6674]: AD5B424E4A: from=, size=3334, nrcpt=1 (queue active)
Jun 1 06:57:57 velocity postfix/qmgr[6674]: warning: connect to transport private/amavis: Connection refused
Jun 1 06:57:57 velocity postfix/error[21542]: AD5B424E4A: to=, relay=none, delay=42451, delays=42451/0.01/0/0.01, dsn=4.3.0, status=deferred (mail transport unavailable)
Jun 1 07:00:01 velocity pop3d: Connection, ip=[::ffff:127.0.0.1]
Jun 1 07:00:01 velocity pop3d: Disconnected, ip=[::ffff:127.0.0.1]
Jun 1 07:00:01 velocity imapd: Connection, ip=[::ffff:127.0.0.1]
Jun 1 07:00:01 velocity imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0
Jun 1 07:00:01 velocity postfix/smtpd[21610]: connect from localhost.localdomain[127.0.0.1]
Jun 1 07:00:01 velocity postfix/smtpd[21610]: lost connection after CONNECT from localhost.localdomain[127.0.0.1]
Jun 1 07:00:01 velocity postfix/smtpd[21610]: disconnect from localhost.localdomain[127.0.0.1]
Jun 1 07:05:02 velocity pop3d: Connection, ip=[::ffff:127.0.0.1]
Jun 1 07:05:02 velocity pop3d: Disconnected, ip=[::ffff:127.0.0.1]
Jun 1 07:05:02 velocity imapd: Connection, ip=[::ffff:127.0.0.1]
Jun 1 07:05:02 velocity imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0
Jun 1 07:05:02 velocity postfix/smtpd[21734]: connect from localhost.localdomain[127.0.0.1]
Jun 1 07:05:02 velocity postfix/smtpd[21734]: lost connection after CONNECT from localhost.localdomain[127.0.0.1]
Jun 1 07:05:02 velocity postfix/smtpd[21734]: disconnect from localhost.localdomain[127.0.0.1]
Jun 1 07:10:01 velocity pop3d: Connection, ip=[::ffff:127.0.0.1]
Jun 1 07:10:01 velocity pop3d: Disconnected, ip=[::ffff:127.0.0.1]
Jun 1 07:10:01 velocity imapd: Connection, ip=[::ffff:127.0.0.1]
Jun 1 07:10:01 velocity imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0
```

This is my error log. The same line is being spammed into the logs.

```
Jun 1 07:12:57 velocity postfix/qmgr[6674]: warning: connect to transport private/amavis: Connection refused
```

---

### Post by lisati on 2011-06-01
No, that log entry isn't spam. It's a warning that amavis isn't accepting email for processing for some reason.

Things to try include restarting amavis:
```
sudo service amavis restart
```

---

### Post by Wader_WS on 2011-06-01
I have disabled the use of amavis and ClamAV using this guide, [http://www.faqforge.com/linux/controlpanels/ispconfig3/how-to-disable-spamfilter-and-antivirus-functions-in-ispconfig-3/](http://www.faqforge.com/linux/controlpanels/ispconfig3/how-to-disable-spamfilter-and-antivirus-functions-in-ispconfig-3/)

I disabled it because it was causing problems with mail filtering.

---

