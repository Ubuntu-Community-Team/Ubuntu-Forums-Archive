---
title: "Dovecot &amp; Postfix broken set-up"
date: 2010-01-21
forum: Server Platforms
---

### Post by ExemplarUbuntu on 2010-01-21
About a week ago, someone or something chewed up the mail set-up on our remote server. There are only a few people using it, it's a new set-up that we will be moving to.

I had to re-install libsasl and do some re-config od dovecot but stil no joy.

In the mail.log we are now seeing this:

```
Jan 21 11:06:07 hs1 postfix/smtpd[6550]: warning: SASL: Connect to private/auth-client failed: Connection refused
Jan 21 11:06:07 hs1 postfix/smtpd[6550]: fatal: no SASL authentication mechanisms
Jan 21 11:06:08 hs1 postfix/master[6379]: warning: process /usr/lib/postfix/smtpd pid 6548 exit status 1
Jan 21 11:06:08 hs1 postfix/master[6379]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan 21 11:06:08 hs1 postfix/master[6379]: warning: process /usr/lib/postfix/smtpd pid 6550 exit status 1

```

This is some of the set-up:

```

>postconf -a
cyrus
dovecot

>postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command =
mailbox_size_limit = 0
mydestination =xx.xx.xxxxx.co.uk, localhost.xx.xxxxx.co.uk, , localhost, xx.xx.xxxxx-xxxxx.com
mydomain = xx.xxxxx-xxxxx.com
myhostname = hs1.xx.xxxxxxxx.co.uk
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 66.66.666.666
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_sasl_auth_enable = yes
smtp_sasl_path = private/auth-client
smtp_sasl_security_options = noanonymous
smtp_sasl_type = dovecot
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = private/auth-client
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom

```


```

sudo dovecot -a
# 1.1.4: /etc/dovecot/dovecot.conf
base_dir: /var/run/dovecot
log_path:
info_log_path:
log_timestamp: %Y-%m-%d %H:%M:%S
syslog_facility: mail
protocols: imap imaps pop3 pop3s
listen: *
ssl_listen:
ssl_disable: no
ssl_ca_file:
ssl_cert_file: /etc/ssl/certs/ssl-cert-snakeoil.pem
ssl_key_file: /etc/ssl/private/ssl-cert-snakeoil.key
ssl_key_password:
ssl_parameters_regenerate: 168
ssl_cipher_list:
ssl_cert_username_field: commonName
ssl_verify_client_cert: no
disable_plaintext_auth: yes
verbose_ssl: no
shutdown_clients: yes
nfs_check: yes
version_ignore: no
login_dir: /var/run/dovecot/login
login_executable(default): /usr/lib/dovecot/imap-login
login_executable(imap): /usr/lib/dovecot/imap-login
login_executable(pop3): /usr/lib/dovecot/pop3-login
login_user: dovecot
login_greeting: Dovecot ready.
login_log_format_elements: user=<%u> method=%m rip=%r lip=%l %c
login_log_format: %$: %s
login_process_per_connection: yes
login_chroot: yes
login_greeting_capability(default): yes
login_greeting_capability(imap): yes
login_greeting_capability(pop3): no
login_process_size: 64
login_processes_count: 3
login_max_processes_count: 128
login_max_connections: 256
valid_chroot_dirs:
mail_chroot:
max_mail_processes: 512
mail_max_userip_connections: 10
verbose_proctitle: no
first_valid_uid: 500
last_valid_uid: 0
first_valid_gid: 1
last_valid_gid: 0
mail_extra_groups:
mail_access_groups:
mail_privileged_group: mail
mail_uid:
mail_gid:
mail_location: maildir:/home/%u/Maildir
mail_cache_fields:
mail_never_cache_fields: imap.envelope
mail_cache_min_mail_count: 0
mailbox_idle_check_interval: 30
mail_debug: no
mail_full_filesystem_access: no
mail_max_keyword_length: 50
mail_save_crlf: no
mmap_disable: no
dotlock_use_excl: yes
fsync_disable: no
mail_nfs_storage: no
mail_nfs_index: no
mailbox_list_index_disable: yes
lock_method: fcntl
maildir_stat_dirs: no
maildir_copy_with_hardlinks: yes
maildir_copy_preserve_filename: no
mbox_read_locks: fcntl
mbox_write_locks: dotlock fcntl
mbox_lock_timeout: 300
mbox_dotlock_change_timeout: 120
mbox_min_index_size: 0
mbox_dirty_syncs: yes
mbox_very_dirty_syncs: no
mbox_lazy_writes: yes
dbox_rotate_size: 2048
dbox_rotate_min_size: 16
dbox_rotate_days: 1
umask: 63
mail_drop_priv_before_exec: no
mail_executable(default): /usr/lib/dovecot/imap
mail_executable(imap): /usr/lib/dovecot/imap
mail_executable(pop3): /usr/lib/dovecot/pop3
mail_process_size: 256
mail_plugins:
mail_plugin_dir(default): /usr/lib/dovecot/modules/imap
mail_plugin_dir(imap): /usr/lib/dovecot/modules/imap
mail_plugin_dir(pop3): /usr/lib/dovecot/modules/pop3
mail_log_prefix: %Us(%u):
mail_log_max_lines_per_sec: 10
imap_max_line_length: 65536
imap_capability:
imap_client_workarounds(default): tb-extra-mailbox-sep
imap_client_workarounds(imap): tb-extra-mailbox-sep
imap_client_workarounds(pop3):
imap_logout_format: bytes=%i/%o
pop3_no_flag_updates: no
pop3_enable_last: no
pop3_reuse_xuidl: no
pop3_lock_session: no
pop3_uidl_format: %08Xu%08Xv
pop3_client_workarounds:
pop3_logout_format: top=%t/%p, retr=%r/%b, del=%d/%m, size=%s
dict_db_config:
managesieve_max_line_length: 65536
managesieve_implementation_string: dovecot
sieve_storage:
sieve:
auth default:
  mechanisms: plain
  realms:
  default_realm:
  cache_size: 0
  cache_ttl: 3600
  cache_negative_ttl: 3600
  executable: /usr/lib/dovecot/dovecot-auth
  user: root
  chroot:
  username_chars: abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ01234567890.-_@
  username_translation:
  username_format:
  master_user_separator:
  anonymous_username: anonymous
  krb5_keytab:
  gssapi_hostname:
  winbind_helper_path: /usr/bin/ntlm_auth
  failure_delay: 2
  verbose: no
  debug: no
  debug_passwords: no
  ssl_require_client_cert: no
  ssl_username_from_cert: no
  ntlm_use_winbind: no
  count: 1
  worker_max_count: 30
  worker_max_request_count: 0
  process_size: 256
  passdb:
    driver: pam
    args:
    deny: no
    pass: no
    master: no
  userdb:
    driver: passwd
    args:
  socket:
    type: listen
    client:
      path: /var/spool/postfix/private/auth-client
      mode: 432
      user: postfix
      group: postfix

```

I am not hugely familiar with the config of this stuff so it is probably a basic mistake. I am wondering of the ssl key configs have gone.

PS

removed some duplicate items from the main.cf and it seems to be working ok again.

---

### Post by ExemplarUbuntu on 2010-01-21
I think I have made some progress, not just twiddling my thumbs here ;-)

Jan 21 14:15:14 hs1 dovecot: Fatal: imap-login: Can't load private key file /etc/ssl/private/my-private-key.com.key: error:06065064:digital envelope routines:EVP_DecryptFinal_ex:bad decrypt

I have tried the passphrase, challenge password and the PEM passphrase but they all give the same error, so I hope it is something else that causes the error.

Thanks for reading.

---

