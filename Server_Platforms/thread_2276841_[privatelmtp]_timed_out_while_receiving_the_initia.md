---
title: "[private/lmtp] timed out while receiving the initial server greeting"
date: 2015-05-05
forum: Server Platforms
---

### Post by robert-kormar on 2015-05-05
Hi, I am so frustrated... I've spent the past 3 days searching the Internet for a solution, found many with essentially the same problem, but each a little different in some way or another, or no answer at all to their question.

I am running Ubuntu Server 14.04.2 with Postfix 2.11.0 and Dovecot 2.2.9.  My setup needs to work for system as well as virtual accounts.  Postfix is receiving mail but storing all mail in the queue.  I decided to change from dovecot-lda to lmtp for delivery.  My virtual accounts info are in a MySQL DB.  I have lmtp configured for unix socket, not inet.  Here is my (apparent) problem(s):

1) I do not understand why mail is not being delivered, none at all yet is being stored in /var/spool/postfix/defer/ ... and deferred/.
2) I do not know how/why this is happening [private/lmtp] timed out while receiving the initial server greeting.
3) My email client (Thunderbird) will no longer login to my accounts - I get a server timeout (error) message.

Here is a current portion of my mail.log:

May  5 14:26:04 host postfix/lmtp[3549]: 482325E782B: to=<sys-user@domain>, relay=host.domain[private/lmtp], delay=21457, delays=20856/301/300/0, dsn=4.4.2, status=deferred (conversation with host.domain[private/lmtp] timed out while receiving the initial server greeting)
May  5 14:26:04 host postfix/lmtp[3550]: 1569C5E7892: to=<sys-user@domain>, relay=host.domain[private/lmtp], delay=17167, delays=16565/302/300/0, dsn=4.4.2, status=deferred (conversation with host.domain[private/lmtp] timed out while receiving the initial server greeting)
May  5 14:26:04 host postfix/cleanup[3631]: E1AFD5E788E: message-id=<20150505122604.E1AFD5E788E@domain>
May  5 14:26:04 host postfix/bounce[3628]: 1569C5E7892: sender delay notification: E1AFD5E788E
May  5 14:26:04 host postfix/qmgr[2716]: E1AFD5E788E: from=<>, size=5275, nrcpt=1 (queue active)
May  5 14:26:04 host postfix/lmtp[3215]: F21A05E052E: to=<sys-user@domain>, relay=domain[private/lmtp], delay=37564, delays=36962/302/300/0, dsn=4.4.2, status=deferred (conversation with host.domain[private/lmtp] timed out while receiving the initial server greeting)

I have replaced my real host and domain names with host and host.domain for obvious reasons.

Here are my postconf -n and doveconf -n :

postconf -n
alias_database = hash:/etc/postfix/aliases.db
alias_maps = hash:/etc/postfix/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
delay_warning_time = 4h
disable_dns_lookups = no
disable_vrfy_command = yes
enable_original_recipient = no
header_checks = regexp:/etc/postfix/header_checks
home_mailbox = Maildir/
html_directory = /usr/share/doc/postfix/html
inet_interfaces = 192.168.x.xxx, 127.0.0.1
mailbox_size_limit = 0
mailbox_transport = lmtp:unix:private/lmtp
masquerade_domains = $myhostname, $mydomain
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
message_size_limit = 20971520
minimal_backoff_time = 1000s
mydestination = $myhostname, $mydomain, localhost, localhost.$mydomain, www.$mydomain, ftp.$mydomain
mydomain = domain
myhostname = host.domain
mynetworks = 192.168.x.0/24, 127.0.0.0/8
mynetworks_style = host
myorigin = $mydomain
queue_directory = /var/spool/postfix
readme_directory = /usr/share/doc/postfix
recipient_delimiter = +
relay_domains = $mydestination
smtp_connect_timeout = 120s
smtp_helo_timeout = 120s
smtp_sasl_type = dovecot
smtp_tls_mandatory_ciphers = medium
smtp_tls_mandatory_protocols = SSLv3, TLSv1
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu/GNU)
smtpd_client_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unknown_client_hostname, reject_unknown_client, reject_unauth_pipelining, reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, sleep 1, reject_rhsbl_client sbl.spamhaus.org, reject_rhsbl_client blackholes.easynet.nl,
smtpd_data_restrictions = reject_unauth_pipelining, reject_multi_recipient_bounce
smtpd_delay_reject = no
smtpd_error_sleep_time = 60
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_hostname, reject_invalid_helo_hostname, reject_unknown_helo_hostname
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_relay_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination reject_unauth_pipelining, reject_non_fqdn_recipient, reject_unknown_recipient_domain, check_policy_service inet:127.0.0.1:10023
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_sender_restrictions = reject_unknown_sender_domain
smtpd_soft_error_limit = 3
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/dovecot/dovecot.pem
smtpd_tls_key_file = /etc/dovecot/private/dovecot.pem
smtpd_tls_loglevel = 1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
unknown_local_recipient_reject_code = 450
unverified_recipient_reject_code = 550
virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf, mysql:/etc/postfix/mysql_virtual_alias_domainaliases_maps.cf
virtual_gid_maps = static:9000
virtual_mailbox_base = /var/mail/vmail
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf, mysql:/etc/postfix/mysql_virtual_mailbox_domainaliases_maps.cf
virtual_transport = lmtp:unix:private/lmtp
virtual_uid_maps = static:9000

doveconf -n
# 2.2.9: /etc/dovecot/dovecot.conf
# OS: Linux 3.13.0-51-generic x86_64 Ubuntu 14.04.2 LTS 
auth_debug = yes
auth_debug_passwords = yes
auth_mechanisms = plain login
auth_verbose = yes
auth_verbose_passwords = plain
base_dir = /var/run/dovecot/
debug_log_path = /var/log/dovecot/dovecot-debug.log
disable_plaintext_auth = no
hostname = host.domain
import_environment = TZ
info_log_path = /var/log/dovecot/dovecot-info.log
listen = 192.168.x.xxx 127.0.0.1
log_path = /var/log/dovecot/dovecot.log
log_timestamp = "%Y-%m-%d %H:%M:%S "
login_greeting = Dovecot ready.
login_log_format_elements = user=<%u> method=%m rip=%r lip=%l mpid=%e %c
login_trusted_networks = 192.168.x.x/24 127.0.0.1
mail_debug = yes
mail_location = maildir:~/Maildir
mail_plugins = virtual quota sieve
managesieve_notify_capability = mailto
managesieve_sieve_capability = fileinto reject envelope encoded-character vacation subaddress comparator-i;ascii-numeric relational regex imap4flags copy include variables body enotify environment mailbox date ihave
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
  driver = pam
}
passdb {
  args = /etc/dovecot/dovecot-sql.conf.ext
  driver = sql
}
plugin {
  sieve = ~/.dovecot.sieve
  sieve_dir = ~/sieve
}
postmaster_address = postmaster@domain
protocols = imap pop3 lmtp sieve
quota_full_tempfail = yes
service auth-worker {
  user = root
}
service auth {
  unix_listener /var/spool/postfix/private/auth-userdb {
    group = postfix
    mode = 0660
    user = postfix
  }
  unix_listener /var/spool/postfix/private/auth {
    group = postfix
    mode = 0660
    user = postfix
  }
  user = $default_internal_user
}
service imap-login {
  inet_listener imap {
    port = 143
  }
  inet_listener imaps {
    port = 993
    ssl = yes
  }
}
service imap {
  process_limit = 1024
}
service lmtp {
  executable = lmtp -L
  process_min_avail = 5
  unix_listener /var/spool/postfix/private/lmtp {
    group = postfix
    mode = 0660
    user = postfix
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
  process_limit = 1024
}
ssl_cert = </etc/dovecot/dovecot.pem
ssl_key = </etc/dovecot/private/dovecot.pem
submission_host = host.domain
userdb {
  driver = passwd
}
userdb {
  args = /etc/dovecot/dovecot-sql.conf.ext
  driver = sql
}
protocol lmtp {
  info_log_path = /var/log/dovecot/dovecot-lmtp.log
  mail_plugins = virtual quota sieve
  postmaster_address = postmaster@domain
}
protocol lda {
  mail_plugins = virtual quota sieve
}

I've of course edited the IP numbers above, even though they are internal.  I'm wondering if it has to do with the submission_host setting, or that I do not have a submission set in my postfix master.cf file. ???

Any help will be greatly appreciated!
Robert

---

