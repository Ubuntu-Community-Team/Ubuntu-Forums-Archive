---
title: "Problem with setting up Dovecot to iniciate"
date: 2016-11-22
forum: Server Platforms
---

### Post by fabioescabrita on 2016-11-22
Hello guys,

I am trying to build a smart host in UNIX like i have done with previous versions of OSX and Server app, but in the most recent version of Server app, they simply have add a postfix to Server app, and with that i am unable to config main.cf as i have done before. So my idea is just to use postfix that come with the system and not the one who have brought with Server app.

Till now i was able to set my system postfix to be communicated through SMTP (with telnet), but unable to connect to IMAP or POP3 ports, so there is something wrong with dovecot, but i have not change anything about mail_transport.

Here you can check my new postfix config at main.cf that i have change some fields to replace by old fields that i had in a previous version where i had just one postfix working (all commented fields belongs to new postfix that came by default in this new version):

```
compatibility_level = 2
queue_directory = /Library/Server/Mail/Data/spool


#command_directory = /Applications/Server.app/Contents/ServerRoot/usr/sbin
command_directory = /usr/sbin


#daemon_directory = /Applications/Server.app/Contents/ServerRoot/usr/libexec/postfix
daemon_directory = /usr/libexec/postfix


data_directory = /Library/Server/Mail/Data/mta
mail_owner = _postfix
unknown_local_recipient_reject_code = 550
debug_peer_level = 2
debugger_command =
     PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin
     ddd $daemon_directory/$process_name $process_id & sleep 5


#sendmail_path = /Applications/Server.app/Contents/ServerRoot/usr/sbin/sendmail
sendmail_path = /usr/sbin/sendmail




#newaliases_path = /Applications/Server.app/Contents/ServerRoot/usr/bin/newaliases
newaliases_path = /usr/bin/newaliases


#mailq_path = /Applications/Server.app/Contents/ServerRoot/usr/bin/mailq
mailq_path = /usr/bin/mailq


setgid_group = _postdrop


#html_directory = /Applications/Server.app/Contents/ServerRoot/usr/share/doc/postfix/html
html_directory = /usr/share/doc/postfix/html


#manpage_directory = /Applications/Server.app/Contents/ServerRoot/usr/share/man
manpage_directory = /usr/share/man


#sample_directory = /Applications/Server.app/Contents/ServerRoot/usr/share/doc/postfix/examples
sample_directory = /usr/share/doc/postfix/examples


#readme_directory = /Applications/Server.app/Contents/ServerRoot/usr/share/doc/postfix
readme_directory = /usr/share/doc/postfix


inet_protocols = all
dovecot_destination_recipient_limit = 1
mailbox_size_limit = 0
smtpd_tls_exclude_ciphers = SSLv2, 3DES, aNULL, ADH, eNULL, EXPORT
tls_random_source = dev:/dev/urandom
imap_submit_cred_file = /Library/Server/Mail/Config/postfix/submit.cred
use_sacl_cache = yes
mydomain_fallback = localhost


#alias_maps = hash:/Library/Server/Mail/Config/postfix/aliases hash:/Library/Server/Mail/Data/listserver/aliases/list_server_aliases


#message_size_limit = 10485760
message_size_limit = 0 #unlimited space


biff = no
mynetworks = 127.0.0.0/8, [::1]/128
smtpd_client_restrictions = permit_mynetworks permit_sasl_authenticated permit
recipient_delimiter = +
smtpd_tls_ciphers = medium


#inet_interfaces = loopback-only
inet_interfaces = loopback-only


smtp_tls_protocols = !SSLv2, !SSLv3
smtp_tls_mandatory_protocols = !SSLv2, !SSLv3
smtpd_tls_protocols = !SSLv2, !SSLv3
smtpd_tls_mandatory_protocols = !SSLv2, !SSLv3
smtp_tls_loglevel = 1
smtp_tls_security_level = may


config_directory = /Library/Server/Mail/Config/postfix
#smtpd_require_virtual_map = yes


virtual_alias_domains = $virtual_alias_maps hash:/Library/Server/Mail/Config/postfix/virtual_domains
virtual_alias_maps = $virtual_maps hash:/Library/Server/Mail/Config/postfix/virtual_users hash:/Library/Server/Mail/Data/listserver/aliases/list_server_virtual
enable_server_options = yes
smtpd_helo_required = yes
smtpd_pw_server_security_options = cram-md5,digest-md5,gssapi
smtpd_tls_CAfile = /etc/certificates/X.chain.pem


#mydomain = X.private
mydomain = X.pt


content_filter = smtp-amavis:[127.0.0.1]:10024
smtpd_tls_cert_file = /etc/certificates/X.cert.pem


#relayhost = 
relayhost = [mail.X.pt]:25
smtp_fallback_relay = [cpanel.ideiasfrescas.pt]:25


smtpd_sasl_auth_enable = yes
smtp_tls_key_file = /etc/certificates/X.key.pem
smtp_tls_cert_file = /etc/certificates/X.cert.pem
smtpd_recipient_restrictions = permit_sasl_authenticated
smtpd_helo_restrictions = reject_non_fqdn_helo_hostname reject_invalid_helo_hostname
smtp_tls_CAfile = /etc/certificates/X.chain.pem
smtpd_enforce_tls = no
smtpd_use_tls = yes
myhostname = remote.X.private
smtpd_use_pw_server = yes
header_checks = pcre:/Library/Server/Mail/Config/postfix/custom_header_checks
smtpd_tls_key_file = /etc/certificates/X.key.pem
recipient_canonical_maps = hash:/Library/Server/Mail/Config/postfix/system_user_maps
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain, X.pt
mailbox_transport = dovecot


meta_directory = /Library/Server/Mail/Config/postfix
#shlib_directory = no


######Edit######
smtp_sasl_security_options =
smtp_sasl_auth_enable = yes
smtp_sender_dependent_authentication = yes


smtp_sasl_password_maps = hash:/Library/Server/Mail/Config/postfix/sasl/passwd


sender_dependent_relayhost_maps = hash:/Library/Server/Mail/Config/postfix/relayhost/maps



```

Dovecot config:

```
remote:~ root# doveconf -n
# 2.2.24 (a82c823): /Library/Server/Mail/Config/dovecot/dovecot.conf
# OS: Darwin 16.1.0 x86_64  hfs
auth_gssapi_hostname = $ALL
auth_mechanisms = cram-md5 digest-md5 gssapi
auth_realms = remote.X.private
auth_socket_path = /var/run/dovecot/auth-userdb
auth_username_format = %n
debug_log_path = /Library/Logs/Mail/mail-debug.log
default_internal_user = _dovecot
default_login_user = _dovenull
first_valid_gid = 6
first_valid_uid = 6
imap_id_log = *
imap_id_send = "name" * "version" *
imap_urlauth_submit_user = submit
info_log_path = /Library/Logs/Mail/mail-info.log
log_path = /Library/Logs/Mail/mail-err.log
login_log_format_elements = user=<%u> method=%m rip=%r lip=%l mpid=%e %c
mail_access_groups = mail
mail_attribute_dict = file:/Library/Server/Mail/Data/attributes/attributes.dict
mail_location = maildir:/Library/Server/Mail/Data/mail/%u
mail_log_prefix = "%s(pid %p user %u): "
mail_plugins = quota zlib acl fts fts_sk
managesieve_notify_capability = mailto
managesieve_sieve_capability = fileinto reject envelope encoded-character vacation subaddress comparator-i;ascii-numeric relational regex imap4flags copy include variables body enotify environment mailbox date ihave
mdbox_rotate_size = 200 M
namespace acl-mailboxes {
  list = children
  location = maildir:/Library/Server/Mail/Data/mail/users/%%u:INDEX=/Library/Server/Mail/Data/mail/shared/%%u
  prefix = shared.%%u.
  separator = .
  subscriptions = no
  type = shared
}
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
namespace list-archives {
  list = children
  location = maildir:/Library/Server/Mail/Data/listserver/messages/archive/lists/%%u:INDEX=/Library/Server/Mail/Data/listserver/messages/archive/shared/%%u
  prefix = archives.%%u.
  separator = .
  subscriptions = no
  type = shared
}
passdb {
  driver = od
}
passdb {
  args = /Library/Server/Mail/Config/dovecot/submit.passdb
  driver = passwd-file
}
plugin {
  acl = vfile:/Library/Server/Mail/Config/dovecot/global-acls:cache_secs=300
  acl_shared_dict = file:/Library/Server/Mail/Data/shared/shared-mailboxes
  fts = sk
  quota = maildir:User quota
  quota_warning = storage=100%% quota-exceeded %u
  sieve = /Library/Server/Mail/Data/rules/%u/dovecot.sieve
  sieve_dir = /Library/Server/Mail/Data/rules/%u
  stats_refresh = 30 secs
  stats_track_cmds = yes
}
postmaster_address = [EMAIL="postmaster@remote.X.privat"]postmaster@remote.X.privat[/EMAIL]e
protocols = imap pop3 lmtp sieve
quota_full_tempfail = yes
service auth {
  extra_groups = _keytabusers
  idle_kill = 15 mins
  unix_listener auth-userdb {
    user = _dovecot
  }
}
service dns_client {
  unix_listener dns-client {
    mode = 0600
  }
}
service imap-login {
  inet_listener imap {
    port = 143
  }
  inet_listener imaps {
    port = 993
    ssl = yes
  }
  service_count = 0
}
service imap {
  client_limit = 5
  process_limit = 200
  service_count = 0
}
service indexer-worker {
  user = _dovecot
}
service lmtp {
  unix_listener lmtp {
    mode = 0600
  }
}
service managesieve-login {
  inet_listener sieve {
    port = 4190
  }
}
service pop3-login {
  inet_listener pop3 {
    port = 110
  }
  inet_listener pop3s {
    port = 995
    ssl = yes
  }
}
service pop3 {
  client_limit = 5
  process_limit = 200
  service_count = 0
}
service quota-exceeded {
  executable = script /Applications/Server.app/Contents/ServerRoot/usr/libexec/dovecot/quota-exceeded.sh
  unix_listener quota-exceeded {
    group = mail
    mode = 0660
    user = _dovecot
  }
  user = _dovecot
}
service quota-warning {
  executable = script /Applications/Server.app/Contents/ServerRoot/usr/libexec/dovecot/quota-warning.sh
  unix_listener quota-warning {
    group = mail
    mode = 0660
    user = _dovecot
  }
  user = _dovecot
}
service stats {
  fifo_listener stats-mail {
    mode = 0600
    user = _dovecot
  }
}
ssl = required
ssl_ca = </etc/certificates/X.chain.pem
ssl_cert = </etc/certificates/X.cert.pem
ssl_cipher_list = ALL:!LOW:!EXP:!aNULL:!ADH:!eNULL:!EXPORT:!3DES:!DES:!aECDH:!DSS:!SEED
ssl_key = </etc/certificates/X.key.pem
ssl_key_path = /etc/certificates/X.key.pem
ssl_protocols = !SSLv2 !SSLv3
userdb {
  args = partition=/Library/Server/Mail/Config/dovecot/partition_map.conf enforce_quotas=no
  driver = od
}
userdb {
  args = /Library/Server/Mail/Config/dovecot/submit.passdb
  driver = passwd-file
}
verbose_proctitle = yes
protocol lmtp {
  mail_plugins = quota zlib acl fts fts_sk sieve
}
protocol lda {
  mail_plugins = quota zlib acl fts fts_sk sieve
}
protocol imap {
  mail_max_userip_connections = 20
  mail_plugins = quota zlib acl fts fts_sk imap_acl imap_quota imap_zlib
}
protocol pop3 {
  mail_max_userip_connections = 6
}
[/QUOTE]

UPDATE1:

My dovecot file is located outside of my Server app:

[QUOTE]remote:~ root# doveconf -n | head -n1
# 2.2.24 (a82c823): /Library/Server/Mail/Config/dovecot/dovecot.conf

```
Anyone?

---

### Post by fabioescabrita on 2016-11-22
So i finally discover how to solve this. I notice that my dovecot was offline, so to turn it online was my main problem. After reading the documentation of it i discover that to start a dovecot server i must user just the syntax "dovecotd". In OSX it a bit different the way that dovecot is called.

---

