---
title: "Unable login in to UebiMiau"
date: 2009-04-12
forum: Server Platforms
---

### Post by Spikerok on 2009-04-12
Im using ISPConfig, and UebiMiau as email tool.
To login im using [email]user@domain.com[/email] and password which was set in ftp/email
When i try to login im getting that login is failed

My log file
[PHP]
Apr 12 22:51:38 server1 pop3d: Connection, ip=[::ffff:127.0.0.1]
Apr 12 22:51:40 server1 pop3d: LOGIN FAILED, user=web1_user, ip=[::ffff:127.0.0.1]
Apr 12 22:51:45 server1 pop3d: Disconnected, ip=[::ffff:127.0.0.1]
[/PHP]

im using postfix and ISPconfig
im not using maildir.

my postfix/main.cf
[PHP]
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
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = server1.web-a.org.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = server1.web-a.org.uk, localhost.web-a.org.uk, , localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

virtual_maps = hash:/etc/postfix/virtusertable

mydestination = /etc/postfix/local-host-names
[/PHP]

---

### Post by Spikerok on 2009-04-12
netstat -tap
[PHP]
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:mysql                 *:*                     LISTEN      4210/mysqld
tcp        0      0 *:www                   *:*                     LISTEN      4956/apache2
tcp        0      0 *:81                    *:*                     LISTEN      4771/ispconfig_http
tcp        0      0 ubuntu.lan:domain       *:*                     LISTEN      5081/named
tcp        0      0 localhost.locald:domain *:*                     LISTEN      5081/named
tcp        0      0 *:ssh                   *:*                     LISTEN      4120/sshd
tcp        0      0 localhost.localdoma:953 *:*                     LISTEN      5081/named
tcp        0      0 *:smtp                  *:*                     LISTEN      5046/master
tcp        0      0 *:https                 *:*                     LISTEN      4956/apache2
tcp        0     52 ubuntu.lan:ssh          PC194765792715.lan:2164 ESTABLISHED 4946/sshd: vladisla
tcp6       0      0 [::]:imaps              [::]:*                  LISTEN      4325/couriertcpd
tcp6       0      0 [::]:pop3s              [::]:*                  LISTEN      4368/couriertcpd
tcp6       0      0 [::]:pop3               [::]:*                  LISTEN      4346/couriertcpd
tcp6       0      0 [::]:imap2              [::]:*                  LISTEN      4303/couriertcpd
tcp6       0      0 [::]:ftp                [::]:*                  LISTEN      5098/proftpd: (acce
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      4120/sshd
tcp6       0      0 localhost:953           [::]:*                  LISTEN      5081/named
tcp6       0      0 [::]:smtp               [::]:*                  LISTEN      5046/master
[/PHP]

---

### Post by Spikerok on 2009-04-12
im thinking of changing postfix on sendmail because i know alot more about sendmail..

---

### Post by Spikerok on 2009-04-13
bump..

---

