---
title: "courier / postfix on ubuntu 13.10"
date: 2014-03-08
forum: Server Platforms
---

### Post by bluethundr2 on 2014-03-08
Hey all,

 I've built a mail server using flurdy's famous guide on Ubuntu 13.10 LTS.

 When I test out the mail server portion alone from courier IMAP everything is working as planned. The mail server can send and receive to the virual mailboxes I've setup. 

However courier imap is having trouble authenticating users and I think the problem could be database related. As in courier may not be communicating with MySQL. 

Please have a look at my setup:

courier IMAP login fails:
```

root@mail:~# telnet localhost 143
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2011 Double Precision, Inc.  See COPYING for distribution information.
a login lilspenny@example.com secret
a NO Login failed.

```



I'm seeing this in the mail logs:

```

Mar  8 12:24:23 ip-172-31-41-226 authdaemond: received auth request, service=imap, authtype=login
Mar  8 12:24:23 ip-172-31-41-226 authdaemond: FAIL, all modules rejected
Mar  8 12:24:23 ip-172-31-41-226 imapd: LOGIN FAILED, user=lilspenny@example, ip=[::ffff:127.0.0.1]

```


I'm not seeing any activity in the mysql logs

This is the output of postconf -n

```

root@mail:~# postconf -n
alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
delay_warning_time = 4h
disable_vrfy_command = yes
inet_interfaces = all
local_recipient_maps =
mailbox_size_limit = 0
masquerade_domains = mail.example.com example.com !sub.dyndomain.com
masquerade_exceptions = root
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination =
myhostname = mail.example.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mynetworks_style = host
myorigin = example.com
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_helo_timeout = 60s
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
transport_maps = mysql:/etc/postfix/mysql_transport.cf
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = static:5000

```

And these are my mysql map files:

mysql_alias.cf
```

user=mail
password=secret
dbname=maildb 
table=aliases 
select_field=destination i
where_field=mail 
hosts=127.0.0.1 i
additional_conditions = and enabled = 1

```

mysql_domains.cf
```

user=mail
password=secret
dbname=maildb
table=domains
select_field=domain
where_field=domain
hosts=127.0.0.1
additional_conditions = and enabled = 10

```

mysql_mailbox.cf
```

password=secret
dbname=maildb
table=users
select_field=maildir
where_field=id
hosts=127.0.0.1
additional_conditions = and enabled = 1

```

mysql_transport.cf
```

user=mail
password=secret
dbname=maildb
table=domains
select_field=transport
where_field=domain
hosts=127.0.0.1
additional_conditions = and enabled = 1

```

And I can log into the database and use the maildb using the credentials shown above (but using a real password of course).

And this is what I have in my authdaemonrc

```

root@mail:/etc/postfix# cat /etc/courier/authdaemonrc | grep -v "#"




authmodulelistorig="authmysql"


daemons=5


authdaemonvar=/var/run/courier/authdaemon


DEBUG_LOGIN=2


DEFAULTOPTIONS=""


LOGGEROPTS=""

```

And this is the contents of my authmysqlrc

```

root@mail:/etc/postfix# cat /etc/courier/authmysqlrc | grep -v "#"



MYSQL_SERVER            127.0.0.1
MYSQL_USERNAME          mail
MYSQL_PASSWORD          secret




MYSQL_PORT              0


MYSQL_OPT               0


MYSQL_DATABASE          maildb



MYSQL_USER_TABLE        users


MYSQL_CRYPT_PWFIELD     crypt



MYSQL_UID_FIELD         uid


MYSQL_GID_FIELD         gid


MYSQL_LOGIN_FIELD       id


MYSQL_HOME_FIELD        home


MYSQL_NAME_FIELD        name

MYSQL_MAILDIR_FIELD concat(home,'/',maildir)





MYSQL_WHERE_CLAUSE enabled=1

```

I'm hoping someone out there with an eagel eye might be able to spot trouble in my config or perhaps someone can help me with a few more troubleshooting steps.

Thank you
Tim

---

### Post by vampire_k on 2014-03-17
Exact same problem. Hope someone can help.

---

### Post by vampire_k on 2014-03-17
I managed to get it working. In the mysql_alias.cf, mysql_domains.cf, mysql_mailbox.cf, I changed "hosts=127.0.0.1" to "hosts=localhost".

---

