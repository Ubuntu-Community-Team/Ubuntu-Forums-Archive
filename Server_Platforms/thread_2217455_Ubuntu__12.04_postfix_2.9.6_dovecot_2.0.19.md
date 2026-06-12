---
title: "Ubuntu  12.04 postfix 2.9.6 dovecot 2.0.19"
date: 2014-04-17
forum: Server Platforms
---

### Post by fabio11 on 2014-04-17
Hi to all,
I'm trying to create an internal mail server for my lan, so I have installed postfix + dovecot.
I succed in telnet my machine but I can't login with thunderbird.


Here is what i get in my mail.log


Apr 17 14:29:51 orchestra postfix/smtpd[3195]: connect from unknown[10.111.1.51]
Apr 17 14:29:51 orchestra postfix/smtpd[3195]: warning: SASL: Connect to private/auth-client failed: No such file or directory
Apr 17 14:29:51 orchestra postfix/smtpd[3195]: fatal: no SASL authentication mechanisms
Apr 17 14:29:52 orchestra postfix/master[2927]: warning: process /usr/lib/postfix/smtpd pid 3195 exit status 1


Here are my config files
postfix/main.cf

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
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


myhostname = orchestra.pvt
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = Orchestra, localhost.localdomain, localhost, orchestra.pvt
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 10.111.1.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
myorigin = /etc/mailname
default_transport = smtp
relay_transport = smtp
inet_protocols = all
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth-client
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sender_restrictions = reject_unknown_sender_domain
mailbox_command = procmail -a "$EXTENSION"
smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_auth_only = no
tls_random_source = dev:/dev/urandom
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_session_cache_timeout = 3600s
queue_directory = /var/spool/postfix

```


dovecot.conf
```

# 2.0.19: /etc/dovecot/dovecot.conf
# OS: Linux 3.8.0-38-generic i686 Ubuntu 12.04.4 LTS ext4
auth_mechanisms = plain login
disable_plaintext_auth = no
mail_location = maildir:/home/%u/Maildir
managesieve_notify_capability = mailto
managesieve_sieve_capability = fileinto reject envelope encoded-character vacation subaddress comparator-i;ascii-numeric relational regex imap4flags copy include variables body enotify environment mailbox date ihave
passdb {
  driver = pam
}
plugin {
  sieve = ~/.dovecot.sieve
  sieve_dir = ~/sieve
}
protocols = pop3 imap
service auth {
  unix_listener /var/spool/postfix/private/auth {
    group = postfix
    mode = 0660
    user = postfix
  }
  unix_listener /var/spool/postfix/private/dovecot-auth {
    group = postfix
    mode = 0660
    user = postfix
  }
}
ssl_cert = </etc/ssl/certs/ssl-cert-snakeoil.pem
ssl_cipher_list = ALL:!LOW:!SSLv2:ALL:!aNULL:!ADH:!eNULL:!EXP:RC4+RSA:+HIGH:+MEDIUM
ssl_key = </etc/ssl/private/ssl-cert-snakeoil.key
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


10-auth.conf
```

##
## Authentication processes
##


# Disable LOGIN command and all other plaintext authentications unless
# SSL/TLS is used (LOGINDISABLED capability). Note that if the remote IP
# matches the local IP (ie. you're connecting from the same computer), the
# connection is considered secure and plaintext authentication is allowed.
#disable_plaintext_auth = yes


# Authentication cache size (e.g. 10M). 0 means it's disabled. Note that
# bsdauth, PAM and vpopmail require cache_key to be set for caching to be used.
#auth_cache_size = 0
# Time to live for cached data. After TTL expires the cached record is no
# longer used, *except* if the main database lookup returns internal failure.
# We also try to handle password changes automatically: If user's previous
# authentication was successful, but this one wasn't, the cache isn't used.
# For now this works only with plaintext authentication.
#auth_cache_ttl = 1 hour
# TTL for negative hits (user not found, password mismatch).
# 0 disables caching them completely.
#auth_cache_negative_ttl = 1 hour


# Space separated list of realms for SASL authentication mechanisms that need
# them. You can leave it empty if you don't want to support multiple realms.
# Many clients simply use the first one listed here, so keep the default realm
# first.
#auth_realms =


# Default realm/domain to use if none was specified. This is used for both
# SASL realms and appending @domain to username in plaintext logins.
#auth_default_realm =


# List of allowed characters in username. If the user-given username contains
# a character not listed in here, the login automatically fails. This is just
# an extra check to make sure user can't exploit any potential quote escaping
# vulnerabilities with SQL/LDAP databases. If you want to allow all characters,
# set this value to empty.
#auth_username_chars = abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ01234567890.-_@


# Username character translations before it's looked up from databases. The
# value contains series of from -> to characters. For example "#@/@" means
# that '#' and '/' characters are translated to '@'.
#auth_username_translation =


# Username formatting before it's looked up from databases. You can use
# the standard variables here, eg. %Lu would lowercase the username, %n would
# drop away the domain if it was given, or "%n-AT-%d" would change the '@' into
# "-AT-". This translation is done after auth_username_translation changes.
#auth_username_format =


# If you want to allow master users to log in by specifying the master
# username within the normal username string (ie. not using SASL mechanism's
# support for it), you can specify the separator character here. The format
# is then <username><separator><master username>. UW-IMAP uses "*" as the
# separator, so that could be a good choice.
#auth_master_user_separator =


# Username to use for users logging in with ANONYMOUS SASL mechanism
#auth_anonymous_username = anonymous


# Maximum number of dovecot-auth worker processes. They're used to execute
# blocking passdb and userdb queries (eg. MySQL and PAM). They're
# automatically created and destroyed as needed.
#auth_worker_max_count = 30


# Host name to use in GSSAPI principal names. The default is to use the
# name returned by gethostname(). Use "$ALL" (with quotes) to allow all keytab
# entries.
#auth_gssapi_hostname =


# Kerberos keytab to use for the GSSAPI mechanism. Will use the system
# default (usually /etc/krb5.keytab) if not specified. You may need to change
# the auth service to run as root to be able to read this file.
#auth_krb5_keytab =


# Do NTLM and GSS-SPNEGO authentication using Samba's winbind daemon and
# ntlm_auth helper. <doc/wiki/Authentication/Mechanisms/Winbind.txt>
#auth_use_winbind = no


# Path for Samba's ntlm_auth helper binary.
#auth_winbind_helper_path = /usr/bin/ntlm_auth


# Time to delay before replying to failed authentications.
#auth_failure_delay = 2 secs


# Require a valid SSL client certificate or the authentication fails.
#auth_ssl_require_client_cert = no


# Take the username from client's SSL certificate, using
# X509_NAME_get_text_by_NID() which returns the subject's DN's
# CommonName.
#auth_ssl_username_from_cert = no


# Space separated list of wanted authentication mechanisms:
#   plain login digest-md5 cram-md5 ntlm rpa apop anonymous gssapi otp skey
#   gss-spnego
# NOTE: See also disable_plaintext_auth setting.
auth_mechanisms = plain


##
## Password and user databases
##


#
# Password database is used to verify user's password (and nothing more).
# You can have multiple passdbs and userdbs. This is useful if you want to
# allow both system users (/etc/passwd) and virtual users to login without
# duplicating the system users into virtual database.
#
# <doc/wiki/PasswordDatabase.txt>
#
# User database specifies where mails are located and what user/group IDs
# own them. For single-UID configuration use "static" userdb.
#
# <doc/wiki/UserDatabase.txt>


#!include auth-deny.conf.ext
#!include auth-master.conf.ext


!include auth-system.conf.ext
#!include auth-sql.conf.ext
#!include auth-ldap.conf.ext
#!include auth-passwdfile.conf.ext
#!include auth-checkpassword.conf.ext
#!include auth-vpopmail.conf.ext
#!include auth-static.conf.ext

```

10-master.conf
```

#default_process_limit = 100
#default_client_limit = 1000


# Default VSZ (virtual memory size) limit for service processes. This is mainly
# intended to catch and kill processes that leak memory before they eat up
# everything.
#default_vsz_limit = 256M


# Login user is internally used by login processes. This is the most untrusted
# user in Dovecot system. It shouldn't have access to anything at all.
#default_login_user = dovenull


# Internal user is used by unprivileged processes. It should be separate from
# login user, so that login processes can't disturb other processes.
#default_internal_user = dovecot


service imap-login {
  inet_listener imap {
    #port = 143
  }
  inet_listener imaps {
    #port = 993
    #ssl = yes
  }


  # Number of connections to handle before starting a new process. Typically
  # the only useful values are 0 (unlimited) or 1. 1 is more secure, but 0
  # is faster. <doc/wiki/LoginProcess.txt>
  #service_count = 1


  # Number of processes to always keep waiting for more connections.
  #process_min_avail = 0


  # If you set service_count=0, you probably need to grow this.
  #vsz_limit = 64M
}


service pop3-login {
  inet_listener pop3 {
    #port = 110
  }
  inet_listener pop3s {
    #port = 995
	    #ssl = yes
  }
}


service lmtp {
  unix_listener lmtp {
    #mode = 0666
  }


  # Create inet listener only if you can't use the above UNIX socket
  #inet_listener lmtp {
    # Avoid making LMTP visible for the entire internet
    #address =
    #port =
  #}
}


service imap {
  # Most of the memory goes to mmap()ing files. You may need to increase this
  # limit if you have huge mailboxes.
  #vsz_limit = 256M


  # Max. number of IMAP processes (connections)
  #process_limit = 1024
}


service pop3 {
  # Max. number of POP3 processes (connections)
  #process_limit = 1024
}


service auth {
  # auth_socket_path points to this userdb socket by default. It's typically
  # used by dovecot-lda, doveadm, possibly imap process, etc. Its default
  # permissions make it readable only by root, but you may need to relax these
  # permissions. Users that have access to this socket are able to get a list
  # of all usernames and get results of everyone's userdb lookups.
  unix_listener auth-userdb {
    #mode = 0600
    #user =
    #group =
  }

```


Any idea about my problem?

---

### Post by fabio11 on 2014-04-22
up up

---

