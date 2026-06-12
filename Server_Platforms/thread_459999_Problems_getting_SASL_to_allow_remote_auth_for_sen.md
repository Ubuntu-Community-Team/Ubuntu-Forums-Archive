---
title: "Problems getting SASL to allow remote auth for sending mail"
date: 2007-05-31
forum: Server Platforms
---

### Post by badfeet on 2007-05-31
have set up an Ubuntu server (6.06LTS) following the guide at [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/).
Almost everything is working great except that I am unable to send email via SMTP or IMAP from
a remote computer.  Using squirrelmail or telneting to port 25 sends the mail just fine, but no joy
from any email clients.  I get the following messages in /var/log/mail.log:

May 30 18:40:23 www postfix/smtpd[4338]: connect from unknown[10.0.7.14]
May 30 18:40:32 www postfix/smtpd[4338]: warning: unknown[10.0.7.14]: SASL LOGIN
 authentication failed
May 30 18:40:32 www postfix/smtpd[4338]: lost connection after AUTH from unknown
[10.0.7.14]
May 30 18:40:32 www postfix/smtpd[4338]: disconnect from unknown[10.0.7.14]


My main.cf is:

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

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = my.domain.tld
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination =
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

smtpd_banner = $myhostname ESMTP $mail_name
mynetworks_style = host
local_recipient_maps =
delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12
smtpd_helo_restrictions = permit_mynetworks,  warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname,  permit
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_i
f_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pip
elining, permit
# smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client relays.ordb.org, reject_rbl_client 

blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, perm
it_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domai
n, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000,permit
smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
# transport_maps = mysql:/etc/postfix/mysql_tgransport.cf
content_filter = amavis:[127.0.0.1]:10024
#receive_override_options = no_address_mappings
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_data_restrictions = reject_unauth_pipelining


My /etc/postfix/sasl/smtpd.conf file is:

pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passwd: xxxxxx
sql_database: maildb
sql_select: select clear from users where id='%u%r' and enabled = 1


Any other info you need to help solve it?

Thanks in advance.

---

### Post by Ateo on 2007-06-02
I was having issues and I copied your configuration and it all worked with one little tweak....

depending on what username your user uses when authenticating, you may need to change your sql_select statement in smtp.conf... My users are required to use their full email address thus my sql_select statement is as follows:

[CODE]sql_select: SELECT password FROM mailbox WHERE pobox='%u' AND active = '1' AND postfix = 'y' LIMIT 1[/CODE

The %u is all I need since the full email address is required.

I *believe* the statement for usernames without domain is %u@%r but I am not sure...

HTH

---

