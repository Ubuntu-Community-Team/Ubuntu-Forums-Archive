---
title: "postfix - /home/vmail/mailboxXX is not created"
date: 2011-06-07
forum: Server Platforms
---

### Post by jstd on 2011-06-07
Hello,

I'm following this HowTo:
[https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)
when I try to log in with squirrelmail, I get this ERROR: Connection dropped by IMAP server.

The problem might be, that there are no files or directorys in /home/vmail

Creating domains and mailadresses with Postfixadmin works perfectly fine (checked it with phpmyadmin), but no direcotrys are created.

the logfile, while sending the welcome mail shows me:

```
Jun  7 21:11:20 jstdEU postfix/smtpd[9265]: connect from localhost.localdomain[127.0.0.1]
Jun  7 21:11:20 jstdEU postfix/smtpd[9265]: 226E52108C24: client=localhost.localdomain[127.0.0.1]
Jun  7 21:11:20 jstdEU postfix/cleanup[9269]: 226E52108C24: message-id=<20110607191120.226E52108C24@XXX.dyndns-blog.com>
,Jun  7 21:11:20 jstdEU postfix/smtpd[9265]: disconnect from localhost.localdomain[127.0.0.1]
Jun  7 21:11:20 jstdEU postfix/qmgr[9259]: 226E52108C24: from=<admin@XXX.dyndns-blog.com>, size=598, nrcpt=1 (queue active)
Jun  7 21:11:20 jstdEU postfix/error[9271]: 226E52108C24: to=<mailbox@XXX.dyndns-blog.com/>, orig_to=<mailbox@XXX.dyndns-blog.com>, relay=none, delay=0.81, delays=0.55/0.01/0/0.26, dsn=5.1.3, status=bounced (bad address syntax)
Jun  7 21:11:20 jstdEU postfix/cleanup[9269]: E790C2108C28: message-id=<20110607191120.E790C2108C28@XXX.dyndns-blog.com>
Jun  7 21:11:21 jstdEU postfix/qmgr[9259]: E790C2108C28: from=<>, size=2810, nrcpt=1 (queue active)
Jun  7 21:11:21 jstdEU postfix/bounce[9272]: 226E52108C24: sender non-delivery notification: E790C2108C28
Jun  7 21:11:21 jstdEU postfix/qmgr[9259]: 226E52108C24: removed
Jun  7 21:11:21 jstdEU postfix/virtual[9274]: E790C2108C28: to=<admin@XXX.dyndns-blog.com>, relay=virtual, delay=0.35, delays=0.21/0.01/0/0.13, dsn=5.1.1, status=bounced (unknown user: "admin@XXX.dyndns-blog.com")
Jun  7 21:11:21 jstdEU postfix/qmgr[9259]: E790C2108C28: removed

```

my main.cf:
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

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = XXX.dyndns-blog.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination =
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
#mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

# Virtual Mailbox Domain Settings

virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf
virtual_mailbox_limit = 51200000
virtual_minimum_uid = 5000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_transport = virtual

# Additional for quota support

virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = mysql:/etc/postfix/mysql_virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = Sorry, the your maildir has overdrawn your diskspace quo$
virtual_overquota_bounce = yes


```

vmail is owner of /home/vmail:
```
cd /home
chown -R vmail.vmail vmail

```
Can anyone help?
Thanks, johannes

P.s.: I skipped the part installing and setting up SMTP authentication, but I thinks thats fine...

---

