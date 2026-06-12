---
title: "postfix and dovecot virtual domains and users problems"
date: 2013-01-11
forum: Server Platforms
---

### Post by troypiggo on 2013-01-11
I'm trying to set up postfix and dovecot serving a couple of virtual domains and users.  The incoming emails are coming in fine to the virtual domains' mailboxes, so I'm pretty sure the postfix smtp side of things is fine.  I can open the mails on the server with mutt.

Having trouble with the authentication for remote users.  eg trying to set up Thunderbird accounts.  Need your help as I'm missing something I can't see.

```
# postconf -n
alias_database = hash:/etc/aliases                                                                                      
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = smtp-amavis:[127.0.0.1]:10024
delay_warning_time = 4h
disable_vrfy_command = yes
header_checks = pcre:/etc/postfix/header_checks.pcre
home_mailbox = Maildir/
inet_interfaces = all
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-mail-stack-delivery.conf -m "${EXTENSION}"
mailbox_size_limit = 0
mydestination = dove.XYZ.local, dove, dove.XYZ.com, localhost.localdomain, localhost, XYZ.dyndns.org
mydomain = XYZ.dyndns.org
myhostname = XYZ.dyndns.org
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.0.0/22
mynetworks_style = host
myorigin = /etc/mailname
policy-spf_time_limit = 3600s
postscreen_dnsbl_sites = list.dnswl.org*-5
readme_directory = no
receive_override_options = no_address_mappings
recipient_delimiter = _
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_client_restrictions = permit_mynetworks, reject_invalid_hostname
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, reject_invalid_hostname
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, permit_dnswl_client list.dnswl.org, reject_rbl_client zen.spamhaus.org, reject_rbl_client bl.spamcop.net, check_policy_service inet:127.0.0.1:10023
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_sender_restrictions = permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_tls_mandatory_ciphers = high
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
virtual_alias_maps = hash:/etc/postfix/virtual
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/mail/vhosts
virtual_mailbox_domains = XYZ.com ABC.com.au
virtual_mailbox_maps = hash:/etc/postfix/vmailbox
virtual_minimum_uid = 100
virtual_uid_maps = static:5000 
```

```
# doveconf -n
# 2.0.19: /etc/dovecot/dovecot.conf                                                                                     
# OS: Linux 3.2.0-35-virtual x86_64 Ubuntu 12.04.1 LTS ext4
auth_verbose = yes
disable_plaintext_auth = no
mail_location = maildir:/var/mail/vhosts/%d/%n
managesieve_notify_capability = mailto
managesieve_sieve_capability = fileinto reject envelope encoded-character vacation subaddress comparator-i;ascii-numeric relational regex imap4flags copy include variables body enotify environment mailbox date ihave
passdb {
  driver = pam
}
passdb {
  driver = pam
}
passdb {
  args = /etc/dovecot/passwd
  driver = passwd-file
}
plugin {
  sieve = ~/.dovecot.sieve
  sieve_dir = ~/sieve
}
protocols = imap
service auth {
  unix_listener /var/spool/postfix/private/dovecot-auth {
    group = postfix
    mode = 0660
    user = postfix
  }
}
ssl = no
ssl_cert = </etc/ssl/certs/dovecot.pem
ssl_cipher_list = ALL:!LOW:!SSLv2:ALL:!aNULL:!ADH:!eNULL:!EXP:RC4+RSA:+HIGH:+MEDIUM
ssl_key = </etc/ssl/private/dovecot.pem
userdb {
  driver = passwd
}
userdb {
  driver = passwd
}
userdb {
  args = uid=vmail gid=vmail home=/var/mail/vhosts/%d/%n
  driver = static
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
  postmaster_address = postmaster@XYZ.dyndns.org
  quota_full_tempfail = yes
  rejection_reason = Your message to <%t> was automatically rejected:%n%r
} 
```

---

### Post by vasiliscnisrok on 2013-01-11
try
```
telnet IP-mail-server 110
```

verify mailserver
use by example

USER [email]username@domain.com[/email]
PASS password
LIST
QUIT

---

### Post by troypiggo on 2013-01-11
Hmmm.  If I 'netcat -zv localhost 25' the connection succeeds but ports 110 and 993 refused.  It's not a firewall issue.  Must be dovecot.  Any ideas based on the above config?

---

### Post by vasiliscnisrok on 2013-01-14
verify log /var/log/dovecot.log
and give me
```
sudo netstat -nap4|grep LIS
```

---

