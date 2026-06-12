---
title: "Postfix + dovecot = frustration"
date: 2012-12-23
forum: Server Platforms
---

### Post by garfieldairlines on 2012-12-23
Hello,

I have installed postfix and dovecot on ubuntu server and  after hours of trying different tutorials and suggestions I just can't  manage to make a mail server

/etc/postfix/main.cf
```

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

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.garfieldairlines.net
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
mydestination = $myhostname, localhost, localhost.localdomain, localhost.$myhostname
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
#inet_protocols = all
home_mailbox = Maildir/

smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = 
broken_sasl_auth_clients = yes

smtpd_sender_restrictions = permit_mynetworks, reject_sender_login_mismatch, permit_sasl_authenticated

smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
inet_protocols = all
virtual_alias_domains = 
myorigin = mail.garfieldairlines.net
mydomain = garfieldairlines.net
mynetworks_style = subnet
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_reject_unlisted_recipient = yes
smtpd_reject_unlisted_sender = yes
delay_warning_time = 0h
maximal_queue_lifetime = 1d
bounce_queue_lifetime = 1d
proxy_read_maps  = $canonical_maps $lmtp_generic_maps $local_recipient_maps  $mydestination $mynetworks $recipient_bcc_maps $recipient_canonical_maps  $relay_domains $relay_recipient_maps $relocated_maps $sender_bcc_maps  $sender_canonical_maps $smtp_generic_maps $smtpd_sender_login_maps  $transport_maps $virtual_alias_domains $virtual_alias_maps  $virtual_mailbox_domains $virtual_mailbox_maps  $smtpd_sender_restrictions
smtp_data_init_timeout = 240s
smtp_data_xfer_timeout = 600s
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks,permit_sasl_authenticated, check_helo_access pcre:/etc/postfix/helo_access.pcre
queue_run_delay = 300s
minimal_backoff_time = 300s
maximal_backoff_time = 4000s
enable_original_recipient = no
disable_vrfy_command = yes
allow_min_user = no
message_size_limit = 15728640
virtual_minimum_uid = 1001
virtual_uid_maps = static:1001
virtual_gid_maps = static:1001
virtual_mailbox_base = /var/vmail
transport_maps = proxy:mysql:/etc/postfix/mysql/transport_maps_user.cf, proxy:mysql:/etc/postfix/mysql/transport_maps_domain.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql/virtual_mailbox_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql/virtual_mailbox_maps.cf
virtual_alias_maps  = proxy:mysql:/etc/postfix/mysql/virtual_alias_maps.cf,  proxy:mysql:/etc/postfix/mysql/domain_alias_maps.cf,  proxy:mysql:/etc/postfix/mysql/catchall_maps.cf,  proxy:mysql:/etc/postfix/mysql/domain_alias_catchall_maps.cf
sender_bcc_maps  = proxy:mysql:/etc/postfix/mysql/sender_bcc_maps_user.cf,  proxy:mysql:/etc/postfix/mysql/sender_bcc_maps_domain.cf
recipient_bcc_maps  = proxy:mysql:/etc/postfix/mysql/recipient_bcc_maps_user.cf,  proxy:mysql:/etc/postfix/mysql/recipient_bcc_maps_domain.cf
relay_domains = $mydestination, proxy:mysql:/etc/postfix/mysql/relay_domains.cf
smtpd_sender_login_maps = proxy:mysql:/etc/postfix/mysql/sender_login_maps.cf
smtpd_sasl_authenticated_header = no
smtpd_end_of_data_restrictions = check_policy_service inet:127.0.0.1:10031
smtpd_tls_security_level = may
smtpd_tls_loglevel = 1
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
tls_random_source = dev:/dev/urandom
mailbox_command = /usr/lib/dovecot/deliver
virtual_transport = dovecot
dovecot_destination_recipient_limit = 1
smtpd_sasl_type = dovecot
smtpd_sasl_path = ./dovecot-auth
content_filter = smtp-amavis:[127.0.0.1]:10024
smtp-amavis_destination_recipient_limit = 1
smtp_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s

```dovecot.conf
```


# Listen addresses.
#   - '*' means all available IPv4 addresses.
#   - '[::]' means all available IPv6 addresses.
# Listen on all available addresses by default
listen = *, [::]

#base_dir = /var/run/dovecot

# Enabled mail protocols.
protocols = pop3 imap sieve

# User/group who owns the message files:
mail_uid = 1001
mail_gid = 1001

# Assign uid to virtual users.
first_valid_uid = 1001
last_valid_uid = 1001

# Logging. Reference: http://wiki2.dovecot.org/Logging
log_path = /var/log/dovecot.log
mail_debug = no
auth_verbose = no
auth_debug = no
auth_debug_passwords = no
# Possible values: no, plain, sha1.
auth_verbose_passwords = no

# SSL: Global settings.
# Refer to wiki site for per protocol, ip, server name SSL settings:
# http://wiki2.dovecot.org/SSL/DovecotConfiguration
ssl = required
verbose_ssl = no
ssl_cert = </etc/ssl/certs/iRedMail_CA.pem
ssl_key = </etc/ssl/private/iRedMail.key

# With disable_plaintext_auth=yes AND ssl=required, STARTTLS is mandatory.
# Set disable_plaintext_auth=no AND ssl=yes to allow plain password transmitted
# insecurely.
disable_plaintext_auth = yes
# Allow plain text password per IP address/net
#remote 192.168.0.0/24 {
#   disable_plaintext_auth = no
#}

# Mail location and mailbox format.
mail_location = maildir:/%Lh/Maildir/:INDEX=/%Lh/Maildir/

# Authentication related settings.
# Append this domain name if client gives empty realm.
auth_default_realm = 

# Authentication mechanisms.
auth_mechanisms = PLAIN LOGIN

service auth {
    unix_listener /var/spool/postfix/dovecot-auth {
        user = postfix
        group = postfix
        mode = 0666
    }
    unix_listener auth-master {
        user = vmail
        group = vmail
        mode = 0666
    }
    unix_listener auth-userdb {
        user = vmail
        group = vmail
        mode = 0660
    }
}

# Virtual mail accounts.
userdb {
    args = /etc/dovecot/dovecot-mysql.conf
    driver = sql
}
passdb {
    args = /etc/dovecot/dovecot-mysql.conf
    driver = sql
}

plugin {
    auth_socket_path = /var/run/dovecot/auth-master

    quota = dict:user::proxy::quotadict
    quota_rule = *:storage=1G
    #quota_rule2 = *:messages=0
    #quota_rule3 = Trash:storage=1G
    #quota_rule4 = Junk:ignore

    # Quota warning.
    # If user suddenly receives a huge mail and the quota jumps from
    # 85% to 95%, only the 95% script is executed.
    quota_warning = storage=85%% quota-warning 85 %u
    quota_warning2 = storage=90%% quota-warning 90 %u
    quota_warning3 = storage=95%% quota-warning 95 %u

    # Plugin: autocreate. Create and subscribe to default IMAP folders.
    autocreate = INBOX
    autocreate2 = Sent
    autocreate3 = Trash
    autocreate4 = Drafts
    autocreate5 = Junk
    autosubscribe = INBOX
    autosubscribe2 = Sent
    autosubscribe3 = Trash
    autosubscribe4 = Drafts
    autosubscribe5 = Junk

    # Plugin: expire.
    expire = Trash 7 Trash/* 7 Junk 30
    expire_dict = proxy::expire

    # ACL and share folder
    acl = vfile
    acl_shared_dict = proxy::acl

    # By default Dovecot doesn't allow using the IMAP "anyone" or
    # "authenticated" identifier, because it would be an easy way to spam
    # other users in the system. If you wish to allow it,
    #acl_anyone = allow

    # Pigeonhole managesieve service.
    # Reference: http://wiki2.dovecot.org/Pigeonhole/Sieve/Configuration
    # Per-user sieve settings.
    sieve_dir = /%Lh/sieve
    sieve = /%Lh/sieve/dovecot.sieve

    # Global sieve settings.
    sieve_global_dir = /var/vmail/sieve
    sieve_global_path = /var/vmail/sieve/dovecot.sieve
    #sieve_before =
    #sieve_after =
}

service quota-warning {
    executable = script /usr/local/bin/dovecot-quota-warning.sh
    unix_listener quota-warning {
        user = vmail
        group = vmail
        mode = 0660
    }
}

service dict {
    unix_listener dict {
        mode = 0660
        user = vmail
        group = vmail
    }
}

dict {
    expire = db:/var/lib/dovecot/expire/expire.db
    quotadict = mysql:/etc/dovecot/dovecot-used-quota.conf
    acl = mysql:/etc/dovecot/dovecot-share-folder.conf
}

protocol lda {
    # Reference: http://wiki2.dovecot.org/LDA
    mail_plugins = quota sieve autocreate
    auth_socket_path = /var/run/dovecot/auth-master
    log_path = /var/log/sieve.log
    lda_mailbox_autocreate = yes
    postmaster_address = root
}
protocol imap {
    imap_client_workarounds = tb-extra-mailbox-sep
    login_greeting_capability = yes
    mail_plugins = quota imap_quota autocreate
}
protocol pop3 {
    mail_plugins = quota
    pop3_client_workarounds = outlook-no-nuls oe-ns-eoh
    pop3_uidl_format = %08Xu%08Xv
}

namespace {
    type = private
    separator = /
    prefix =
    #location defaults to mail_location.
    inbox = yes
}

namespace {
    type = shared
    separator = /
    prefix = Shared/%%u/
    location = maildir:/%%Lh/Maildir/:INDEX=/%%Lh/Maildir/Shared/%%u
    # this namespace should handle its own subscriptions or not.
    subscriptions = yes
    list = children
}

# Public mailboxes.
# Refer to Dovecot wiki page for more details:
# http://wiki2.dovecot.org/SharedMailboxes/Public
#namespace {
#    type = public
#    separator = /
#    prefix = Public/
#
#    # CONTROL=: Mark this public folder as read-only mailbox
#    # INDEX=: Per-user \Seen flag
#    location = maildir:/var/vmail/public/:CONTROL=~/Maildir/public:INDEX=~/Maildir/public
#
#    # Allow users to subscribe to the public folders.
#    subscriptions = yes
#}

auth default {
mechanisms = plain login
passdb pam {
}
userdb passwd {
}
socket listen {
client {
path = /var/spool/postfix/private/auth
mode = 0660
user = postfix
group = postfix
}
}
}

protocol imap {
     listen = *:143
     ssl_listen = *:993
}

```tail /var/log/mail.log
```

Dec  23 13:58:40 stock postfix/smtpd[12363]: warning: TLS library problem:  12363:error:2006D080:BIO routines:BIO_new_file:no such  file:bss_file.c:172:
Dec 23 13:58:40 stock postfix/smtpd[12363]:  warning: TLS library problem: 12363:error:0B084002:x509 certificate  routines:X509_load_cert_crl_file:system lib:by_file.c:274:
Dec 23 13:58:40 stock postfix/smtpd[12363]: connect from pavot.april.org[86.65.39.24]
Dec 23 13:58:40 stock postfix/smtpd[12363]: warning: SASL: Connect to ./dovecot-auth failed: Connection refused
Dec 23 13:58:40 stock postfix/smtpd[12363]: fatal: no SASL authentication mechanisms
Dec 23 13:58:41 stock postfix/master[8489]: warning: process /usr/lib/postfix/smtpd pid 12363 exit status 1
Dec 23 13:58:41 stock postfix/master[8489]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec 23 14:00:21 stock postfix/anvil[12182]: statistics: max connection rate 1/60s for (smtp:88.190.228.84) at Dec 23 13:54:35
Dec 23 14:00:21 stock postfix/anvil[12182]: statistics: max connection count 1 for (smtp:88.190.228.84) at Dec 23 13:54:35
Dec 23 14:00:21 stock postfix/anvil[12182]: statistics: max cache size 2 at Dec 23 13:56:38

```The  only hint I can give is that thunderbird says that connexion is  refused. I know the config files are a mess. Thanks in advance for your  help.

---

### Post by craigp84 on 2012-12-24
It's likely all the listed log complaints are related to the same problem from the first 2 lines:

```

Dec  23 13:58:40 stock postfix/smtpd[12363]: warning: TLS library problem:  12363:error:2006D080:BIO routines:BIO_new_file:no such  file:bss_file.c:172:
Dec 23 13:58:40 stock postfix/smtpd[12363]:  warning: TLS library problem: 12363:error:0B084002:x509 certificate  routines:X509_load_cert_crl_file:system lib:by_file.c:274:
```

Are there any other log entries before these 2? From these messages it's most likely that a path you've specified or a default path in the main.cf is pointing to a wrong location or if all files are valid / visible then the file cannot be read by the user smtpd is running as (could be due to permissions, attributes, App Armour etc.).

---

