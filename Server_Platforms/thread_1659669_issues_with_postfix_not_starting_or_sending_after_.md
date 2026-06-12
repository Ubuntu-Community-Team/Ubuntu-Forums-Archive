---
title: "issues with postfix not starting or sending after adding this:"
date: 2011-01-04
forum: Server Platforms
---

### Post by kustomjs on 2011-01-04
Hi Guys
I have ubuntu 10.04 server with postfix running and when I tried to add alias to mysql and mail server I get this error message:

```
Jan  4 10:33:13 mail postfix/postfix-script[2419]: warning: group or other writable: /etc/postfix/./postfix-script
Jan  4 10:33:13 mail postfix/postfix-script[2420]: warning: group or other writable: /etc/postfix/./postfix-script.dpkg-dist
Jan  4 10:33:27 mail postfix/smtpd[2463]: fatal: /etc/postfix/mysql_alias.cf: bad string length 0 < 1: dbname = 
Jan  4 10:33:28 mail postfix/master[2071]: warning: process /usr/lib/postfix/smtpd pid 2463 exit status 1
Jan  4 10:33:28 mail postfix/master[2071]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan  4 10:33:37 mail postfix/trivial-rewrite[2464]: fatal: /etc/postfix/mysql_alias.cf: bad string length 0 < 1: dbname = 
Jan  4 10:33:38 mail postfix/master[2071]: warning: process /usr/lib/postfix/trivial-rewrite pid 2464 exit status 1
Jan  4 10:33:38 mail postfix/master[2071]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
Jan  4 10:33:43 mail postfix/cleanup[2465]: fatal: /etc/postfix/mysql_alias.cf: bad string length 0 < 1: dbname = 
Jan  4 10:33:44 mail postfix/master[2071]: warning: process /usr/lib/postfix/cleanup pid 2465 exit status 1
Jan  4 10:33:44 mail postfix/master[2071]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
Jan  4 10:34:20 mail postfix/master[2071]: terminating on signal 15
Jan  4 10:34:46 mail postfix/master[2693]: daemon started -- version 2.7.0, configuration /etc/postfix
Jan  4 10:35:03 mail postfix/smtpd[2703]: fatal: /etc/postfix/mysql_alias.cf: bad string length 0 < 1: dbname = 
Jan  4 10:35:04 mail postfix/master[2693]: warning: process /usr/lib/postfix/smtpd pid 2703 exit status 1
Jan  4 10:35:04 mail postfix/master[2693]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan  4 10:36:04 mail postfix/smtpd[2716]: fatal: /etc/postfix/mysql_alias.cf: bad string length 0 < 1: table = 
Jan  4 10:36:05 mail postfix/master[2693]: warning: process /usr/lib/postfix/smtpd pid 2716 exit status 1
Jan  4 10:36:05 mail postfix/master[2693]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan  4 10:37:05 mail postfix/smtpd[2719]: fatal: /etc/postfix/mysql_alias.cf: bad string length 0 < 1: table = 
Jan  4 10:37:06 mail postfix/master[2693]: warning: process /usr/lib/postfix/smtpd pid 2719 exit status 1
Jan  4 10:37:06 mail postfix/master[2693]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan  4 10:37:35 mail postfix/master[2693]: terminating on signal 15
Jan  4 10:37:37 mail postfix/master[2843]: daemon started -- version 2.7.0, configuration /etc/postfix
Jan  4 11:02:16 mail postfix/smtpd[2957]: fatal: /etc/postfix/mysql_alias.cf: bad string length 0 < 1: table = 
Jan  4 11:02:17 mail postfix/master[2843]: warning: process /usr/lib/postfix/smtpd pid 2957 exit status 1
Jan  4 11:02:17 mail postfix/master[2843]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan  4 11:03:17 mail postfix/smtpd[2962]: fatal: /etc/postfix/mysql_alias.cf: bad string length 0 < 1: table = 
Jan  4 11:03:18 mail postfix/master[2843]: warning: process /usr/lib/postfix/smtpd pid 2962 exit status 1
Jan  4 11:03:18 mail postfix/master[2843]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan  4 11:04:18 mail postfix/smtpd[2966]: fatal: /etc/postfix/mysql_alias.cf: bad string length 0 < 1: table = 
Jan  4 11:04:19 mail postfix/master[2843]: warning: process /usr/lib/postfix/smtpd pid 2966 exit status 1
Jan  4 11:04:19 mail postfix/master[2843]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan  4 11:05:19 mail postfix/smtpd[2970]: fatal: /etc/postfix/mysql_alias.cf: bad string length 0 < 1: table = 
Jan  4 11:05:20 mail postfix/master[2843]: warning: process /usr/lib/postfix/smtpd pid 2970 exit status 1
Jan  4 11:05:20 mail postfix/master[2843]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan  4 11:05:37 mail postfix/postfix-script[3032]: warning: group or other writable: /etc/postfix/./postfix-script
Jan  4 11:05:37 mail postfix/postfix-script[3033]: warning: group or other writable: /etc/postfix/./postfix-script.dpkg-dist

```

I used this guide of: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

here is my main.cf

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name
biff = no


# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no


myhostname = mail.nxxxxxx.com
alias_maps = hash:/etc/postfix/aliases 
alias_database = hash:/etc/postfix/aliases 
myorigin = /etc/mailname
mydestination = $myhostname, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
recipient_delimiter = +
inet_interfaces = all
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf  
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_path = private/auth
smtpd_sasl_type = dovecot
mailbox_size_limit = 5120000



virtual_mailbox_limit_maps = mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
virtual_maildir_extended = yes
inet_protocols = ipv4

```

when I tried to add: virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf # and this is for domain lookups 

into my main.cf as: virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf,mysql:/etc/postfix/mysql_alias.cf

that is when I start getting them errors and cant send out messages.

also here is the information from mysql:/etc/postfix/mysql_alias.cf

```
user=
password= 
dbname=mail table=aliases 
select_field=destination where_field=mail
hosts=127.0.0.1 additional_conditions = and enabled = 1
```

---

### Post by kustomjs on 2011-01-04
just a update I was able to get the postfix and sending error gone and this what I had to do:

for mysql:/etc/postfix/mysql_alias.cf
```
user =  
password = 
dbname = mail 
table = aliases 
select_field = destination 
where_field = mail
hosts = 127.0.0.1 
additional_conditions = and enabled = 1
```

then I went back into main.cf and put it like this: virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf,mysql:/etc/postfix/mysql_alias.cf

---

