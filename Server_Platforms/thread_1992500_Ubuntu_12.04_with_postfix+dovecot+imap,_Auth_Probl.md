---
title: "Ubuntu 12.04 with postfix+dovecot+imap, Auth Problems?"
date: 2012-05-31
forum: Server Platforms
---

### Post by delphius on 2012-05-31
I have some issues regarding AUTH.

pop3/login/pop3-auth, sending, login, getting messages works fine.

But when trying to AUTH with IMAP I am getting some problems.

I am trying to IMAP auth with Thunderbird and Trustedbird,
but Thunderbird only nags about 'is the username or password wrong?"

When trying everything on [http://wiki.dovecot.org/TestInstallation](http://wiki.dovecot.org/TestInstallation)
, such as telnet-login -> b select inbox and openssl s_client -connect imap.example.com:143 -starttls imap everything works and the user can IMAP log-in.

But not with Thunderbird and Trustedbird.
POP3 works though.

### <DOVECOT CONF> #####
This is the output from dovecot -n:
# 2.0.19: /etc/dovecot/dovecot.conf
# OS: Linux 3.2.0-23-generic-pae i686 Ubuntu 12.04 LTS ext4
auth_debug = yes
auth_mechanisms = plain login
auth_verbose = yes
first_valid_uid = 150
last_valid_uid = 150
mail_debug = yes
mail_gid = mail
mail_location = maildir:/var/vmail/%d/%n
mail_uid = vmail
passdb {
  args = /etc/dovecot/dovecot-sql.conf.ext
  driver = sql
}
protocols = pop3 imap
service auth-worker {
  unix_listener auth-worker {
    user = dovecot
  }
}
service auth {
  unix_listener /var/spool/postfix/private/auth {
    group = postfix
    mode = 0666
    user = postfix
  }
  unix_listener auth-userdb {
    group = mail
    mode = 0600
    user = vmail
  }
}
service imap-login {
  inet_listener imap {
    port = 143
  }
}
service pop3-login {
  inet_listener pop3 {
    port = 110
  }
}
ssl_cert = </etc/ssl/certs/dovecot.pem
ssl_key = </etc/ssl/private/dovecot.pem
userdb {
  args = /etc/dovecot/dovecot-sql.conf.ext
  driver = sql
}
protocol imap {
  imap_client_workarounds = tb-extra-mailbox-sep
}

#### </DOVECOT CONF> #####


#### <POSTFIX CONF> #####
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
disable_vrfy_command = yes
dovecot_destination_recipient_limit = 1
enable_original_recipient = no
header_checks = regexp:/etc/postfix/header_checks
inet_interfaces = all
inet_protocols = ipv4
mailbox_size_limit = 0
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination = mail.specus.net, localhost, lion.specus.net
myhostname = mail.specus.net
mynetworks = 127.0.0.0/8 10.0.0.0/24
mynetworks_style = host
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
smtp_helo_timeout = 60s
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf, mysql:/etc/postfix/mysql_virtual_alias_domainaliases_maps.cf
virtual_gid_maps = static:8
virtual_mailbox_base = /var/vmail
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf, mysql:/etc/postfix/mysql_virtual_mailbox_domainaliases_maps.cf
virtual_transport = dovecot
virtual_uid_maps = static:150

####</POSTCONF CODE> ######


What could be wrong when POP3 works, but not IMAP on client side? 


Please help

- Delphius

---

### Post by elico on 2012-05-31
what are the settings in thunderbird? it also can be an antivirus if you have one.

---

### Post by delphius on 2012-06-03
> **elico said:**
> what are the settings in thunderbird? it also can be an antivirus if you have one.

You were perfectly right! Shutted down the antivirus, and it auth'd with the imap service. And at the same time Thunderbird asked for permission to use a cert. That option had not been available earlier. Strange things


Thank you very much for the tip!

---

