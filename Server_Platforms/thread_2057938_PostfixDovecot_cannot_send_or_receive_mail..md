---
title: "Postfix/Dovecot cannot send or receive mail."
date: 2012-09-14
forum: Server Platforms
---

### Post by Bcordrey on 2012-09-14
I am attempting to set up an email server using Postfix and Dovecot. Both services are starting fine, but when I log into Squirrelmail to send a test email it won't send, and the response from server error is blank. I tried setting up Thunderbird for the test account, and Thunderbird could not detect the server settings, so I tried to put them in manually, and it still wouldn't work. I'm extremely new to mail servers in Linux, so I have no clue as to what could be going on.

My dovecot.conf -n looks like this:

```

# 2.0.19: /etc/dovecot/dovecot.conf
# OS: Linux 3.2.0-30-generic x86_64 Ubuntu 12.04.1 LTS
auth_mechanisms = plain login
disable_plaintext_auth = no
log_timestamp = "%Y-%m-%d %H:%M:%S "
mail_privileged_group = vmail
passdb {
  args = /etc/dovecot/dovecot-sql.conf
  driver = sql
}
plugin {
  quota = dict:user::file:/var/vmail/%d/%n/.quotausage
  sieve = /var/vmail/%d/%n/.sieve
}
protocols = imap pop3
service auth {
  unix_listener /var/spool/postfix/private/auth {
    group = postfix
    mode = 0660
    user = postfix
  }
  unix_listener auth-userdb {
    group = vmail
    mode = 0600
    user = vmail
  }
  user = root
}
ssl_cert = </etc/postfix/smtpd.cert
ssl_key = </etc/postfix/smtpd.key
userdb {
  args = /etc/dovecot/dovecot-sql.conf
  driver = sql
}
protocol imap {
  mail_plugins = quota imap_quota
}
protocol pop3 {
  mail_plugins = quota
  pop3_uidl_format = %08Xu%08Xv
}
protocol lda {
  mail_plugins = sieve quota
}

```

And my postfix main.cf looks like this:

```


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

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = ns1.moahco.net
alias_maps = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
alias_database = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
myorigin = /etc/mailname
mydestination = ns1.moahco.net, localhost, localhost.localdomain
relayhost =
mynetworks = 127.0.0.0/8 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, proxy:mysql:/etc/postfi$
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /var/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_recipient_access$
smtpd_tls_security_level = may
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf

relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $$
smtpd_sender_restrictions = check_sender_access mysql:/etc/postfix/mysql-virtual_sender.cf
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual_client.cf
smtpd_client_message_rate_limit = 100
maildrop_destination_concurrency_limit = 1
maildrop_destination_recipient_limit = 1
virtual_transport = dovecot
header_checks = regexp:/etc/postfix/header_checks
mime_header_checks = regexp:/etc/postfix/mime_header_checks
nested_header_checks = regexp:/etc/postfix/nested_header_checks
body_checks = regexp:/etc/postfix/body_checks
owner_request_special = no
dovecot_destination_recipient_limit = 1
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings

```

I have TLS set up, and I think that may be what's causing the issue, but I'm not sure. I get SSL_accept errors in my mail log any time I try to send a mail from Squirrelmail, and if I try to send on from an outside host it never shows anything beyond a connection notice, and I never receive the mail.

---

