---
title: "Postfix mail transport unavailable"
date: 2012-10-24
forum: Server Platforms
---

### Post by Zipper5004 on 2012-10-24
Hey guys,

google just brought me to this site and realy hope you can help me.

I have the problem, that my postfix doesnt work as I want it to.

Auto forwarding Mails works finde, but i cant receive and save messages.

var/log/Dovecot.log
```
2012-10-24 18:13:35 pop3-login: Info: Login: user=<mails@hkgame.de>, method=PLAIN, rip=94.220.0.171, lip=84.200.73.132, TLS
2012-10-24 18:13:35 POP3(mails@hkgame.de): Info: Effective uid=5000, gid=5000, home=/var/mail/vhosts/hkgame.de/mails
2012-10-24 18:13:35 POP3(mails@hkgame.de): Info: maildir: data=/var/mail/vhosts/hkgame.de/mails
2012-10-24 18:13:35 POP3(mails@hkgame.de): Info: maildir++: root=/var/mail/vhosts/hkgame.de/mails, index=, control=, inbox=/var/mail/vhosts/hkgame.de/mails
2012-10-24 18:13:35 POP3(mails@hkgame.de): Info: Namespace : Using permissions from /var/mail/vhosts/hkgame.de/mails: mode=0700 gid=-1
2012-10-24 18:13:35 POP3(mails@hkgame.de): Info: Disconnected: Logged out top=0/0, retr=0/0, del=0/0, size=0

```

var/log/mail.warn
```
Oct 24 16:29:24 hkgame postfix/qmgr[22991]: warning: connect to transport private/dovecot: Connection refused
Oct 24 16:30:39 hkgame postfix/smtpd[23044]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
```

var/log/mail.log
```
Oct 24 16:24:11 hkgame postfix/smtpd[23003]: connect from nm3-vm0.bullet.mail.ukl.yahoo.com[217.146.183.228]
Oct 24 16:24:12 hkgame postfix/smtpd[23003]: 0CAA115A071: client=nm3-vm0.bullet.mail.ukl.yahoo.com[217.146.183.228]
Oct 24 16:24:12 hkgame postfix/cleanup[23007]: 0CAA115A071: message-id=<5088162D.8060009@yahoo.de>
Oct 24 16:24:12 hkgame postfix/qmgr[22991]: 0CAA115A071: from=<zipper5004@yahoo.de>, size=2417, nrcpt=1 (queue active)
Oct 24 16:24:12 hkgame postfix/qmgr[22991]: warning: connect to transport private/dovecot: Connection refused
Oct 24 16:24:12 hkgame postfix/error[23011]: 0CAA115A071: to=<mails@hkgame.de>, relay=none, delay=0.18, delays=0.16/0.01/0/0.01, dsn=4.3.0, status=deferred (mail transport unavailable)
Oct 24 16:24:12 hkgame postfix/smtpd[23003]: disconnect from nm3-vm0.bullet.mail.ukl.yahoo.com[217.146.183.228]
```

etc/postfix/main.cf
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

recipient_delimiter = +
readme_directory = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.hkgame.de
mydomain = mail.hkgame.de
myorigin = $mydomain

inet_interfaces = all

mydestination = localhost, $mydomain
#mydestination = $myhostname, localhost.$mydomain, localhost

mynetworks = 127.0.0.0/8 

#Virtuelle Mailboxen
virtual_mailbox_domains = /etc/postfix/virtual_domains
virtual_mailbox_base = /var/mail/vhosts
virtual_mailbox_maps = hash:/etc/postfix/vmailbox
virtual_alias_maps = hash:/etc/postfix/virtual_alias
virtual_minimum_uid = 100
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_transport = dovecot
dovecot_destination_recipient_limit = 1
mailbox_size_limit = 0

smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $mydomain

smtpd_use_tls=yes
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtpd_tls_cert_file=/etc/ssl/certs/hkgame.crt
smtpd_tls_key_file=/etc/ssl/certs/hkgame.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_received_header = yes
tls_random_source = dev:/dev/urandom

#sonstige Policies
smtpd_require_helo = yes
smtpd_client_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_invalid_hostname, reject_unknown_client, reject_rbl_client sbl-xbl.spamhaus.org
#smtpd_sender_restrictions = permit_mynetworks, reject_unknown_address, reject_unknown_sender_domain, reject_non_fqdn_sender 
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_recipient_limit = 250

broken_sasl_auth_clients = yes
```

etc/postfix/vmailbox
```
test@hkgame.de    hkgame.de/test/
spam@hkgame.de    hkgame.de/spam/
mails@hkgame.de    hkgame.de/mails/
root@hkgame.de    hkgame.de/root/
```

It seems like it cant save the mails but I dont know why.
The permission of /var/mail/vhosts/hkgame.de/mails
are 
Owner: vmail [5000]
Group: vmail [5000]

Could you guys help me please? Many Thanks!

---

