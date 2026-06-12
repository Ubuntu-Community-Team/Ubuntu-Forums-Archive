---
title: "Postfix 2.7 Dovecot v2  sasl mysql fatal: no SASL authentication mechanisms"
date: 2013-04-02
forum: Server Platforms
---

### Post by abcinc on 2013-04-02
I keep getting 
Apr  2 19:27:23 web5 postfix/smtpd[4685]: warning: SASL: Connect to /usr/lib/dovecot/dovecot-auth failed: No such file or directory
Apr  2 19:27:23 web5 postfix/smtpd[4685]: fatal: no SASL authentication mechanisms
Apr  2 19:27:24 web5 postfix/master[3021]: warning: process /usr/lib/postfix/smtpd pid 4685 exit status 1
Apr  2 19:27:24 web5 postfix/master[3021]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

in /var/log/mail.log

file /usr/lib/dovecot/dovecot-auth exists and is mode 660

Postfig -a
cyrus
dovecot

dovecot -n
# 2.1.7: /usr/local/etc/dovecot/dovecot.conf
# OS: Linux 2.6.32-45-generic-pae i686 Ubuntu 10.04.4 LTS ext4
default_login_user = mail user
disable_plaintext_auth = no
listen = *
mail_gid = mail
mail_location = maildir:/var/mail/%d/%n
mail_uid = mail
namespace inbox {
  inbox = yes
  location =
  mailbox Drafts {
    special_use = \Drafts
  }
  mailbox Junk {
    special_use = \Junk
  }
  mailbox Sent {
    special_use = \Sent
  }
  mailbox "Sent Messages" {
    special_use = \Sent
  }
  mailbox Trash {
    special_use = \Trash
  }
  prefix =
}
passdb {
  args = /usr/local/etc/dovecot/dovecot-sql.conf
  driver = sql
}
passdb {
  driver = pam
}
protocols = imap pop3
service auth {
  unix_listener /var/spool/postfix/private/auth {
    group = postfix
    mode = 0660
    user = postfix
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
ssl = no
ssl_cert = </etc/ssl/private/mail5.abcsitehosting.com.cert
ssl_key = </etc/ssl/private/mail5.abcsitehosting.com.key
userdb {
  args = /usr/local/etc/dovecot/dovecot-sql.conf
  driver = sql
}
userdb {
  driver = passwd
}

postfix conf main.conf

mydestination = localhost, localhost.localdomain
myhostname = mail5.domain.com
mydomain = domain.com
biff = no
append_dot_mydomain = no
readme_directory = no
mynetworks = 127.0.0.0/8
mynetworks_style = host
mailbox_size_limit = 0
recipient_delimiter = +
message_size_limit = 0
relay_domains = $mydomain
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_local_domain = $myhostname
 queue_directory = /var/spool/postfix
smtpd_helo_required = yes
disable_vrfy_command = yes
alias_maps = hash:/etc/aliases
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf,  proxy:mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /var/mail
virtual_minimum_uid = 500
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_transport = dovecot
virtual_mailbox_limit = 0
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-dovecot-postfix.conf -n -m "${EXTENSION}"
home_mailbox = Maildir/
smtpd_tls_loglevel = 3
debug_peer_level = 3
smtpd_recipient_restrictions = 
 permit_mynetworks, 
 permit_sasl_authenticated, 
 reject_unauth_destination,
 permit
                             
smtpd_sasl_type = dovecot
smtpd_sasl_path = /usr/lib/dovecot/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_tls_loglevel = 4
broken_sasl_auth_clients = yes
# virtual_alias_domains = 
# smtpd_tls_security_level = may
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
relay_domains = proxy:mysql:/etc/postfix/mysql-virtual_relaydomains.cf
virtual_create_maildirsize = yes
virtual_maildir_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
maildrop_destination_concurrency_limit = 1
maildrop_destination_recipient_limit = 1
header_checks = regexp:/etc/postfix/header_checks
mime_header_checks = regexp:/etc/postfix/mime_header_checks
nested_header_checks = regexp:/etc/postfix/nested_header_checks
body_checks = regexp:/etc/postfix/body_checks
# smtpd_tls_security_level = none
ignore_mx_lookup_error = yes

Please help
Thanks

---

### Post by abcinc on 2013-04-10
Anyone reading this?  Please help with this.
Thank You

---

