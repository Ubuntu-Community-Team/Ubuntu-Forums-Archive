---
title: "Postfix-Courier Mail Server"
date: 2007-02-17
forum: Server Platforms
---

### Post by ClayPTino on 2007-02-17
Hi,

I've been trying to set up a mail server using these tutorials I have found on the boards:

[http://www.urbanpuddle.com/articles/2006/10/12/setup-postfix-in-about-1-hour](http://www.urbanpuddle.com/articles/2006/10/12/setup-postfix-in-about-1-hour)

[http://www.howtoforge.com/virtual_postfix_mysql_quota_courier](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier)

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

I have been able to send emails using the SMTP server; however, I can't log into the POP server or the IMAP server using SquirrelMail.  I know I need to send an email to the account in order to populate the Mailder folders, however, whenever I send a message to the server from a separate account, I get the following bounce back email:

```

This is the Postfix program at host clayscape.com.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to <postmaster>

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

			The Postfix program

<tino@hamail.clayscape.com> (expanded from <tino@clayscape.com>): Host or
    domain name not found. Name service error for name=hamail.clayscape.com
    type=A: Host not found

```

For some reason, the host name is being appended to hamail, and I don't know why.

Here is the output of postconf -n:

```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
inet_interfaces = all
mailbox_size_limit = 0
mydestination = mydomain.com, localhost, localhost.localdomain
myhostname = mydomain.com
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
receive_override_options = no_address_mappings
recipient_delimiter = +
relayhost = 
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_alias_domains = 
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_uid_maps = static:5000

```

I have also included the output for a few of the log files.

mail.err:

```

Feb 14 17:34:38 hal imaplogin: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Feb 14 17:35:25 hal imaplogin: DISCONNECTED, user=tino@clayscape.com, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Feb 14 17:48:56 hal imaplogin: DISCONNECTED, user=tino@clayscape.com, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Feb 14 17:53:35 hal imaplogin: DISCONNECTED, user=tino@clayscape.com, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Feb 14 17:54:38 hal imaplogin: DISCONNECTED, user=tino@clayscape.com, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Feb 14 17:58:04 hal imaplogin: DISCONNECTED, user=tino@clayscape.com, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Feb 14 18:08:09 hal imaplogin: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Feb 14 18:08:09 hal imaplogin: DISCONNECTED, ip=[::ffff:127.0.0.1], time=5
Feb 15 01:14:45 hal imaplogin: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Feb 15 18:41:35 hal imaplogin: DISCONNECTED, ip=[::ffff:192.168.1.1], time=8
Feb 15 18:41:48 hal imaplogin: DISCONNECTED, ip=[::ffff:192.168.1.1], time=6
Feb 15 18:42:01 hal imaplogin: DISCONNECTED, ip=[::ffff:192.168.1.1], time=7
Feb 15 19:02:40 hal courierpop3login: LOGIN FAILED, ip=[::ffff:192.168.1.1]
Feb 15 19:02:56 hal courierpop3login: LOGIN FAILED, ip=[::ffff:192.168.1.1]
Feb 16 17:21:47 hal courierpop3login: LOGIN FAILED, ip=[::ffff:59.1.193.2]
Feb 16 17:22:22 hal last message repeated 18 times
Feb 16 17:23:26 hal last message repeated 40 times
Feb 16 17:24:30 hal last message repeated 44 times
Feb 16 17:25:34 hal last message repeated 44 times
Feb 16 17:26:37 hal last message repeated 44 times
Feb 16 17:27:42 hal last message repeated 44 times
Feb 16 17:28:41 hal last message repeated 43 times
Feb 16 17:29:45 hal last message repeated 43 times

```

mail.info:

```

Feb 14 16:39:32 hal authdaemond.mysql: modules="authpam", daemons=5
Feb 14 16:39:32 hal authdaemond.mysql: restarting authdaemond children
Feb 14 16:39:32 hal authdaemond.mysql: modules="authpam", daemons=5
Feb 14 17:16:21 hal postfix/master[8333]: terminating on signal 15
Feb 14 17:16:21 hal postfix/master[9541]: daemon started -- version 2.2.10, configuration /etc/postfix
Feb 14 17:28:54 hal authdaemond.mysql: restarting authdaemond children
Feb 14 17:28:54 hal authdaemond.mysql: modules="authmysql", daemons=5
Feb 14 17:28:54 hal authdaemond.mysql: modules="authmysql", daemons=5
Feb 14 17:30:04 hal postgrey[9968]: Process Backgrounded
Feb 14 17:30:04 hal postgrey[9968]: 2007/02/14-17:30:04 postgrey (type Net::Server::Multiplex) starting! pid(9968)
Feb 14 17:30:04 hal postgrey[9968]: Binding to TCP port 60000 on host 127.0.0.1
Feb 14 17:30:04 hal postgrey[9968]: Setting gid to "113 113"
Feb 14 17:30:04 hal postgrey[9968]: Setting uid to "113"
Feb 14 17:31:08 hal postgrey[9968]: 2007/02/14-17:31:08 Server closing!
Feb 14 17:31:09 hal postgrey[9975]: Process Backgrounded
Feb 14 17:31:09 hal postgrey[9975]: 2007/02/14-17:31:09 postgrey (type Net::Server::Multiplex) starting! pid(9975)
Feb 14 17:31:09 hal postgrey[9975]: Binding to TCP port 60000 on host 127.0.0.1
Feb 14 17:31:09 hal postgrey[9975]: Setting gid to "113 113"
Feb 14 17:31:09 hal postgrey[9975]: Setting uid to "113"
Feb 14 17:34:25 hal imaplogin: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Feb 14 17:34:25 hal imaplogin: LOGOUT, ip=[::ffff:127.0.0.1]
Feb 14 17:34:38 hal imaplogin: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Feb 14 17:34:38 hal imaplogin: LOGOUT, ip=[::ffff:127.0.0.1]

```

mail.log:

```

Feb 14 16:39:32 hal authdaemond.mysql: modules="authpam", daemons=5
Feb 14 16:39:32 hal authdaemond.mysql: restarting authdaemond children
Feb 14 16:39:32 hal authdaemond.mysql: modules="authpam", daemons=5
Feb 14 17:16:21 hal postfix/master[8333]: terminating on signal 15
Feb 14 17:16:21 hal postfix/master[9541]: daemon started -- version 2.2.10, configuration /etc/postfix
Feb 14 17:28:54 hal authdaemond.mysql: restarting authdaemond children
Feb 14 17:28:54 hal authdaemond.mysql: modules="authmysql", daemons=5
Feb 14 17:28:54 hal authdaemond.mysql: modules="authmysql", daemons=5
Feb 14 17:30:04 hal postgrey[9968]: Process Backgrounded
Feb 14 17:30:04 hal postgrey[9968]: 2007/02/14-17:30:04 postgrey (type Net::Server::Multiplex) starting! pid(9968)
Feb 14 17:30:04 hal postgrey[9968]: Binding to TCP port 60000 on host 127.0.0.1
Feb 14 17:30:04 hal postgrey[9968]: Setting gid to "113 113"
Feb 14 17:30:04 hal postgrey[9968]: Setting uid to "113"
Feb 14 17:31:08 hal postgrey[9968]: 2007/02/14-17:31:08 Server closing!
Feb 14 17:31:09 hal postgrey[9975]: Process Backgrounded
Feb 14 17:31:09 hal postgrey[9975]: 2007/02/14-17:31:09 postgrey (type Net::Server::Multiplex) starting! pid(9975)
Feb 14 17:31:09 hal postgrey[9975]: Binding to TCP port 60000 on host 127.0.0.1
Feb 14 17:31:09 hal postgrey[9975]: Setting gid to "113 113"
Feb 14 17:31:09 hal postgrey[9975]: Setting uid to "113"
Feb 14 17:34:20 hal imaplogin: Connection, ip=[::ffff:127.0.0.1]
Feb 14 17:34:25 hal imaplogin: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Feb 14 17:34:25 hal imaplogin: LOGOUT, ip=[::ffff:127.0.0.1]
Feb 14 17:34:33 hal imaplogin: Connection, ip=[::ffff:127.0.0.1]

```

Thanks, I'd really appreciate the help.

---

### Post by cyracks on 2007-02-17
Try this tutorial:
**[http://postfix.wiki.xs4all.nl/index.php?title=Virtual_Users_and_Domains_with_Courier-IMAP_and_MySQL](http://postfix.wiki.xs4all.nl/index.php?title=Virtual_Users_and_Domains_with_Courier-IMAP_and_MySQL)**

btw, this probably is not correct:

transport_maps = proxy:**mysql**:/etc/postfix/mysql-virtual_transports.cf
...
[I] Feb 14 17:30:04 hal **postgrey**[9968]: Setting gid to "113 **113**"
Feb 14 17:30:04 hal postgrey[9968]: Setting uid to "113"
[/I] ...
*mydestination = mydomain.com, localhost, localhost.localdomain*
should be
* mydestination =*
when you are setting mail with mysql support
...

*Name service error for name=hamail.clayscape.com type=A: Host not found*
Do you have mx, and A records correctly configured ?

---

### Post by ClayPTino on 2007-02-17
I may not have the DNS setting correct, as I really have no idea what they are really supposed to be.

I am using GoDaddy for DNS service, and my A record seems to be working (domain points to my apache2 server).  However, I'm not sure how I need to do the MX settings.

Right now they are set as follows (where mydomain.com is the name of my registered site):

Priority: 10
Host: mydomain.com
Goes To: mydomain.com

---

### Post by ClayPTino on 2007-02-17
I found an error in the user database, everything is fine now.

Thank you all for the help.

---

