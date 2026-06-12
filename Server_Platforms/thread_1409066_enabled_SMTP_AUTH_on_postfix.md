---
title: "enabled SMTP AUTH on postfix"
date: 2010-02-17
forum: Server Platforms
---

### Post by flipybcn on 2010-02-17
Hi.

I've been reading and following the howtos around the help pages at ubuntu, but I'm stuck trying to enable SMTP AUTH and disable plain login.

Also, if anything seems ambigous or wrong, I'd thank if someone can point in the right direction of this configuration.

System is:
Ubuntu 9.04
Postfix 2.5.5.-1.1 with Postfix-ldap module
Dovecot 1.1.11-0ubuntu4.1

Configurations follow:
**dovecot.conf**
```
# 1.1.11: /etc/dovecot/dovecot.conf
# OS: Linux 2.6.28-17-server x86_64 Ubuntu 9.04 ext4
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
ssl_cert_file: /etc/ssl/certs/venus.crt
ssl_key_file: /etc/ssl/private/venus.key
ssl_key_password: 
ssl_parameters_regenerate: 168
ssl_cipher_list: 
ssl_cert_username_field: commonName
ssl_verify_client_cert: no
disable_plaintext_auth: no
verbose_ssl: no
shutdown_clients: yes
nfs_check: yes
version_ignore: no
login_dir: /var/run/dovecot/login
login_executable(default): /usr/lib/dovecot/imap-login
login_executable(imap): /usr/lib/dovecot/imap-login
login_executable(pop3): /usr/lib/dovecot/pop3-login
login_user: postfix
login_greeting: Dovecot ready.
login_log_format_elements: user=<%u> method=%m rip=%r lip=%l %c
login_log_format: %$: %s
login_process_per_connection: yes
login_chroot: yes
login_greeting_capability: no
login_process_size: 64
login_processes_count: 3
login_max_processes_count: 128
login_max_connections: 256
valid_chroot_dirs: /var/spool/dovecot
mail_chroot: 
max_mail_processes: 512
mail_max_userip_connections: 10
verbose_proctitle: no
first_valid_uid: 1000
last_valid_uid: 0
first_valid_gid: 512
last_valid_gid: 0
mail_extra_groups: 
mail_access_groups: 
mail_privileged_group: mail
mail_uid: 
mail_gid: 
mail_location: maildir:/var/spool/dovecot/%n/
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
mail_plugins(default): quota imap_quota
mail_plugins(imap): quota imap_quota
mail_plugins(pop3): quota
mail_plugin_dir(default): /usr/lib/dovecot/modules/imap
mail_plugin_dir(imap): /usr/lib/dovecot/modules/imap
mail_plugin_dir(pop3): /usr/lib/dovecot/modules/pop3
mail_log_prefix: %Us(%u): 
mail_log_max_lines_per_sec: 10
imap_max_line_length: 65536
imap_capability: 
imap_client_workarounds(default): delay-newmail outlook-idle netscape-eoh tb-extra-mailbox-sep
imap_client_workarounds(imap): delay-newmail outlook-idle netscape-eoh tb-extra-mailbox-sep
imap_client_workarounds(pop3): 
imap_logout_format: bytes=%i/%o
pop3_no_flag_updates: no
pop3_enable_last: no
pop3_reuse_xuidl: no
pop3_lock_session: no
pop3_uidl_format: %08Xu%08Xv
pop3_client_workarounds(default): 
pop3_client_workarounds(imap): 
pop3_client_workarounds(pop3): outlook-no-nuls oe-ns-eoh
pop3_logout_format: top=%t/%p, retr=%r/%b, del=%d/%m, size=%s
dict_db_config: 
managesieve_max_line_length: 65536
managesieve_implementation_string: dovecot
sieve_storage: 
sieve: 
auth default:
  mechanisms: plain login
  realms: 
  default_realm: esci.es
  cache_size: 0
  cache_ttl: 3600
  cache_negative_ttl: 3600
  executable: /usr/lib/dovecot/dovecot-auth
  user: root
  chroot: 
  username_chars: abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ01234567890.-_@
  username_translation: 
  username_format: %Lu
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
  passdb:
    driver: ldap
    args: /etc/dovecot/dovecot-ldap.conf
    deny: no
    pass: no
    master: no
  userdb:
    driver: prefetch
    args: 
  userdb:
    driver: passwd
    args: 
  userdb:
    driver: ldap
    args: /etc/dovecot/dovecot-ldap-userdb.conf
  socket:
    type: listen
    client:
      path: /var/spool/postfix/private/auth
      mode: 432
      user: postfix
      group: postfix
    master:
      path: /var/run/dovecot/auth-master
      mode: 384
      user: mail
      group: mail
plugin:
  quota: maildir:User quota
  quota_rule: *:storage=50M
  quota_rule2: Trash:ignore
```

**dovecot-ldap.conf**
```
hosts = ldap2.esci.es, ldap.esci.es
auth_bind = yes
ldap_version = 3
base = ou=Users, dc=esci, dc=es
scope = subtree
user_attrs = homeDirectory=home,uidNumber=uid,gidNumber=gid,mailQuota=quota_rule=*:storage=%$M
user_filter = (&(objectClass=posixAccount)(|(mail=%u)(uid=%u)(uid=%n)))
pass_attrs = uid=user,userPassword=password,\
  homeDirectory=userdb_home,uidNumber=userdb_uid,gidNumber=userdb_gid,mailQuota=userdb_quota_rule=*:storage=%$M
default_pass_scheme = SSHA
```

**main.cf**
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
delay_warning_time = 4h

readme_directory = no

unknown_local_recipient_reject_code = 550

debug_peer_list = 127.0.0.1
debug_peer_level = 1

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/venus.crt
smtpd_tls_key_file = /etc/ssl/private/venus.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

#SASL
smtpd_sasl_auth_enable = no
smtpd_sasl_type = cyrus
smtpd_sasl_path = smtpd
smtpd_sasl_authenticated_header = no
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = 
broken_sasl_auth_clients = no
smtpd_recipient_restrictions = permit_mynetworks, reject_unauth_destination
smtpd_sender_restrictions = 
smtp_use_tls = yes
smtpd_tls_received_header = no
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_auth_only = no
tls_random_source = dev:/dev/urandom

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = jupiter.esci.es
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = esci.es, alum.esci.es, admi.esci.es, prof.esci.es, aalum.esci.es, jupiter.esci.es, localhost.esci.es, localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 10.0.0.0/24 192.168.10.0/24 193.145.56.0/24 84.88.68.64/28
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
relayhost = 193.145.56.10
```

**master.cf**
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
#628      inet  n       -       -       -       -       qmqpd
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
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
```


Thanks for your time and sorry for the big post.

Regards,
Andreas

---

