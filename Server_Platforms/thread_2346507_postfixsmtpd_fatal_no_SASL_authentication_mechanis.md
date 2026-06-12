---
title: "postfix/smtpd: fatal: no SASL authentication mechanisms"
date: 2016-12-15
forum: Server Platforms
---

### Post by MechaMechanism on 2016-12-15
Filed bug report here.  [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1652131](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1652131)
Here is how to fix this.
Did the following.

```
sudo aa-complain usr.lib.dovecot.auth
```That was the whole problem right there.  Once I put that into complain mode everything just worked.  I had all my apparmor profiles on enforce mode.  I'll file a bug with launchpad for that profile.  Telnet worked great.  Sent a test email using mutt and it was received by gmail and gmail said tls worked.  Thanks for all your help Graham_Willis.  This has been quite the learning experience.



Followed this how to; [https://help.ubuntu.com/lts/serverguide/postfix.html](https://help.ubuntu.com/lts/serverguide/postfix.html)

Can't make tls auth work.  I generated the keys, certs and csr just fine, I think. I've included the config files for Postfix and the 2 config files for Dovecot. The answer is not obvious to me.


mail log
```
Dec 15 02:01:00 frontier postfix/master[20558]: daemon started -- version 3.1.0, configuration /etc/postfix
Dec 15 02:09:50 frontier postfix/smtpd[1957]: connect from portal.universal-mechanism.org[98.127.57.218]
Dec 15 02:09:50 frontier postfix/smtpd[1957]: warning: SASL: Connect to private/auth failed: Permission denied
Dec 15 02:09:50 frontier postfix/smtpd[1957]: fatal: no SASL authentication mechanisms
Dec 15 02:09:51 frontier postfix/master[20558]: warning: process /usr/lib/postfix/sbin/smtpd pid 1957 exit status 1
Dec 15 02:09:51 frontier postfix/master[20558]: warning: /usr/lib/postfix/sbin/smtpd: bad command startup -- throttling
Dec 15 02:11:31 frontier postfix/anvil[1960]: statistics: max connection rate 1/60s for (smtp:98.127.57.218) at Dec 15 02:09:50
Dec 15 02:11:31 frontier postfix/anvil[1960]: statistics: max connection count 1 for (smtp:98.127.57.218) at Dec 15 02:09:50
Dec 15 02:11:31 frontier postfix/anvil[1960]: statistics: max cache size 1 at Dec 15 02:09:50
Dec 15 02:11:37 frontier postfix/smtpd[2065]: connect from localhost[127.0.0.1]
Dec 15 02:11:37 frontier postfix/smtpd[2065]: warning: SASL: Connect to private/auth failed: Permission denied
Dec 15 02:11:37 frontier postfix/smtpd[2065]: fatal: no SASL authentication mechanisms
Dec 15 02:11:38 frontier postfix/master[20558]: warning: process /usr/lib/postfix/sbin/smtpd pid 2065 exit status 1
Dec 15 02:11:38 frontier postfix/master[20558]: warning: /usr/lib/postfix/sbin/smtpd: bad command startup -- throttling
Dec 15 02:13:10 frontier postfix/smtpd[2104]: connect from localhost[127.0.0.1]
Dec 15 02:13:10 frontier postfix/smtpd[2104]: warning: SASL: Connect to private/auth failed: Permission denied
Dec 15 02:13:10 frontier postfix/smtpd[2104]: fatal: no SASL authentication mechanisms
Dec 15 02:13:11 frontier postfix/master[20558]: warning: process /usr/lib/postfix/sbin/smtpd pid 2104 exit status 1
```


Main.cf postfix
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
smtpd_tls_cert_file = /etc/ssl/certs/server.crt
smtpd_tls_key_file = /etc/ssl/private/server.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = portal.universal-mechanism.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, portal.universal-mechanism.org, frontier, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
compatibility_level = 2
queue_directory = /var/spool/postfix
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_local_domain = portal.universal-mechanism.org
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = \ permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem

```


Dovecot 10-master.conf
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
  #vsz_limit = $default_vsz_limit
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
  #vsz_limit = $default_vsz_limit

  # Max. number of IMAP processes (connections)
  #process_limit = 1024
}

service pop3 {
  # Max. number of POP3 processes (connections)
  #process_limit = 1024
}

service auth {
  # auth_socket_path points to this userdb socket by default. It's typically
  # used by dovecot-lda, doveadm, possibly imap process, etc. Users that have
  # full permissions to this socket are able to get a list of all usernames and
  # get the results of everyone's userdb lookups.
  #
  # The default 0666 mode allows anyone to connect to the socket, but the
  # userdb lookups will succeed only if the userdb returns an "uid" field that
  # matches the caller process's UID. Also if caller's uid or gid matches the
  # socket's uid or gid the lookup succeeds. Anything else causes a failure.
  #
  # To give the caller full permissions to lookup all users, set the mode to
  # something else than 0666 and Dovecot lets the kernel enforce the
  # permissions (e.g. 0777 allows everyone full permissions).
  unix_listener auth-userdb {
    #mode = 0666
    #user = 
    #group = 
  }

  # Postfix smtp-auth
  unix_listener /var/spool/postfix/private/auth {
    mode = 0660
  }

  # Auth process is run as this user.
  user = postfix
  }

service auth-worker {
  # Auth worker process is run as root by default, so that it can access
  # /etc/shadow. If this isn't necessary, the user should be changed to
  # $default_internal_user.
  #user = root
}

service dict {
  # If dict proxy is used, mail processes should have access to its socket.
  # For example: mode=0660, group=vmail and global mail_access_groups=vmail
  unix_listener dict {
    #mode = 0600
    #user = 
    #group = 
  }
}
```


Dovecot 10-auth.conf
```
##
## Authentication processes
##

# Disable LOGIN command and all other plaintext authentications unless
# SSL/TLS is used (LOGINDISABLED capability). Note that if the remote IP
# matches the local IP (ie. you're connecting from the same computer), the
# connection is considered secure and plaintext authentication is allowed.
# See also ssl=required setting.
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
#auth_username_format = %Lu

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

---

### Post by MechaMechanism on 2016-12-16
I'm adding more information.

Got this from the logs.

```
Dec 15 02:01:00 frontier postfix/master[20558]: daemon started -- version 3.1.0, configuration /etc/postfix
Dec 15 02:09:50 frontier postfix/smtpd[1957]: connect from portal.universal-mechanism.org[98.127.57.218]
Dec 15 02:09:50 frontier postfix/smtpd[1957]: warning: SASL: Connect to private/auth failed: Permission denied
Dec 15 02:09:50 frontier postfix/smtpd[1957]: fatal: no SASL authentication mechanisms
Dec 15 02:09:51 frontier postfix/master[20558]: warning: process /usr/lib/postfix/sbin/smtpd pid 1957 exit status 1
Dec 15 02:09:51 frontier postfix/master[20558]: warning: /usr/lib/postfix/sbin/smtpd: bad command startup -- throttling
Dec 15 02:11:31 frontier postfix/anvil[1960]: statistics: max connection rate 1/60s for (smtp:98.127.57.218) at Dec 15 02:09:50
Dec 15 02:11:31 frontier postfix/anvil[1960]: statistics: max connection count 1 for (smtp:98.127.57.218) at Dec 15 02:09:50
Dec 15 02:11:31 frontier postfix/anvil[1960]: statistics: max cache size 1 at Dec 15 02:09:50
Dec 15 02:11:37 frontier postfix/smtpd[2065]: connect from localhost[127.0.0.1]
Dec 15 02:11:37 frontier postfix/smtpd[2065]: warning: SASL: Connect to private/auth failed: Permission denied
Dec 15 02:11:37 frontier postfix/smtpd[2065]: fatal: no SASL authentication mechanisms
Dec 15 02:11:38 frontier postfix/master[20558]: warning: process /usr/lib/postfix/sbin/smtpd pid 2065 exit status 1
Dec 15 02:11:38 frontier postfix/master[20558]: warning: /usr/lib/postfix/sbin/smtpd: bad command startup -- throttling
Dec 15 02:13:10 frontier postfix/smtpd[2104]: connect from localhost[127.0.0.1]
Dec 15 02:13:10 frontier postfix/smtpd[2104]: warning: SASL: Connect to private/auth failed: Permission denied
Dec 15 02:13:10 frontier postfix/smtpd[2104]: fatal: no SASL authentication mechanisms
Dec 15 02:13:11 frontier postfix/master[20558]: warning: process /usr/lib/postfix/sbin/smtpd pid 2104 exit status 1
```

---

### Post by Graham_Willis on 2016-12-17
It should work if it is configured correctly. What's the output of **netstat -av | egrep '25|465|587'**?
What happens after you issue from the server (I don't know on which port your postfix is listening so change it as appropriate):

telnet 127.0.0.1 25
EHLO portal.universal-mechanism.org

?

---

### Post by MechaMechanism on 2016-12-17
> **Graham_Willis said:**
> It should work if it is configured correctly. What's the output of **netstat -av | egrep '25|465|587'**?
What happens after you issue from the server (I don't know on which port your postfix is listening so change it as appropriate):

telnet 127.0.0.1 25
EHLO portal.universal-mechanism.org

?


What about this?  frontier postfix/smtpd[1957]: warning: SASL: Connect to private/auth failed: Permission denied.  Seems to be a permissions issue possibly.
```
nate@frontier:~$ netstat -av | egrep '25|465|587'
netstat: no support for `AF INET (sctp)' on this system.
netstat: no support for `AF INET (sctp)' on this system.
unix  2      [ ACC ]     STREAM     LISTENING     425598   private/retry
unix  2      [ ACC ]     STREAM     LISTENING     425601   private/discard
unix  2      [ ACC ]     STREAM     LISTENING     425604   private/local
unix  2      [ ACC ]     STREAM     LISTENING     425607   private/virtual
unix  2      [ ACC ]     STREAM     LISTENING     425610   private/lmtp
unix  2      [ ACC ]     STREAM     LISTENING     425613   private/anvil
unix  2      [ ACC ]     STREAM     LISTENING     425548   public/pickup
unix  2      [ ACC ]     STREAM     LISTENING     425616   private/scache
unix  2      [ ACC ]     STREAM     LISTENING     425619   private/maildrop
unix  2      [ ACC ]     STREAM     LISTENING     425622   private/uucp
unix  2      [ ACC ]     STREAM     LISTENING     425625   private/ifmail
unix  2      [ ACC ]     STREAM     LISTENING     425628   private/bsmtp
unix  2      [ ACC ]     STREAM     LISTENING     425631   private/scalemail-backend
unix  2      [ ACC ]     STREAM     LISTENING     425634   private/mailman
unix  2      [ ACC ]     STREAM     LISTENING     425559   private/tlsmgr
unix  2      [ ]         DGRAM                    22599    /var/spool/postfix/dev/log
unix  2      [ ACC ]     STREAM     LISTENING     425555   public/qmgr
unix  2      [ ACC ]     STREAM     LISTENING     38052    @nate-com.canonical.Unity.Master.Scope.files.T640185425691
unix  2      [ ACC ]     STREAM     LISTENING     425552   public/cleanup
unix  2      [ ACC ]     STREAM     LISTENING     425565   private/bounce
unix  2      [ ACC ]     STREAM     LISTENING     36428    @nate-com.canonical.Unity.Scope.scopes.T642407646582
unix  2      [ ACC ]     STREAM     LISTENING     425568   private/defer
unix  2      [ ACC ]     STREAM     LISTENING     425571   private/trace
unix  2      [ ACC ]     STREAM     LISTENING     425562   private/rewrite
unix  2      [ ACC ]     STREAM     LISTENING     425574   private/verify
unix  2      [ ACC ]     STREAM     LISTENING     425577   public/flush
unix  2      [ ACC ]     STREAM     LISTENING     425580   private/proxymap
unix  2      [ ACC ]     STREAM     LISTENING     425583   private/proxywrite
unix  2      [ ACC ]     STREAM     LISTENING     425586   private/smtp
unix  2      [ ACC ]     STREAM     LISTENING     425589   private/relay
unix  2      [ ACC ]     STREAM     LISTENING     425592   public/showq
unix  2      [ ACC ]     STREAM     LISTENING     425595   private/error
unix  2      [ ]         STREAM     CONNECTED     25625    /run/snapd.socket
unix  3      [ ]         STREAM     CONNECTED     33253    
unix  2      [ ]         STREAM     CONNECTED     25936    /run/snapd.socket
unix  3      [ ]         STREAM     CONNECTED     25142    /run/systemd/journal/stdout
unix  2      [ ]         DGRAM                    15253    
unix  3      [ ]         STREAM     CONNECTED     38054    @nate-com.canonical.Unity.Master.Scope.files.T640185425691
unix  3      [ ]         STREAM     CONNECTED     19251    
unix  3      [ ]         STREAM     CONNECTED     32425    
unix  3      [ ]         STREAM     CONNECTED     25198    
unix  3      [ ]         STREAM     CONNECTED     22591    
unix  3      [ ]         STREAM     CONNECTED     25199    
unix  3      [ ]         STREAM     CONNECTED     25200    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     22597    
unix  3      [ ]         STREAM     CONNECTED     25201    /run/systemd/journal/stdout
unix  2      [ ]         DGRAM                    22596    
unix  3      [ ]         STREAM     CONNECTED     22598    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     33251    
unix  3      [ ]         STREAM     CONNECTED     32825    @/tmp/dbus-96utvFmQsJ
unix  3      [ ]         STREAM     CONNECTED     32545    
unix  3      [ ]         STREAM     CONNECTED     25363    
unix  3      [ ]         STREAM     CONNECTED     32514    
unix  3      [ ]         STREAM     CONNECTED     33025    
unix  2      [ ]         STREAM     CONNECTED     1587428  
unix  3      [ ]         STREAM     CONNECTED     25362    
unix  3      [ ]         STREAM     CONNECTED     30254    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     37725    
unix  3      [ ]         STREAM     CONNECTED     25438    
unix  3      [ ]         STREAM     CONNECTED     25928    
unix  3      [ ]         STREAM     CONNECTED     36430    @nate-com.canonical.Unity.Scope.scopes.T642407646582
unix  3      [ ]         STREAM     CONNECTED     36025    
unix  3      [ ]         STREAM     CONNECTED     25929    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     30253    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     1587425  /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     32225    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     30258    
unix  2      [ ]         DGRAM                    25560    
unix  3      [ ]         STREAM     CONNECTED     25552    
unix  3      [ ]         STREAM     CONNECTED     33252    /run/systemd/journal/stdout
netstat: no support for `AF IPX' on this system.
netstat: no support for `AF AX25' on this system.
netstat: no support for `AF X25' on this system.
netstat: no support for `AF NETROM' on this system.
```

```
nate@frontier:~$ telnet 127.0.0.1 25
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
Connection closed by foreign host.
```

---

### Post by Graham_Willis on 2016-12-18
> 
What about this? frontier postfix/smtpd[1957]: warning: SASL: Connect to private/auth failed: Permission denied. Seems to be a permissions issue possibly.


It's necessary to establish what the escalation of the problem is. I saw the warning that you quoted, but they're often misleading. You can strace postfix though, and it perhaps will tell you explicitly what the path to the file of which permissions it's complaining about is. 

Connection was closed before you even got a chance to issue EHLO command, yes? It's necessary to know if the situation's better if SASL is completely turned off. Issue the following commands:

**sudo su -**
**cd /etc/postfix**
**cp -p main.cf main.cf.original**
**sed 's/.*sasl.*//' main.cf | sed 's/.*tls.*//' | sed 's/.*ssl.*//' > main.cf.without_ssl**
**mv main.cf.without_ssl main.cf**
[B]systemctl restart postfix.service

[/B]and see what it yields - specifically if it at least give you a chance to issue commands after establishing telnet connection to port 25 of your server.

Second, the logs that you presented are from **/var/log/mail.log**, yes? Do you have any entries relevant to your problem in **/var/log/auth.log**?

---

### Post by MechaMechanism on 2016-12-18
It works after that last set of commands.
```
nate@frontier:~$ telnet 127.0.0.1 25
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
220 frontier ESMTP Postfix (Ubuntu)
 EHLO portal.universal-mechanism.org
250-frontier
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250-DSN
250 SMTPUTF8
quit
221 2.0.0 Bye
Connection closed by foreign host.
```

The logs I posted before are from mail.log.  Here are the results from auth.log.  These are the only ones in auth.log other than sudo commands.
```
groupadd[ group added to /etc/group: name=postfix, GID=138
groupadd[29252]: group added to /etc/gshadow: name=postfix
groupadd[29252]: new group: name=postfix, GID=138
useradd[29258]: new user: name=postfix, UID=130, GID=138, home=/var/spool/postfix, shell=/bin/false
usermod[29263]: change user 'postfix' password
changed password expiry for postfix
group added to /etc/group: name=postdrop, GID=139
groupadd[29312]: group added to /etc/gshadow: name=postdrop
groupadd[29312]: new group: name=postdrop, GID=139
```

---

### Post by Graham_Willis on 2016-12-18
I've started postfix with your main.cf file and it worked just fine, at least it didn't quit the session at once and displayed the list of capabilities. Restore your original main.cf and reload postfix. What's the output of the following commands then:

**openssl s_client -starttls smtp -crlf -connect 127.0.0.1:25**
**sudo su -**
**ls -ld /etc/ /etc/ssl /etc/ssl/certs /etc/ssl/private**
**cd /etc/ssl**
**ls -la certs/server.crt certs/cacert.pem private/server.key**
**ls -ld /var /var/lib /var/lib/postfix**
**ls -la /var/lib/postfix/***
**ls -ld /var /var/spool /var/spool/postfix /var/spool/postfix/private**
**ls -la /var/spool/postfix/private/auth**

?

---

### Post by MechaMechanism on 2016-12-18
Here ya go.

```
nate@frontier:~$  openssl s_client -starttls smtp -crlf -connect 127.0.0.1:25
CONNECTED(00000003)
didn't found starttls in server response, try anyway...
140291666972376:error:140770FC:SSL routines:SSL23_GET_SERVER_HELLO:unknown protocol:s23_clnt.c:794:
---
no peer certificate available
---
No client certificate CA names sent
---
SSL handshake has read 217 bytes and written 340 bytes
---
New, (NONE), Cipher is (NONE)
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
SSL-Session:
    Protocol  : TLSv1.2
    Cipher    : 0000
    Session-ID: 
    Session-ID-ctx: 
    Master-Key: 
    Key-Arg   : None
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    Start Time: 1482089813
    Timeout   : 300 (sec)
    Verify return code: 0 (ok)
```
```
nate@frontier:~$  sudo su -
[sudo] password for nate: 
root@frontier:~#  ls -ld /etc/ /etc/ssl /etc/ssl/certs /etc/ssl/private
drwxr-xr-x 157 root root     12288 Dec 17 21:18 /etc/
drwxr-xr-x   6 root root      4096 Dec 15 01:47 /etc/ssl
drwxr-xr-x   2 root root     28672 Dec 15 01:49 /etc/ssl/certs
drwx--x---   2 root ssl-cert  4096 Dec 15 01:49 /etc/ssl/private
```
```
root@frontier:/etc/ssl#  ls -la certs/server.crt certs/cacert.pem private/server.key
-rw-r--r-- 1 nate nate 1521 Dec 15 01:49 certs/cacert.pem
-rw-r--r-- 1 root root 1273 Nov  9 00:15 certs/server.crt
-rw-r--r-- 1 root root 1675 Nov  9 00:15 private/server.key
```
```
root@frontier:/etc/ssl#  ls -ld /var /var/lib /var/lib/postfix
drwxr-xr-x 16 root    root    4096 Jun  1  2016 /var
drwxr-xr-x 90 root    root    4096 Dec 13 00:44 /var/lib
drwxr-xr-x  2 postfix postfix 4096 Dec 13 02:32 /var/lib/postfix
```
```
root@frontier:/etc/ssl#  ls -la /var/lib/postfix/*
-rw------- 1 postfix postfix   33 Dec 18 10:13 /var/lib/postfix/master.lock
-rw------- 1 postfix postfix 1024 Dec 18 09:31 /var/lib/postfix/prng_exch
-rw------- 1 postfix postfix 8192 Dec 17 21:39 /var/lib/postfix/smtpd_scache.db
-rw------- 1 postfix postfix 8192 Dec 17 21:39 /var/lib/postfix/smtp_scache.db
```
```
root@frontier:/etc/ssl#  ls -ld /var /var/spool /var/spool/postfix /var/spool/postfix/private
drwxr-xr-x 16 root    root 4096 Jun  1  2016 /var
drwxr-xr-x  8 root    root 4096 Dec 12 20:09 /var/spool
drwxr-xr-x 20 root    root 4096 Dec 13 00:46 /var/spool/postfix
drwx------  2 postfix root 4096 Dec 18 10:13 /var/spool/postfix/private
```
```
root@frontier:/etc/ssl#  ls -la /var/spool/postfix/private/auth
srw-rw---- 1 root root 0 Dec 15 02:45 /var/spool/postfix/private/auth
```

---

### Post by Graham_Willis on 2016-12-18
You haven't changed **unix_listener /var/spool/postfix/private/auth** section in your **/etc/dovecot/conf.d/10-master.conf **file. Also, I'm not sure if you don't have a mistake there: 

```

unix_listener /var/spool/postfix/private/auth {
    mode = 0660
  }


  # Auth process is run as this user.
  user = postfix
  }

```

It seems like there is an enclosing curly bracket without corresponding opening one. Change values in unix_listener section according to the tutorial (user = postfix, group = postfix), remove typos if there're present and reload dovecot and postfix. Does it fix the problem?

---

### Post by MechaMechanism on 2016-12-18
> **Graham_Willis said:**
> You haven't changed **unix_listener /var/spool/postfix/private/auth** section in your **/etc/dovecot/conf.d/10-master.conf **file. Also, I'm not sure if you don't have a mistake there: 

```

unix_listener /var/spool/postfix/private/auth {
    mode = 0660
  }


  # Auth process is run as this user.
  user = postfix
  }

```

It seems like there is an enclosing curly bracket without corresponding opening one. Change values in unix_listener section according to the tutorial (user = postfix, group = postfix), remove typos if there're present and reload dovecot and postfix. Does it fix the problem?Still fails.  Grrr.  I did restart the services, both dovecot and postfix.
Here is what my 10-master.conf looks like now after your suggestion.```
    unix_listener auth-userdb {
    mode = 0666
    user = postfix
    group = postfix
  }

   #Postfix smtp-auth {
  unix_listener /var/spool/postfix/private/auth {
    mode = 0660
    user = postfix
    group = postfix
  }

  # Auth process is run as this user.
  user = postfix
}
```

No go on telnet. ```
nate@frontier:~$  telnet 127.0.0.1 25
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
Connection closed by foreign host.
```
I appreciate your help very much.

---

### Post by Graham_Willis on 2016-12-19
Have you tried restarting services the second time to be sure that both of them read the configuration of each other? If yes, you have uncommented entries in both **unix_listener auth-userd** and in **unix_listener /var/spool/postfix/private/auth**, while in the guide you linked to only the entries in the latter section are uncommented. So comment the entries in the former section, restart postfix, restart dovecot, restart both services again and check if it brings any changes. However, it should work with uncommented entries in both the sections, too.

---

### Post by MechaMechanism on 2016-12-19
> **Graham_Willis said:**
> Have you tried restarting services the second time to be sure that both of them read the configuration of each other? If yes, you have uncommented entries in both **unix_listener auth-userd** and in **unix_listener /var/spool/postfix/private/auth**, while in the guide you linked to only the entries in the latter section are uncommented. So comment the entries in the former section, restart postfix, restart dovecot, restart both services again and check if it brings any changes. However, it should work with uncommented entries in both the sections, too.

I tried with this; ```
unix_listener auth-userdb {
    #mode = 0666
    #user =
    #group =
  }

  # Postfix smtp-auth
  unix_listener /var/spool/postfix/private/auth {
    mode = 0666
  }
```Then I tried with this; ```
unix_listener auth-userdb {
    mode = 0660
    user = postfix
    group = postfix
  }

  # Postfix smtp-auth
  unix_listener /var/spool/postfix/private/auth {
    mode = 0666
  }
```

Nothing worked.
Dec 19 06:12:00 frontier postfix/smtpd[18019]: fatal: no SASL authentication mechanisms
I also noticed this in mail.log; ```
Dec 19 06:11:51 frontier postfix/postfix-script[17948]: warning: group or other writable: /usr/lib/postfix/./libpostfix-master.so.1
Dec 19 06:11:51 frontier postfix/postfix-script[17949]: warning: group or other writable: /usr/lib/postfix/./libpostfix-dns.so.1
Dec 19 06:11:51 frontier postfix/postfix-script[17950]: warning: group or other writable: /usr/lib/postfix/./libpostfix-util.so.1
Dec 19 06:11:51 frontier postfix/postfix-script[17951]: warning: group or other writable: /usr/lib/postfix/./libpostfix-global.so.1
Dec 19 06:11:51 frontier postfix/postfix-script[17952]: warning: group or other writable: /usr/lib/postfix/./libpostfix-tls.so.1
Dec 19 06:11:51 frontier postfix/postfix-script[17953]: warning: group or other writable: /usr/lib/postfix/./sbin/lmtp
Dec 19 06:11:51 frontier postfix/postfix-script[17954]: warning: group or other writable: /usr/lib/postfix/sbin/./lmtp
Dec 19 06:11:51 frontier postfix/postfix-script[18005]: starting the Postfix mail system
Dec 19 06:11:51 frontier postfix/master[18007]: daemon started -- version 3.1.0, configuration /etc/postfix
Dec 19 06:12:00 frontier postfix/smtpd[18019]: connect from localhost[127.0.0.1]
Dec 19 06:12:00 frontier postfix/smtpd[18019]: fatal: no SASL authentication mechanisms
Dec 19 06:12:01 frontier postfix/master[18007]: warning: process /usr/lib/postfix/sbin/smtpd pid 18019 exit status 1
Dec 19 06:12:01 frontier postfix/master[18007]: warning: /usr/lib/postfix/sbin/smtpd: bad command startup -- throttling
```

---

### Post by Graham_Willis on 2016-12-20
Have you tried with:

```

unix_listener auth-userdb {
    #mode = 0600
    #user = 
    #group = 
  }


  # Postfix smtp-auth
  unix_listener /var/spool/postfix/private/auth {
    mode = 0660
    user = postfix
    group = postfix
  }

```

? What's the output of 
[B]
openssl s_client -starttls smtp -crlf -connect 127.0.0.1:25
ls -la /var/spool/postfix/private/auth[/B]

now? I see the following possibilities:

- you have accidentally changed more than necessary in your 10-master.conf file (I don't know to what extent the message "fatal: no SASL authentication mechanism" is to be trusted) or perhaps in some more files,
- your SASL-related libraries are broken. 

You're using dovecot SASL so I'd recommend switching to CyrusSASL to see if it makes any difference. If dovecot SASL-related libraries are broken, then the simplest way to go - if you insist on using dovecot SASL -  would be to remove purge dovecot and install it again (but taking backup earlier's strongly recommended).

---

### Post by MechaMechanism on 2016-12-20
> **Graham_Willis said:**
> Have you tried with:

```

unix_listener auth-userdb {
    #mode = 0600
    #user = 
    #group = 
  }


  # Postfix smtp-auth
  unix_listener /var/spool/postfix/private/auth {
    mode = 0660
    user = postfix
    group = postfix
  }

```

? What's the output of 
[B]
openssl s_client -starttls smtp -crlf -connect 127.0.0.1:25
ls -la /var/spool/postfix/private/auth[/B]

now? I see the following possibilities:

- you have accidentally changed more than necessary in your 10-master.conf file (I don't know to what extent the message "fatal: no SASL authentication mechanism" is to be trusted) or perhaps in some more files,
- your SASL-related libraries are broken. 

You're using dovecot SASL so I'd recommend switching to CyrusSASL to see if it makes any difference. If dovecot SASL-related libraries are broken, then the simplest way to go - if you insist on using dovecot SASL -  would be to remove purge dovecot and install it again (but taking backup earlier's strongly recommended).

Interesting, no certs found.  ```
nate@frontier:~$ openssl s_client -starttls smtp -crlf -connect 127.0.0.1:25
CONNECTED(00000003)
didn't found starttls in server response, try anyway...
write:errno=32
---
no peer certificate available
---
No client certificate CA names sent
---
SSL handshake has read 0 bytes and written 25 bytes
---
New, (NONE), Cipher is (NONE)
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
SSL-Session:
    Protocol  : TLSv1.2
    Cipher    : 0000
    Session-ID: 
    Session-ID-ctx: 
    Master-Key: 
    Key-Arg   : None
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    Start Time: 1482245798
    Timeout   : 300 (sec)
    Verify return code: 0 (ok)
---
```

---

### Post by Graham_Willis on 2016-12-21
OK, move your cert-related files to your home directory and generate these files again using:

[http://stackoverflow.com/questions/10175812/how-to-create-a-self-signed-certificate-with-openssl](http://stackoverflow.com/questions/10175812/how-to-create-a-self-signed-certificate-with-openssl)

> 
[B]openssl genrsa -des3 -out server.key 2048
[/B]**openssl rsa -in server.key -out server.key**
**openssl req -sha256 -new -key server.key -out server.csr -subj '/CN=localhost'**
**openssl x509 -req -sa256 -days 365 -in server.csr -signkey server.key -out server.crt**
**cat server.crt server.key > cert.pem**


Copy them as appropriate, then restart dovecot, postfix, dovecot, postfix and see if it brings any changes. If it doesn't, then post the output of the **openssl** and **telnet** testing command again. And the output of previously requested **ls **command, too.

---

### Post by MechaMechanism on 2016-12-21
Looks like Dovecot can't connect to the private/auth file.  Apparmor is blocking Dovecot maybe?  Telnet, etc all give pretty much the same thing as before.  We should take a look at the Apparmor profile for dovecot.

```
Dec 21 09:56:58 frontier postfix/smtpd[4437]: connect from localhost[127.0.0.1]
Dec 21 09:56:58 frontier postfix/smtpd[4437]: fatal: no SASL authentication mechanisms
Dec 21 09:56:58 frontier kernel: [ 1160.804065] audit: type=1400 audit(1482339418.476:108): apparmor="DENIED" operation="connect" profile="/usr/lib/dovecot/auth" name="/run/dovecot/anvil-auth-penalty" pid=4440 comm="auth" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Dec 21 09:56:58 frontier kernel: [ 1160.804097] audit: type=1400 audit(1482339418.476:109): apparmor="DENIED" operation="open" profile="/usr/lib/dovecot/auth" name="/run/dovecot/stats-user" pid=4440 comm="auth" requested_mask="w" denied_mask="w" fsuid=0 ouid=0
Dec 21 09:56:58 frontier kernel: [ 1160.804130] audit: type=1400 audit(1482339418.476:110): apparmor="DENIED" operation="sendmsg" info="Failed name lookup - disconnected path" error=-13 profile="/usr/lib/dovecot/log" name="run/systemd/journal/dev-log" pid=4274 comm="log" requested_mask="w" denied_mask="w" fsuid=0 ouid=0
Dec 21 09:56:58 frontier kernel: [ 1160.804146] audit: type=1400 audit(1482339418.476:111): apparmor="DENIED" operation="sendmsg" info="Failed name lookup - disconnected path" error=-13 profile="/usr/lib/dovecot/log" name="run/systemd/journal/dev-log" pid=4274 comm="log" requested_mask="w" denied_mask="w" fsuid=0 ouid=0
Dec 21 09:56:58 frontier kernel: [ 1160.804678] audit: type=1400 audit(1482339418.476:112): apparmor="DENIED" operation="file_perm" profile="/usr/lib/dovecot/auth" name="/var/spool/postfix/private/auth" pid=4440 comm="auth" requested_mask="w" denied_mask="w" fsuid=129 ouid=130
Dec 21 09:56:58 frontier kernel: [ 1160.804682] audit: type=1400 audit(1482339418.476:113): apparmor="DENIED" operation="file_perm" profile="/usr/lib/dovecot/auth" name="/var/spool/postfix/private/auth" pid=4440 comm="auth" requested_mask="w" denied_mask="w" fsuid=129 ouid=130
```

---

### Post by Graham_Willis on 2016-12-22
Possible. Just try to disable it for testing purposes and check if it makes any difference:

[https://help.ubuntu.com/lts/serverguide/apparmor.html](https://help.ubuntu.com/lts/serverguide/apparmor.html) :

[B]sudo systemctl stop apparmor.service
[/B][B]sudo update-rc.d -f apparmor remove
[/B]
**There's one very important thing to remember about when you're done with this problem**: note that your cert.pem file contains the private key, so it's necessary to set appropriate permissions on it.

---

### Post by MechaMechanism on 2016-12-22
Did the following.

```
sudo aa-complain usr.lib.dovecot.auth
```That was the whole problem right there.  Once I put that into complain mode everything just worked.  I had all my apparmor profiles on enforce mode.  I'll file a bug with launchpad for that profile.  Telnet worked great.  Sent a test email using mutt and it was received by gmail and gmail said tls worked.  Thanks for all your help Graham_Willis.  This has been quite the learning experience.

---

### Post by MechaMechanism on 2016-12-22
Did the following.

```
sudo aa-complain usr.lib.dovecot.auth
```That was the whole problem right there.  Once I put that into complain mode everything just worked.  I had all my apparmor profiles on enforce mode.  I'll file a bug with launchpad for that profile.  Telnet worked great.  Sent a test email using mutt and it was received by gmail and gmail said tls worked.  Thanks for all your help Graham_Willis.  This has been quite the learning experience.

---

### Post by MechaMechanism on 2016-12-22
Did the following.

```
sudo aa-complain usr.lib.dovecot.auth
```That was the whole problem right there.  Once I put that into complain mode everything just worked.  I had all my apparmor profiles on enforce mode.  I'll file a bug with launchpad for that profile.  Telnet worked great.  Sent a test email using mutt and it was received by gmail and gmail said tls worked.  Thanks for all your help Graham_Willis.  This has been quite the learning experience.

---

