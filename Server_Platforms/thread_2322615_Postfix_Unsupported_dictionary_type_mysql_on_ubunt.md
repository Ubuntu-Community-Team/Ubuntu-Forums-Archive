---
title: "Postfix: Unsupported dictionary type: mysql on ubuntu 16.04"
date: 2016-04-29
forum: Server Platforms
---

### Post by Ppaa on 2016-04-29
Hi! After upgrade to ubuntu 15.10 to 16.04 in mail.err - postfix/proxymap[35158]: error: unsupported dictionary type: mysql
postconf -m | grep mysql
mysql exist
reinstall postfix-mysql and postfix not work

postconf -n
```

alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
allow_min_user = no
allow_percent_hack = no
biff = no
body_checks = pcre:/etc/postfix/body_checks.pcre
broken_sasl_auth_clients = yes
command_directory = /usr/sbin
content_filter = smtp-amavis:[127.0.0.1]:10024
daemon_directory = /usr/lib/postfix/sbin
data_directory = /var/lib/postfix
debug_peer_level = 2
debugger_command = PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin ddd $daemon_directory/$process_name $process_id &                                                                     sleep 5
disable_vrfy_command = yes
dovecot_destination_recipient_limit = 1
enable_original_recipient = no
header_checks = pcre:/etc/postfix/header_checks
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
lmtp_tls_mandatory_protocols = !SSLv2 !SSLv3
lmtp_tls_protocols = !SSLv2 !SSLv3
mail_owner = postfix
mailbox_command = /usr/lib/dovecot/deliver
mailq_path = /usr/bin/mailq
message_size_limit = 15728640
mydestination = $myhostname, localhost, x-fil.es, localhost.localdomain
mydomain =domain.com
myhostname = domain.com
mynetworks = 127.0.0.1, 192.168.1.0/24
myorigin = $mydomain
newaliases_path = /usr/bin/newaliases
postscreen_access_list = permit_mynetworks, cidr:/etc/postfix/postscreen_access.cidr
postscreen_blacklist_action = enforce
postscreen_dnsbl_action = enforce
postscreen_dnsbl_reply_map = texthash:/etc/postfix/postscreen_dnsbl_reply
postscreen_dnsbl_sites = zen.spamhaus.org*3 b.barracudacentral.org*2 bl.spameatingmonkey.net*2 bl.spamcop.net dnsbl.s                                                                    orbs.net psbl.surriel.com bl.mailspike.net swl.spamhaus.org*-4 list.dnswl.org=127.[0..255].[0..255].0*-2 list.dnswl.o                                                                    rg=127.[0..255].[0..255].1*-3 list.dnswl.org=127.[0..255].[0..255].[2..255]*-4
postscreen_dnsbl_threshold = 2
postscreen_dnsbl_whitelist_threshold = -2
postscreen_greet_action = enforce
proxy_read_maps = $canonical_maps $lmtp_generic_maps $local_recipient_maps $mydestination $mynetworks $recipient_bcc_                                                                    maps $recipient_canonical_maps $relay_domains $relay_recipient_maps $relocated_maps $sender_bcc_maps $sender_canonica                                                                    l_maps $smtp_generic_maps $smtpd_sender_login_maps $transport_maps $virtual_alias_domains $virtual_alias_maps $virtua                                                                    l_mailbox_domains $virtual_mailbox_maps $smtpd_sender_restrictions
queue_directory = /var/spool/postfix
recipient_bcc_maps = proxy:mysql:/etc/postfix/mysql/recipient_bcc_maps_user.cf proxy:mysql:/etc/postfix/mysql/recipie                                                                    nt_bcc_maps_domain.cf
recipient_delimiter = +
relay_domains = $mydestination proxy:mysql:/etc/postfix/mysql/relay_domains.cf
relayhost = relay.lipetsk.ru:25
sender_bcc_maps = proxy:mysql:/etc/postfix/mysql/sender_bcc_maps_user.cf proxy:mysql:/etc/postfix/mysql/sender_bcc_ma                                                                    ps_domain.cf
sendmail_path = /usr/sbin/sendmail
setgid_group = postdrop
shlib_directory = /usr/lib/postfix/lib
smtp-amavis_destination_recipient_limit = 1
smtp_tls_CAfile = $smtpd_tls_CAfile
smtp_tls_loglevel = 0
smtp_tls_mandatory_protocols = !SSLv2 !SSLv3
smtp_tls_note_starttls_offer = yes
smtp_tls_protocols = !SSLv2 !SSLv3
smtp_tls_security_level = may
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_end_of_data_restrictions = check_policy_service inet:127.0.0.1:7777
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks permit_sasl_authenticated reject_non_fqdn_helo_hostname reject_invalid_he                                                                    lo_hostname check_helo_access pcre:/etc/postfix/helo_access.pcre
smtpd_recipient_restrictions = reject_unknown_recipient_domain reject_non_fqdn_recipient reject_unlisted_recipient ch                                                                    eck_policy_service inet:127.0.0.1:7777 permit_mynetworks permit_sasl_authenticated reject_unauth_destination
smtpd_reject_unlisted_recipient = yes
smtpd_reject_unlisted_sender = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_sender_login_maps = proxy:mysql:/etc/postfix/mysql/sender_login_maps.cf
smtpd_sender_restrictions = reject_unknown_sender_domain reject_non_fqdn_sender reject_unlisted_sender permit_mynetwo                                                                    rks reject_sender_login_mismatch permit_sasl_authenticated check_sender_access pcre:/etc/postfix/sender_access.pcre
smtpd_tls_CAfile = /etc/ssl/certs/iRedMail.crt
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/ssl/certs/iRedMail.crt
smtpd_tls_dh1024_param_file = /etc/ssl/dhparams.pem
smtpd_tls_exclude_ciphers = aNULL, eNULL, EXPORT, DES, RC4, MD5, PSK, aECDH, EDH-DSS-DES-CBC3-SHA, EDH-RSA-DES-CDC3-S                                                                    HA, KRB5-DE5, CBC3-SHA
smtpd_tls_key_file = /etc/ssl/private/iRedMail.key
smtpd_tls_loglevel = 0
smtpd_tls_mandatory_protocols = !SSLv2 !SSLv3
smtpd_tls_protocols = !SSLv2 !SSLv3
smtpd_tls_security_level = may
swap_bangpath = no
tls_random_source = dev:/dev/urandom
transport_maps = proxy:mysql:/etc/postfix/mysql/transport_maps_user.cf proxy:mysql:/etc/postfix/mysql/transport_maps_                                                                    domain.cf
unknown_local_recipient_reject_code = 550
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql/virtual_alias_maps.cf proxy:mysql:/etc/postfix/mysql/domain_alias                                                                    _maps.cf proxy:mysql:/etc/postfix/mysql/catchall_maps.cf proxy:mysql:/etc/postfix/mysql/domain_alias_catchall_maps.cf
virtual_gid_maps = static:2000
virtual_mailbox_base = /var/vmail
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql/virtual_mailbox_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql/virtual_mailbox_maps.cf
virtual_minimum_uid = 2000
virtual_transport = dovecot
virtual_uid_maps = static:2000

```

dpkg -l | grep -i mysql

```

ii  dbconfig-mysql                      2.0.4ubuntu1                        all          dbconfig-common MySQL/MariaDB support
ii  dovecot-mysql                       1:2.2.22-1ubuntu2                   amd64        secure POP3/IMAP server - MySQL support
ii  libdbd-mysql-perl                   4.033-1build2                       amd64        Perl5 database interface to the MySQL database
ii  libmysqlclient18:amd64              5.6.30-0ubuntu0.15.10.1             amd64        MySQL database client library
ii  libmysqlclient20:amd64              5.7.11-0ubuntu6                     amd64        MySQL database client library
ii  mysql-apt-config                    0.7.2-1                             all          Auto configuration for MySQL APT Repo.
ii  mysql-client                        5.7.12-1ubuntu15.10                 amd64        MySQL Client meta package depending on latest version
ii  mysql-common                        5.7.12-1ubuntu15.10                 amd64        MySQL configuration for client and server
ii  mysql-community-client              5.7.12-1ubuntu15.10                 amd64        MySQL Client and client tools
ii  mysql-community-server              5.7.12-1ubuntu15.10                 amd64        MySQL Server and server tools
ii  mysql-server                        5.7.12-1ubuntu15.10                 amd64        MySQL Server meta package depending on latest version
ii  mysqltuner                          1.6.0-1                             all          high-performance MySQL tuning script
ii  mytop                               1.9.1-2                             all          top like query monitor for MySQL
ii  php-mysql                           1:7.0+35ubuntu6                     all          MySQL module for PHP [default]
rc  php5-mysql                          5.6.20+dfsg-1+deb.sury.org~wily+1   amd64        MySQL module for php5
rc  php5-mysqlnd                        5.6.20+dfsg-1+deb.sury.org~wily+1   amd64        MySQL module for php5 (Native Driver)
ii  php7.0-mysql                        7.0.4-7ubuntu2                      amd64        MySQL module for PHP
ii  phpmyadmin                          4:4.5.4.1-2ubuntu1                  all          MySQL web administration tool
ii  postfix-mysql                       3.1.0-3                             amd64        MySQL map support for Postfix
ii  python-mysql.connector              2.0.4-1                             all          pure Python implementation of MySQL Client/Server protocol
ii  python-mysqldb                      1.3.7-1build2                       amd64        Python interface to MySQL
ii  python-pymysql                      0.7.2-1                             all          Pure-Python MySQL driver - Python 2.x

```

---

### Post by Jeraimee on 2016-05-15
Seems to be an error in the package. You need to symlink postfix-mysql.so.1.0.1 to dict_mysql.so:
```

cd /usr/lib/postfix
ln -s postfix-mysql.so.1.0.1 dict_mysql.so

```

---

### Post by mleisher on 2016-05-22
I'm having a similar problem on 16.04. The mysql dictionary type is supported, but with **alias_maps = mysql:/etc/postfix/aliases.cf** postfix consistently generates a *Temporary lookup failure* for every email address, alias or not. When I do a **postmap -q alias mysql:/etc/postfix/aliases.cf** aliases are expanded properly.

---

### Post by mleisher on 2016-05-22
My problem turned out to be postfix being unable to connect to the unix socket for mysql no matter what permissions were used, but when I connect to 127.0.0.1:3306 everything works.

---

### Post by trevelyon on 2016-10-17
Thanks for this thread.  I had the same problem and followed your solution of creating the link to solve it.  I also opened a bug here: [https://bugs.launchpad.net/ubuntu/+source/postfix/+bug/1628258](https://bugs.launchpad.net/ubuntu/+source/postfix/+bug/1628258)

It turns out this bug is caused by not updating the config files along with the postfix package, in particular my /etc/postfix/dynamicmaps.cf file.  The proper fix for this would be:

cp /usr/share/postfix/dynamicmaps.cf /etc/postfix/

That brings in the proper dynamicmaps.cf file and solves the issues without creating a symlink that may break during updates.  Hope this helps

---

