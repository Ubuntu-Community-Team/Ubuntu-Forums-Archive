---
title: "Postfix/Dovecot: SMTP not working"
date: 2011-04-11
forum: Server Platforms
---

### Post by jduhls on 2011-04-11
I followed this article:

[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

...and I can't telnet mydomain.com 25. Nothin's there. Can't send email through my own SMTP server. Helps? I opened port 25 via UFW and everything.

Here's my main.cf:

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
content_filter = scan:127.0.0.1:10026
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command =
mailbox_size_limit = 0
myhostname = localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = $myhostname
readme_directory = no
receive_override_options = no_address_mappings
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = private/auth-client
smtpd_sasl_security_options = noplaintext,noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = /etc/postfix/vhosts
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000
```

...and master.cf:

```
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
# AV scan filter (used by content_filter)
scan      unix  -       -       n       -       16      smtp
        -o smtp_send_xforward_command=yes
# For injecting mail back into postfix from the filter
127.0.0.1:10025 inet  n -       n       -       16      smtpd
        -o content_filter=
        -o receive_override_options=no_unknown_recipient_checks,no_header_body_checks
        -o smtpd_helo_restrictions=
        -o smtpd_client_restrictions=
        -o smtpd_sender_restrictions=
        -o smtpd_recipient_restrictions=permit_mynetworks,reject
        -o mynetworks_style=host
        -o smtpd_authorized_xforward_hosts=127.0.0.0/8
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
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

```

...and dovecot.conf:

```
base_dir = /var/run/dovecot/
protocols = imap pop3
disable_plaintext_auth = yes
shutdown_clients = yes
log_path = /var/log/dovecot
info_log_path = /var/log/dovecot.info
log_timestamp = "%Y-%m-%d %H:%M:%S "
#ssl_disable = yes
ssl = no
login_dir = /var/run/dovecot/login
login_chroot = yes
login_user = dovecot
login_greeting = Dovecot ready.
mail_location = maildir:/home/vmail/%d/%n
mmap_disable = no
valid_chroot_dirs = /var/spool/vmail
protocol imap {
  login_executable = /usr/lib/dovecot/imap-login
  mail_executable = /usr/lib/dovecot/imap
}
protocol pop3 {
  login_executable = /usr/lib/dovecot/pop3-login
  mail_executable = /usr/lib/dovecot/pop3
  pop3_uidl_format = %08Xu%08Xv
}
#auth_debug_passwords = yes
mail_debug = yes
auth_executable = /usr/lib/dovecot/dovecot-auth
auth_verbose = yes
auth default {
  mechanisms = plain cram-md5
  passdb passwd-file {
    args = /etc/dovecot/passwd
  }
  userdb passwd-file {
    args = /etc/dovecot/users
  }
  user = root
  socket listen {
    client {
      # The client socket is generally safe to export to everyone. Typical use
      # is to export it to your SMTP server so it can do SMTP AUTH lookups
      # using it.
      path = /var/spool/postfix/private/auth-client
      mode = 0660
      user = postfix
      group = postfix
    }
  }
}
```

...but here's telnet from the server to itself on 25:

```
root@webserver:/etc/postfix# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 localhost ESMTP Postfix (Ubuntu)
```

---

### Post by jduhls on 2011-04-11
Ha..duh.

Changed smtp port from default 25 to another less defaulty number after reading many "ISP's block port 25". I can now send email thru my SMTP server no problem.

---

