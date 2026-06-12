---
title: "Postfix, courier Mysql problems."
date: 2011-01-31
forum: Server Platforms
---

### Post by cromestant on 2011-01-31
Hello, 
I configured my server to have the virtual mail authenticated and stored through mysql DB.
Now the authentication works, but then I got the dreaded -ERR chdir error.

After research and testing for ohurs I finally got it working on ONE account after I created the maildir with maildirmake.

Now I am able to login and "list" messages, but nothing else. When I use postfixadmin to setup a new user, the maildir does not get created so I have the same problem.
I'm trying to troubleshoot what is happening, but can't seem to figure it out.
Here are the relevant config files:

**/etc/postfix/main.cf**
```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf
virtual_mailbox_limit = 51200000
virtual_minimum_uid = 5000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail/
virtual_transport = virtual

# Additional for quota support

virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = mysql:/etc/postfix/mysql_virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = Sorry, the your maildir has overdrawn your diskspace quota, please free up some of spaces of your mailbox try again.
virtual_overquota_bounce = yes


# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h
home_mailbox = Maildir/

readme_directory = no
# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.mydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination =
relayhost =
mynetworks = all
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
myorigin = /etc/mailname
inet_protocols = all
smtpd_sasl_local_domain =
#smtpd_sasl_auth_enable = yes#smtpd_sasl_security_options = noanonymous
#broken_sasl_auth_clients = yes#smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_rec
ipient, reject_unknown_recipient_domain reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit
#smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_do
main, reject_unauth_pipelining, permit
#smtp_tls_security_level = may
#smtpd_tls_security_level = may
#smtpd_tls_auth_only = no
#smtp_tls_note_starttls_offer = yes
#smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
#smtpd_tls_loglevel = 1
#smtpd_tls_received_header = yes#smtpd_tls_session_cache_timeout = 3600stls_random_source = dev:/dev/urandom
                                                                                                         39,1          97%

```

**master.cf**

```

smtp      inet  n       -       -       -       -       smtpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
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
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
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
# ====================================================================
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
# ====================================================================
#
# Recent Cyrus versions can use the existing "lmtp" master.cf entry.
#
# Specify in cyrus.conf:
#   lmtp    cmd="lmtpd -a" listen="localhost:lmtp" proto=tcp4
#
# Specify in main.cf one or more of the following:
#  mailbox_transport = lmtp:inet:localhost
#  virtual_transport = lmtp:inet:localhost
#
# ==================================

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

                
```


**mysql_virtual_alias_maps.cf **
```
user = postfix
password = password
hosts = 127.0.0.1
dbname = postfix
table = alias
select_field = goto
where_field = address

```
**mysql_virtual_mailbox_maps.cf**
```
user = postfix
password = password
hosts = 127.0.0.1
dbname = postfix
table = mailbox
select_field = maildir
where_field = username
#additional_conditions = and active = '1

```

**mysql_virtual_mailbox_limit_maps.cf **
```
user = postfix
password = password
hosts = 127.0.0.1
dbname = postfix
table = mailbox
select_field = quota
where_field = username
#additional_conditions = and active = '1'

```
[B]mysql_virtual_domains_maps.cf 
[/B]```
user = postfix
password = password
hosts = 127.0.0.1
dbname = postfix
table = domain
select_field = domain
where_field = domain
#additional_conditions = and backupmx = '0' and active = '1'
```


**/etc/courier/authmysqlrc  **
```
MYSQL_SERVER 127.0.0.1
MYSQL_USERNAME postfix
MYSQL_PASSWORD password
MYSQL_DATABASE postfix
MYSQL_USER_TABLE mailbox
MYSQL_LOGIN_FIELD username
MYSQL_NAME_FIELD name
MYSQL_CRYPT_PWFIELD password
#MYSQL_CLEAR_PWFIELD     password
#MYSQL_MAILDIR_FIELD maildir
MYSQL_MAILDIR_FIELD CONCAT(SUBSTRING_INDEX(username,'@',-1),'/',SUBSTRING_INDEX(username,'@',1),'/')
MYSQL_QUOTA_FIELD concat(quota,'S')
MYSQL_HOME_FIELD        '/home/vmail/'
MYSQL_UID_FIELD '5000'
MYSQL_GID_FIELD '5000'

```

I'm stumped, 
if you made it here, thanks for the help.

If you need any other config file jsut ask away.

---

### Post by cromestant on 2011-01-31
update,
seems the LDA is the culprit, so postfix as SMTP.

log files are filled with these :

```
Jan 31 14:31:32 li197-251 postfix/master[32702]: warning: process /usr/lib/postfix/cleanup pid 992 exit status 1
Jan 31 14:31:33 li197-251 postfix/master[32702]: warning: process /usr/lib/postfix/smtpd pid 985 exit status 1
Jan 31 14:32:07 li197-251 postfix/master[32702]: terminating on signal 15
Jan 31 14:32:07 li197-251 postfix/master[1105]: daemon started -- version 2.7.0, configuration /etc/postfix
Jan 31 14:32:07 li197-251 postfix/cleanup[1108]: fatal: trace: remove 7B15C8128 log: Permission denied
Jan 31 14:32:08 li197-251 postfix/master[1105]: warning: process /usr/lib/postfix/cleanup pid 1108 exit status 1
Jan 31 14:32:08 li197-251 postfix/master[1105]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
Jan 31 14:32:14 li197-251 postfix/smtpd[1110]: connect from localhost[127.0.0.1]
Jan 31 14:32:37 li197-251 postfix/smtpd[1110]: lost connection after EHLO from localhost[127.0.0.1]
Jan 31 14:32:37 li197-251 postfix/smtpd[1110]: disconnect from localhost[127.0.0.1]
Jan 31 14:33:08 li197-251 postfix/cleanup[1115]: fatal: trace: remove 3EAA08128 log: Permission denied
Jan 31 14:33:09 li197-251 postfix/master[1105]: warning: process /usr/lib/postfix/cleanup pid 1115 exit status 1
Jan 31 14:33:09 li197-251 postfix/master[1105]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
Jan 31 14:34:09 li197-251 postfix/cleanup[1116]: fatal: trace: remove 40FD28128 log: Permission denied

```

no idea how to debug this

---

### Post by cromestant on 2011-01-31
another update, 

fixed some permissions, and restarted it now some old mails have been sent. but still getting relay problems


postfix/smtpd[1723]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 554 5.7.1

---

### Post by cromestant on 2011-01-31
definitely a config prolbme with relaying...


look at this:
```
Jan 31 15:37:31 li197-251 postfix/smtpd[1871]: connect from localhost[127.0.0.1]
Jan 31 15:37:31 li197-251 postfix/smtpd[1871]: warning: connect to 127.0.0.1:10023: Connection refused
Jan 31 15:37:31 li197-251 postfix/smtpd[1871]: warning: problem talking to server 127.0.0.1:10023: Connection refused
Jan 31 15:37:32 li197-251 postfix/smtpd[1871]: warning: connect to 127.0.0.1:10023: Connection refused
Jan 31 15:37:32 li197-251 postfix/smtpd[1871]: warning: problem talking to server 127.0.0.1:10023: Connection refused
Jan 31 15:37:32 li197-251 postfix/smtpd[1871]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 451 4.3.5 Server configuration problem; from=<admin@domain.com> to=<test@domain.com> proto=ESMTP helo=<postfixadmin.domain.com>
Jan 31 15:37:32 li197-251 postfix/smtpd[1871]: warning: non-SMTP command from localhost[127.0.0.1]: To: test@domain.com
Jan 31 15:37:32 li197-251 postfix/smtpd[1871]: disconnect from localhost[127.0.0.1]


```


what could thi sbe?


EDIT MORE INFO:

ok this is weird, some scripts are able to send, others are not.
Plus google is trying to send an email I sent form my gmail acconut to test and is unable to send it also.
log file:

```


Jan 31 15:57:25 li197-251 postfix/smtpd[2068]: connect from mail-wy0-f176.google.com[74.125.82.176]
Jan 31 15:57:25 li197-251 postfix/smtpd[2068]: warning: connect to 127.0.0.1:10023: Connection refused
Jan 31 15:57:25 li197-251 postfix/smtpd[2068]: warning: problem talking to server 127.0.0.1:10023: Connection refused
Jan 31 15:57:26 li197-251 postfix/smtpd[2068]: warning: connect to 127.0.0.1:10023: Connection refused
Jan 31 15:57:26 li197-251 postfix/smtpd[2068]: warning: problem talking to server 127.0.0.1:10023: Connection refused
Jan 31 15:57:26 li197-251 postfix/smtpd[2068]: NOQUEUE: reject: RCPT from mail-wy0-f176.google.com[74.125.82.176]: 451 4.3.5 Server configuration problem; from=<crom*****t@gmail.com> to=<crom***t@domain.com> proto=ESMTP helo=<mail-wy0-f176.google.com>
Jan 31 15:57:26 li197-251 postfix/smtpd[2068]: disconnect from mail-wy0-f176.google.com[74.125.82.176]

```

I really don't get this....

---

