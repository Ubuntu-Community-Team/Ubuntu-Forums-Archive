---
title: "smtp auth problem in ubuntu 10.04"
date: 2010-08-07
forum: Server Platforms
---

### Post by Iker Etxebarria on 2010-08-07
I know that this is a known and documented problem. But after trying all the solutions I found on this webforum, the problem continues.
I followed the oficial server documentation but when I make a telnet myhost 25 I get this and not the 250  AUTH message:
```
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

```
I don't know how to make the smtp auth working. This is my main.cf file:
```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/private/consorcio.essbilbao.es.crt
smtpd_tls_key_file = /etc/ssl/private/consorcio.essbilbao.es.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = essbilbao.es
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = essbilbao.es,  localhost.essbilbao.es, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth-client
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sender_restrictions = reject_unknown_sender_domain
smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_auth_only = yes
tls_random_source = dev:/dev/urandom
inet_protocols = all
smtpd_sasl_local-domain = 
smtpd_sasl_security-options = noanonymous
smtpd_tls_auth-only = no
smtp_tls_note_startttls-offer = yes
smtpd_tls_log_level = 1
smtpd_tls_session_cache_timeout = 3600s
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem

```
and this is my dovecot.conf file
```
## Dovecot configuration file

protocols = imaps
listen = *
log_timestamp = "%Y-%m-%d %H:%M:%S "
ssl = yes
disable_plaintext_auth = no
ssl_cert_file = /etc/ssl/certs/consorcio.essbilbao.es.crt
ssl_key_file = /etc/ssl/private/consorcio.essbilbao.es.key
#   mail_location = maildir:~/Maildir
#   mail_location = mbox:~/mail:INBOX=/var/mail/%u
#   mail_location = mbox:/var/mail/%d/%1n/%n:INDEX=/var/indexes/%d/%1n/%n
#
# </usr/share/doc/dovecot-common/wiki/MailLocation.txt>
#
#mail_location = 

  

##
## Authentication processes
##

# Executable location
#auth_executable = /usr/lib/dovecot/dovecot-auth

# Set max. process size in megabytes.
#auth_process_size = 256

# Authentication cache size in kilobytes. 0 means it's disabled.
# Note that bsdauth, PAM and vpopmail require cache_key to be set for caching
# to be used.
#auth_cache_size = 0
# Time to live in seconds for cached data. After this many seconds the cached
# record is no longer used, *except* if the main database lookup returns
# internal failure. We also try to handle password changes automatically: If
# user's previous authentication was successful, but this one wasn't, the
# cache isn't used. For now this works only with plaintext authentication.
#auth_cache_ttl = 3600
# TTL for negative hits (user not found, password mismatch).
# 0 disables caching them completely.
#auth_cache_negative_ttl = 3600

# Space separated list of realms for SASL authentication mechanisms that need
# them. You can leave it empty if you don't want to support multiple realms.
# Many clients simply use the first one listed here, so keep the default realm
# first.
#auth_realms =

# Default realm/domain to use if none was specified. This is used for both
# SASL realms and appending @domain to username in plaintext logins.
auth_default_realm = essbilbao.es 

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

# Log unsuccessful authentication attempts and the reasons why they failed.
#auth_verbose = no

# Even more verbose logging for debugging purposes. Shows for example SQL
# queries.
#auth_debug = no

# In case of password mismatches, log the passwords and used scheme so the
# problem can be debugged. Enabling this also enables auth_debug.
#auth_debug_passwords = no

# Maximum number of dovecot-auth worker processes. They're used to execute
# blocking passdb and userdb queries (eg. MySQL and PAM). They're
# automatically created and destroyed as needed.
#auth_worker_max_count = 30

# Host name to use in GSSAPI principal names. The default is to use the
# name returned by gethostname(). Use "$ALL" to allow all keytab entries.
#auth_gssapi_hostname =

# Kerberos keytab to use for the GSSAPI mechanism. Will use the system 
# default (usually /etc/krb5.keytab) if not specified.
#auth_krb5_keytab = 

# Do NTLM and GSS-SPNEGO authentication using Samba's winbind daemon and
# ntlm_auth helper.
# </usr/share/doc/dovecot-common/wiki/Authentication.Mechanisms.Winbind.txt>
#auth_use_winbind = no

# Path for Samba's ntlm_auth helper binary.
#auth_winbind_helper_path = /usr/bin/ntlm_auth

# Number of seconds to delay before replying to failed authentications.
#auth_failure_delay = 2

auth default {
  mechanisms = plain login

  passdb pam {
  }

  user = root
  socket listen {
    client {
      path = /var/spool/postfix/private/auth-client
      mode = 0660
	user = postfix
 	group = postfix
    }
  }
}

dict {
  #quota = mysql:/etc/dovecot/dovecot-dict-quota.conf
  #expire = db:/var/lib/dovecot/expire.db
}
plugin {
}


```
Thank you for reading. Any kind of help will be very helpfull for me. Thanks again.

---

