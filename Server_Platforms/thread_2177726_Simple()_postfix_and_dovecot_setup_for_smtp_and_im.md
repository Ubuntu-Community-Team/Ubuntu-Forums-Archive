---
title: "Simple(?) postfix and dovecot setup for smtp and imap."
date: 2013-09-30
forum: Server Platforms
---

### Post by snelkat on 2013-09-30
so, here goes.
i'm trying to setup a simple mail server for my domains, smtp and imap.
i'm starting from the beginning;

# apt-get install postfix dovecot-postfix
i do the basic config, no config file editing yet.
try out the account in thunderbird but it fails.
so i guess i'll have to turn on some debug logging in dovecot to see what fails;
auth_verbose = yes in 10-logging.conf

i get this in the mail.log:
Sep 30 09:34:10 do dovecot: imap-login: Disconnected (no auth attempts): rip=3.3.3.3, lip=1.1.1.1, TLS: SSL_read() failed: error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca: SSL alert number 48

i've generated certificates using this method: [https://workaround.org/ispmail/squeeze/ssl-certificates](https://workaround.org/ispmail/squeeze/ssl-certificates)

this should be some pretty basic out-of-the-box-mailserver setup.
i've read somewhere that thunderbird and dovecot doesn't play nice.
but i've once gotten it to function, i just don't remember what i did.

anyone got any ideas?

here's my config (which is pretty much out of the box):
```

# postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-mail-stack-delivery.conf -m "${EXTENSION}"
mailbox_size_limit = 0
mydestination = mydomain.com, localhost
myhostname = do.example.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_sender_restrictions = reject_unknown_sender_domain
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/ssl/certs/postfix.pem
smtpd_tls_key_file = /etc/ssl/private/postfix.pem
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom



# doveconf -n
# 2.0.19: /etc/dovecot/dovecot.conf
# OS: Linux 3.2.0-23-virtual x86_64 Ubuntu 12.04.3 LTS
auth_verbose = yes
mail_location = maildir:~/Maildir
managesieve_notify_capability = mailto
managesieve_sieve_capability = fileinto reject envelope encoded-character vacation subaddress comparator-i;ascii-numeric relational regex imap4flags copy include variables body enotify environment mailbox date ihave
passdb {
  driver = pam
}
plugin {
  sieve = ~/.dovecot.sieve
  sieve_dir = ~/sieve
}
protocols = imap pop3 sieve
service auth {
  unix_listener /var/spool/postfix/private/dovecot-auth {
    group = postfix
    mode = 0660
    user = postfix
  }
}
ssl_cert = </etc/ssl/certs/dovecot.pem
ssl_key = </etc/ssl/private/dovecot.pem
userdb {
  driver = passwd
}
protocol imap {
  imap_client_workarounds = delay-newmail
  mail_max_userip_connections = 10
}
protocol pop3 {
  mail_max_userip_connections = 10
  pop3_client_workarounds = outlook-no-nuls oe-ns-eoh
}
protocol lda {
  deliver_log_format = msgid=%m: %$
  mail_plugins = sieve
  postmaster_address = postmaster
  quota_full_tempfail = yes
  rejection_reason = Your message to <%t> was automatically rejected:%n%r
}

```

---

### Post by snelkat on 2013-09-30
so, i got it to work.
i imported the certificates in thunderbird and enabled submission for postfix for smtp auth.

---

