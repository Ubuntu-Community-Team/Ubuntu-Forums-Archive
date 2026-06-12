---
title: "dovecot + postfix + thunderbird SSL warnings"
date: 2012-07-18
forum: Server Platforms
---

### Post by koprive on 2012-07-18
Hello my name is Simon and I'm new here. I run dovecot 2.0.19 and postfix 2.9.1 on Ubuntu 12.04 and have configured both to use SSL (I think) using a self signed certificate. Now all seems to work well, I can send and receive mails, but there are a bunch of SSL warnings in the mail.log every time I run thunderbird. The messages look friendly but WARNING WARNING scares me. Is this normal?

```
Jul 18 21:50:17 myhost dovecot: pop3-login: Warning: SSL: where=0x10, ret=1: before/accept initialization [192.168.10.2]
Jul 18 21:50:17 myhost dovecot: pop3-login: Warning: SSL: where=0x2001, ret=1: before/accept initialization [192.168.10.2]
Jul 18 21:50:17 myhost dovecot: pop3-login: Warning: SSL: where=0x2001, ret=1: SSLv3 read client hello A [192.168.10.2]
Jul 18 21:50:17 myhost dovecot: pop3-login: Warning: SSL: where=0x2001, ret=1: SSLv3 write server hello A [192.168.10.2]
Jul 18 21:50:17 myhost dovecot: pop3-login: Warning: SSL: where=0x2001, ret=1: SSLv3 write certificate A [192.168.10.2]
Jul 18 21:50:17 myhost dovecot: pop3-login: Warning: SSL: where=0x2001, ret=1: SSLv3 write key exchange A [192.168.10.2]
Jul 18 21:50:17 myhost dovecot: pop3-login: Warning: SSL: where=0x2001, ret=1: SSLv3 write server done A [192.168.10.2]
Jul 18 21:50:17 myhost dovecot: pop3-login: Warning: SSL: where=0x2001, ret=1: SSLv3 flush data [192.168.10.2]
Jul 18 21:50:17 myhost dovecot: pop3-login: Warning: SSL: where=0x2002, ret=-1: SSLv3 read client certificate A [192.168.10.2]
Jul 18 21:50:17 myhost dovecot: pop3-login: Warning: SSL: where=0x2002, ret=-1: SSLv3 read client certificate A [192.168.10.2]
Jul 18 21:50:17 myhost dovecot: pop3-login: Warning: SSL: where=0x2001, ret=1: SSLv3 read client key exchange A [192.168.10.2]
Jul 18 21:50:17 myhost dovecot: pop3-login: Warning: SSL: where=0x2001, ret=1: SSLv3 read finished A [192.168.10.2]
Jul 18 21:50:17 myhost dovecot: pop3-login: Warning: SSL: where=0x2001, ret=1: SSLv3 write session ticket A [192.168.10.2]
Jul 18 21:50:17 myhost dovecot: pop3-login: Warning: SSL: where=0x2001, ret=1: SSLv3 write change cipher spec A [192.168.10.2]
Jul 18 21:50:17 myhost dovecot: pop3-login: Warning: SSL: where=0x2001, ret=1: SSLv3 write finished A [192.168.10.2]
Jul 18 21:50:17 myhost dovecot: pop3-login: Warning: SSL: where=0x2001, ret=1: SSLv3 flush data [192.168.10.2]
Jul 18 21:50:17 myhost dovecot: pop3-login: Warning: SSL: where=0x20, ret=1: SSL negotiation finished successfully [192.168.10.2]
Jul 18 21:50:17 myhost dovecot: pop3-login: Warning: SSL: where=0x2002, ret=1: SSL negotiation finished successfully [192.168.10.2]
Jul 18 21:50:17 myhost dovecot: auth-worker: mysql(localhost): Connected to database virtual_email
Jul 18 21:50:17 myhost dovecot: pop3-login: Login: user=<me@myd.com>, method=PLAIN, rip=192.168.10.2, lip=192.168.10.3, mpid=4126, TLS
Jul 18 21:50:18 myhost dovecot: pop3(me@myd.com): Disconnected: Logged out top=0/0, retr=1/2958, del=0/6228, size=3217288983
Jul 18 21:50:18 myhost dovecot: pop3-login: Warning: SSL alert: where=0x4008, ret=256: warning close notify [192.168.10.2]
```The warnings are there whenever thunderbird logs in over pop3 or imap.


Here is my doveconf -n

```
# 2.0.19: /etc/dovecot/dovecot.conf
# OS: Linux 3.2.0-26-generic i686 Ubuntu 12.04 LTS ext4
auth_mechanisms = plain login digest-md5
log_timestamp = "%Y-%m-%d %H:%M:%S "
mail_location = maildir:/var/vmail/%d/%n/Maildir
passdb {
  args = /etc/dovecot/dovecot-sql.conf
  driver = sql
}
protocols = imap pop3
service auth {
  unix_listener /var/spool/postfix/private/auth {
    group = vmail
    mode = 0666
    user = vmail
  }
  unix_listener auth-master {
    mode = 0666
  }
  vsz_limit = 64 M
}
ssl = required
ssl_ca = </etc/pki/CA/cacrl.pem
ssl_cert = </etc/pki/CA/mail/mail.pem
ssl_cipher_list = ALL:!LOW:!SSLv2
ssl_key = </etc/pki/CA/mail/mail.key
userdb {
  args = uid=5000 gid=5000 home=/home/vmail/%d/%n allow_all_users=yes
  driver = static
}
verbose_ssl = yes
protocol imap {
  imap_max_line_length = 64 k
}
protocol lda {
  auth_socket_path = /var/run/dovecot/auth-master
  postmaster_address = adm@myd.com
}
```And postconf -n

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = smtp-amavis:[127.0.0.1]:10024
dovecot_destination_recipient_limit = 1
inet_interfaces = all
mailbox_command = /usr/lib/dovecot/deliver
mailbox_size_limit = 0
mydestination = my.dom.com, myhost, localhost.localdomain, localhost
myhostname = my.dom.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = dom.com
recipient_delimiter = +
relayhost =
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination,check_policy_service inet:127.0.0.1:10023
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
virtual_alias_domains =
virtual_alias_maps = mysql:/etc/postfix/virtual/mysql-virtual-alias-maps.cf, mysql:/etc/postfix/virtual/mysql-virtual-email2email.cf
virtual_gid_maps = static:5000
virtual_mailbox_domains = mysql:/etc/postfix/virtual/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/virtual/mysql-virtual-mailbox-maps.cf
virtual_transport = dovecot
virtual_uid_maps = static:5000
```I would also appreciate any possible errors pointed out.
Any more info required from me let me know. Thanks.

---

