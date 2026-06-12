---
title: "postfix+dovecot with LDAP backend: not delivering mail"
date: 2009-08-18
forum: Server Platforms
---

### Post by flipybcn on 2009-08-18
Hi!
I want to configure a mail server with postfix and dovecot, and using another server to do the auth thru a LDAP tree.
I've been following the community guide: [https://help.ubuntu.com/community/Postfix/DovecotLDAP](https://help.ubuntu.com/community/Postfix/DovecotLDAP)

I do not want to have virtual domains nor aliases, I just want postfix and dovecot to auth using LDAP, and store the mail under a fixed path.

I can do the login using LDAP and the maildir files are created for each user, but when I try to send a mail to a user it is not delivered.
I've googled around and tried several things, but nothing works.
I think my main problem is that I'm using the mail attribute to do the login but the uid to store the mail.

dovecot.conf
```
protocols = imap
disable_plaintext_auth = no
log_timestamp = "%Y-%m-%d %H:%M:%S "
login_user = postfix
   mail_location = maildir:/var/spool/dovecot/%n
mail_privileged_group = mail
mail_full_filesystem_access = no
mail_debug = yes
mail_log_prefix = "%Us(%u): "
protocol imap {
  login_executable = /usr/lib/dovecot/imap-login
  mail_executable = /usr/lib/dovecot/imap
  mail_plugins = quota imap_quota
  imap_client_workarounds = delay-newmail outlook-idle netscape-eoh tb-extra-mailbox-sep
}
protocol pop3 {
  pop3_uidl_format = %08Xu%08Xv
  mail_plugins = quota
  pop3_client_workarounds = outlook-no-nuls oe-ns-eoh
}
protocol managesieve {
  sieve=~/.dovecot.sieve
  sieve_storage=~/sieve
}
protocol lda {
  postmaster_address = root@esci.es
  mail_plugins = quota
  sendmail_path = /usr/lib/sendmail
}
auth_default_realm = esci.es
auth_username_format = %Lu
auth default {
  mechanisms = plain login
  passdb pam {
  }
  passdb ldap {
    args = /etc/dovecot/dovecot-ldap.conf
  }
  userdb passwd {
  }
  userdb ldap {
    args = /etc/dovecot/dovecot-ldap.conf
  }
  user = root
  socket listen {
    master {
      path = /var/run/dovecot/auth-master
    }
  }
}
dict {
}
plugin {
  quota = maildir
  quota_rule = *:storage=50M
}
```

dovecot-ldap.conf
```
hosts = ldap.esci.es
auth_bind = yes
ldap_version = 3
base = ou=Users, dc=esci, dc=es
scope = subtree
user_attrs = homeDirectory=home,uidNumber=uid,gidNumber=gid
user_filter = (&(objectClass=posixAccount)(|(uid=%u)(mail=%u)))
pass_attrs = uid=user,userPassword=password
pass_filter = (&(objectClass=posixAccount)(|(uid=%u)(mail=%u)))
default_pass_scheme = SSHA
```

main.cf
```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h

readme_directory = no

unknown_local_recipient_reject_code = 550

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = jupiter.esci.es
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = esci.es, jupiter.esci.es, localhost.esci.es, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 10.0.0.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

virtual_mailbox_base = /var/spool/dovecot/
virtual_create_mailbox_dirsize = yes
virtual_mailbox_extended = yes

virtual_alias_maps = ldap:/etc/postfix/ldap_users.cf
virtual_mailbox_maps = ldap:/etc/postfix/ldap_mails.cf
smtpd_sender_login_maps = ldap:/etc/postfix/ldap_senders.cf

mailbox_transport = dovecot
mailbox_command = /usr/lib/dovecot/deliver
dovecot_destination_concurrency_limit = 1
dovecot_destination_recipient_limit = 1
virtual_transport = dovecot
```

ldap_XXX.cf
```
server_host = ldap://ldap.esci.es
search_base = ou=Users,dc=esci,dc=es
bind = no

query_filter = (&(objectclass=inetOrgPerson)(mail=%s))
result_attribute = uid
domain = esci.es
```

Any help/tip would be greatful!!

Thanks!

---

