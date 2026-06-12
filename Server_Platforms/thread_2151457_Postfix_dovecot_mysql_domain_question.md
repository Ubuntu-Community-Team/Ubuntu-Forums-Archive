---
title: "Postfix dovecot mysql domain question"
date: 2013-06-04
forum: Server Platforms
---

### Post by kevinxsalerno on 2013-06-04
I am trying to set up an ubuntu 12.04 email server with postfix and dovecoat through mysql + postfixadmin.

I  am running off of a dedicated box through a router with port forwarding  for imaps, imap, pop, pops, smtp, smtps and have my own official domain  name through godaddy pointing the main 'A' record at my IP.

This was the guide I followed: [http://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/](http://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/) up until the horde webmail thing. The guide is outdated in that part

**Please see post reply #4 for my current issue**

Currently, I think my domain settings are a bit screwed up.

**godaddy zonefile** **(I NEED THE MOST HELP HERE!)**

```

A (host)
Host: @              Points to: 123.123.123.123 (my ip)

Cname (Alias)
host: www          Points to: @


MX (Mail exchanger)

priority: 0         Host: @       Points to: mail.mydomain.com
priority: 10       Host: @       Points to: smtp.mydomain.com

```

/etc/hosts
```
  
GNU nano 2.2.6               File: hosts

127.0.0.1 mydomain.com localhost
127.0.0.1 mail.mydomain.com localhost


```

/etc/hostname
```

mydomain.com

```

postfix main.cf
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version
 
# The first text sent to a connecting process.
smtpd_banner = $myhostname ESMTP $mail_name
biff = no
# appending .domain is the MUA's job.
append_dot_mydomain = no
readme_directory = no
 
# SASL parameters
# ---------------------------------
 
# Use Dovecot to authenticate.
smtpd_sasl_type = dovecot
# Referring to /var/spool/postfix/private/auth
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
smtpd_sasl_authenticated_header = yes
 
# TLS parameters
# ---------------------------------
 
# Replace this with your SSL certificate path if you are using one.
smtpd_tls_cert_file=/etc/apache2/ssl/mydomain/server.crt
smtpd_tls_key_file=/etc/apache2/ssl/mydomain/mydomain.key
# The snakeoil self-signed certificate has no need for a CA file. But
# if you are using your own SSL certificate, then you probably have
# a CA certificate bundle from your provider. The path to that goes
# here.
#smtpd_tls_CAfile=/path/to/ca/file
smtpd_use_tls=yes
smtp_tls_security_level = may
smtpd_tls_security_level = may
#smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
 
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
 
# SMTPD parameters
# ---------------------------------
 
# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h
# will it be a permanent error or temporary
unknown_local_recipient_reject_code = 450
# how long to keep message on queue before return as failed.
# some have 3 days, I have 16 days as I am backup server for some people
# whom go on holiday with their server switched off.
maximal_queue_lifetime = 7d
# max and min time in seconds between retries if connection failed
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
# how long to wait when servers connect before receiving rest of data
smtp_helo_timeout = 60s
# how many address can be used in one message.
# effective stopper to mass spammers, accidental copy in whole address list
# but may restrict intentional mail shots.
smtpd_recipient_limit = 16
# how many error before back off.
smtpd_soft_error_limit = 3
# how many max errors before blocking it.
smtpd_hard_error_limit = 12
 
# This next set are important for determining who can send mail and relay mail
# to other servers. It is very important to get this right - accidentally producing
# an open relay that allows unauthenticated sending of mail is a Very Bad Thing.
#
# You are encouraged to read up on what exactly each of these options accomplish.
 
# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
# Requirements for the sender details
smtpd_sender_restrictions  = permit_sasl_authenticated, permit_mynetworks, warn_if_reject  reject_non_fqdn_sender, reject_unknown_sender_domain,  reject_unauth_pipelining, permit
# Requirements for the connecting server
smtpd_client_restrictions  = reject_rbl_client sbl.spamhaus.org, reject_rbl_client  blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
# Requirement for the recipient address. Note that the entry for
# "check_policy_service inet:127.0.0.1:10023" enables Postgrey.
smtpd_recipient_restrictions  = permit_mynetworks, permit_sasl_authenticated,  reject_non_fqdn_recipient, reject_unknown_recipient_domain,  reject_unauth_destination, reject_unauth_pipelining,  check_policy_service inet:127.0.0.1:10023, permit
smtpd_data_restrictions = reject_unauth_pipelining
 
# require proper helo at connections
smtpd_helo_required = yes
# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes
 
# General host and delivery info
# ----------------------------------
 
myhostname = mail.mydomain.com
#myorigin = 
myorigin = /etc/hostname
# Some people see issues when setting mydestination explicitly to the server
# subdomain, while leaving it empty generally doesn't hurt. So it is left empty here.
# mydestination = mail.example.com, localhost
#mydestination = $myhostname localhost.$mydomain localhost
mydestination =
# If you have a separate web server that sends outgoing mail through this
# mailserver, you may want to add its IP address to the space-delimited list in
# mynetworks, e.g. as 111.222.333.444/32.
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
 
# This specifies where the virtual mailbox folders will be located.
virtual_mailbox_base = /var/vmail
# This is for the mailbox location for each user. The domainaliases
# map allows us to make use of Postfix Admin's domain alias feature.
virtual_mailbox_maps  = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf,  mysql:/etc/postfix/mysql_virtual_mailbox_domainaliases_maps.cf
# and their user id
virtual_uid_maps = static:150
# and group id
virtual_gid_maps = static:8
# This is for aliases. The domainaliases map allows us to make
# use of Postfix Admin's domain alias feature.
virtual_alias_maps  = mysql:/etc/postfix/mysql_virtual_alias_maps.cf,  mysql:/etc/postfix/mysql_virtual_alias_domainaliases_maps.cf
# This is for domain lookups.
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
 
# Integration with other packages
# ---------------------------------------
 
# Tell postfix to hand off mail to the definition for dovecot in master.cf
virtual_transport = dovecot
dovecot_destination_recipient_limit = 1
 
# Use amavis for virus and spam scanning
content_filter = amavis:[127.0.0.1]:10024
 
# Header manipulation
# --------------------------------------
 
# Getting rid of unwanted headers. See: https://posluns.com/guides/header-removal/
header_checks = regexp:/etc/postfix/header_checks
# getting rid of x-original-to
enable_original_recipient = no


```

postfix master.cf
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
 
# SMTP on port 25, unencrypted.
smtp      inet  n       -       -       -       -       smtpd
#smtp      inet  n       -       -       -       1       postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
 
# SMTP with TLS on port 587. Currently commented.
#submission inet n       -       -       -       -       smtpd
#  -o syslog_name=postfix/submission
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_enforce_tls=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject
#  -o smtpd_sasl_tls_security_options=noanonymous
 
# SMTP over SSL on port 465.
smtps     inet  n       -       -       -       -       smtpd
  -o syslog_name=postfix/smtps
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_tls_auth_only=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject
  -o smtpd_sasl_security_options=noanonymous,noplaintext
  -o smtpd_sasl_tls_security_options=noanonymous
 
#628       inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
  -o content_filter=
  -o receive_override_options=no_header_body_checks
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       n       300     1       oqmgr
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
relay     unix  -       -       -       -       -       smtp
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
# ====================================================================
#
# Recent Cyrus versions can use the existing "lmtp" master.cf entry.
#
# Specify in cyrus.conf:
#   lmtp    cmd="lmtpd -a" listen="localhost:lmtp" proto=tcp4
#
# Specify in main.cf one or more of the following:
#  mailbox_transport = lmtp:inet:localhost
#  virtual_transport = lmtp:inet:localhost
#
# ====================================================================
#
# Cyrus 2.1.5 (Amos Gouaux)
# Also specify in main.cf: cyrus_destination_recipient_limit=1
#
#cyrus     unix  -       n       n       -       -       pipe
#  user=cyrus argv=/cyrus/bin/deliver -e -r ${sender} -m ${extension} ${user}
#
# ====================================================================
# Old example of delivery via Cyrus.
#
#old-cyrus unix  -       n       n       -       -       pipe
#  flags=R user=cyrus argv=/cyrus/bin/deliver -e -m ${extension} ${user}
#
# ====================================================================
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
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
 
# The next two entries integrate with Amavis for anti-virus/spam checks.
amavis      unix    -       -       -       -       3       smtp
  -o smtp_data_done_timeout=1200
  -o smtp_send_xforward_command=yes
  -o disable_dns_lookups=yes
  -o max_use=20
127.0.0.1:10025 inet    n       -       -       -       -       smtpd
  -o content_filter=
  -o local_recipient_maps=
  -o relay_recipient_maps=
  -o smtpd_restriction_classes=
  -o smtpd_delay_reject=no
  -o smtpd_client_restrictions=permit_mynetworks,reject
  -o smtpd_helo_restrictions=
  -o smtpd_sender_restrictions=
  -o smtpd_recipient_restrictions=permit_mynetworks,reject
  -o smtpd_data_restrictions=reject_unauth_pipelining
  -o smtpd_end_of_data_restrictions=
  -o mynetworks=127.0.0.0/8
  -o smtpd_error_sleep_time=0
  -o smtpd_soft_error_limit=1001
  -o smtpd_hard_error_limit=1000
  -o smtpd_client_connection_count_limit=0
  -o smtpd_client_connection_rate_limit=0
  -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks
 
# Integration with Dovecot - hand mail over to it for local delivery, and
# run the process under the vmail user and mail group.
dovecot      unix   -        n      n       -       -   pipe
  flags=DRhu user=vmail:mail argv=/usr/lib/dovecot/dovecot-lda -d $(recipient)
```


dovecot main.cf
```

## Dovecot configuration file

# If you're in a hurry, see http://wiki2.dovecot.org/QuickConfiguration

# "doveconf -n" command gives a clean output of the changed settings. Use it
# instead of copy&pasting files when posting to the Dovecot mailing list.

# '#' character and everything after it is treated as comments. Extra spaces
# and tabs are ignored. If you want to use either of these explicitly, put the
# value inside quotes, eg.: key = "# char and trailing whitespace  "

# Default values are shown for each setting, it's not required to uncomment
# those. These are exceptions to this though: No sections (e.g. namespace {})
# or plugin settings are added by default, they're listed only as examples.
# Paths are also just examples with the real defaults being based on configure
# options. The paths listed here are for configure --prefix=/usr
# --sysconfdir=/etc --localstatedir=/var

# Enable installed protocols
!include_try /usr/share/dovecot/protocols.d/*.protocol

# A comma separated list of IPs or hosts where to listen in for connections. 
# "*" listens in all IPv4 interfaces, "::" listens in all IPv6 interfaces.
# If you want to specify non-default ports or anything more complex,
# edit conf.d/master.conf.
#listen = *, ::

# Base directory where to store runtime data.
#base_dir = /var/run/dovecot/

# Name of this instance. Used to prefix all Dovecot processes in ps output.
#instance_name = dovecot

# Greeting message for clients.
#login_greeting = Dovecot ready.

# Space separated list of trusted network ranges. Connections from these
# IPs are allowed to override their IP addresses and ports (for logging and
# for authentication checks). disable_plaintext_auth is also ignored for
# these networks. Typically you'd specify your IMAP proxy servers here.
#login_trusted_networks =

# Sepace separated list of login access check sockets (e.g. tcpwrap)
#login_access_sockets = 

# Show more verbose process titles (in ps). Currently shows user name and
# IP address. Useful for seeing who are actually using the IMAP processes
# (eg. shared mailboxes or if same uid is used for multiple accounts).
#verbose_proctitle = no

# Should all processes be killed when Dovecot master process shuts down.
# Setting this to "no" means that Dovecot can be upgraded without
# forcing existing client connections to close (although that could also be
# a problem if the upgrade is e.g. because of a security fix).
#shutdown_clients = yes

# If non-zero, run mail commands via this many connections to doveadm server,
# instead of running them directly in the same process.
#doveadm_worker_count = 0
# UNIX socket or host:port used for connecting to doveadm server
#doveadm_socket_path = doveadm-server

# Space separated list of environment variables that are preserved on Dovecot
# startup and passed down to all of its child processes. You can also give
# key=value pairs to always set specific settings.
#import_environment = TZ

##
## Dictionary server settings
##

# Dictionary can be used to store key=value lists. This is used by several
# plugins. The dictionary can be accessed either directly or though a
# dictionary server. The following dict block maps dictionary names to URIs
# when the server is used. These can then be referenced using URIs in format
# "proxy::<name>".

dict {
  #quota = mysql:/etc/dovecot/dovecot-dict-sql.conf.ext
  #expire = sqlite:/etc/dovecot/dovecot-dict-sql.conf.ext
}

# Most of the actual configuration gets included below. The filenames are
# first sorted by their ASCII value and parsed in that order. The 00-prefixes
# in filenames are intended to make it easier to understand the ordering.
!include conf.d/*.conf

# A config file can also tried to be included without giving an error if
# it's not found:
!include_try local.conf


```

dovecot master.cf

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
    mode = 0600
    user = vmail
    group = mail
  }

  # Postfix smtp-auth
  unix_listener /var/spool/postfix/private/auth {
    mode = 0660
    user = postfix
    group = postfix
  #}

  # Auth process is run as this user.
  #user = $default_internal_user
}

#service auth-worker {
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





Email I receive from google if I email [EMAIL="kevin@mydomain.com"]kevin@mydomain.com[/EMAIL]

```

[FONT=-moz-fixed]
This is an automatically generated Delivery Status Notification  THIS IS A WARNING MESSAGE ONLY.  YOU DO NOT NEED TO RESEND YOUR MESSAGE.  Delivery to the following recipient has been delayed:      kevin@mydomain.com  Message will be retried for 1 more day(s)  Technical details of temporary failure:  DNS Error: Domain name not found  ----- Original message -----  DKIM-Signature: v=1; a=rsa-sha256; c=relaxed/relaxed;         d=gmail.com; s=20120113;         h=message-id:date:from:user-agent:mime-version:to:subject          :content-type:content-transfer-encoding;         bh=9OP8H/nVHXwSfBXPhsCgGLRr6H7jPj9PEYZDi5pSjcg=;         b=h0t91b0wJH+vNOks1IEW/FPDW40UnplneW/pQ+xzFsRMKDFRXDGZ6hceIHvFa2ICxi          DTp2La2KEDFufucyOt+OkeZ5a31PX8UvvNNDBqLhWLetuuETmRnC0rziJyO/MVTfbJBX          xoYbGkR7UzAnATb6bEyJomo2BHWdiVBP04JLSQXBBZJ63MCTrFcwrJUyG1/fV0yp8qw4          YObN7SFMwE9xkEMoKwGmqGDDoPcOvgG9QupdX6vJtIv3tOJFRYVoPRDcVZplVqFagBUy          NigGF2Y5bYGf7aGOeQYptNeqmsrDRGcOpHH20+gsWFT5hENnK1D3QiYA/Ad3P4TfBArk          HV3Q== X-Received: by 10.50.32.33 with SMTP id f1mr4922220igi.39.1370138639155;         Sat, 01 Jun 2013 19:03:59 -0700 (PDT) Return-Path: myemail@gmail.com Received: from [192.168.1.19] (96-35-96-22.dhcp.bycy.mi.charter.com. [96.35.96.22])         by mx.google.com with ESMTPSA id qn10sm11305953igc.6.2013.06.01.19.03.57         for kevin@mydomain.com         (version=TLSv1 cipher=ECDHE-RSA-RC4-SHA bits=128/128);         Sat, 01 Jun 2013 19:03:58 -0700 (PDT) Message-ID: [EMAIL="51AAA80E.50705@gmail.com"]<51AAA80E.50705@gmail.com>[/EMAIL] Date: Sat, 01 Jun 2013 22:03:58 -0400 From: Kevin Salerno [EMAIL="myemail@gmail.com"]myemail@gmail.com[/EMAIL] User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64; rv:17.0) Gecko/20130509 Thunderbird/17.0.6 MIME-Version: 1.0 To: [EMAIL="kevin@mydomain.com"]kevin@mydomain.com[/EMAIL] Subject: test email Content-Type: text/plain; charset=ISO-8859-1; format=flowed Content-Transfer-Encoding: 7bit  can you read this [/FONT]
```[FONT=-moz-fixed]

no errors in mail.err

a bit of my mail.log 
[/FONT]

```

Jun  3 18:03:04 mydomain spamd[1793]: spamd: server pid: 1793
Jun  3 18:03:04 mydomain spamd[1793]: spamd: server successfully spawned child process, pid 1943
Jun  3 18:03:04 mydomain spamd[1793]: spamd: server successfully spawned child process, pid 1944
Jun  3 18:03:04 mydomain spamd[1793]: prefork: child states: IS
Jun  3 18:03:04 mydomain spamd[1793]: prefork: child states: II
Jun  3 18:03:07 mydomain postfix/master[2413]: daemon started -- version 2.9.6, configuration /etc/postfix
Jun  4 07:31:36 mydomain spamd[1793]: spamd: server hit by SIGHUP, restarting
Jun  4 07:31:36 mydomain spamd[1793]: spamd: child [1943] killed successfully: interrupted, signal 2 (0002)
Jun  4 07:31:36 mydomain spamd[1793]: spamd: child [1944] killed successfully: interrupted, signal 2 (0002)
Jun  4 07:31:36 mydomain spamd[1793]: logger: removing stderr method
Jun  4 07:31:42 mydomain spamd[13099]: pyzor: [13100] error: TERMINATED, signal 15 (000f)
Jun  4 07:31:42 mydomain spamd[13099]: spamd: server started on port 783/tcp (running version 3.3.2)
Jun  4 07:31:42 mydomain spamd[13099]: spamd: server pid: 13099
Jun  4 07:31:42 mydomain spamd[13099]: spamd: server successfully spawned child process, pid 13103
Jun  4 07:31:42 mydomain spamd[13099]: spamd: server successfully spawned child process, pid 13104
Jun  4 07:31:42 mydomain spamd[13099]: prefork: child states: IS
Jun  4 07:31:42 mydomain spamd[13099]: prefork: child states: II

```

---

### Post by Cheesemill on 2013-06-04
At the moment the host mail.mydomain.com doesn't exist, you don't have a DNS entry for it in your zone file.

You need to create either an A record for mail.mydomain.com that points to your IP address, or a CNAME record for mail.mydomain.com that points to @.

---

### Post by kevinxsalerno on 2013-06-04
> **Cheesemill said:**
> At the moment the host mail.mydomain.com doesn't exist, you don't have a DNS entry for it in your zone file.

You need to create either an A record for mail.mydomain.com that points to your IP address, or a CNAME record for mail.mydomain.com that points to @.

Thanks for the response.

So now I have

```

CNames

Host: mail        points to: @
host: smtp       points to: @

```

I will allow the DNS servers to update and then retry. I believe I am still having error

---

### Post by kevinxsalerno on 2013-06-04
Now I am having relay access problems...

```


Delivery to the following recipient failed permanently:       kevin@mydomain.com  Technical details of permanent failure:  Google tried to deliver your message, but it was rejected by the server for the recipient domain mydomain.com by mail.mydomain.com. [66.227.234.53].  The error that the other server returned was: 554 5.7.1 kevin@mydomain.com: Relay access denied 
```


Some of my log file (recent towards bottom, bold is the stuff regarding the 2 messages I sent):

```

[B]Jun  4 17:33:07 mydomain postfix/smtpd[18261]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Jun  4 17:33:07 mydomain postfix/smtpd[18261]: connect from mail-ie0-f181.google.com[209.85.223.181]
Jun  4 17:33:18 mydomain postfix/smtpd[18261]: warning: 181.223.85.209.dnsbl.njabl.org: RBL lookup error: Host or domain name not found. Name service error for name=181.223.85.209.dnsbl.njabl.org type=A: Host not found, try again
Jun  4 17:33:18 mydomain postfix/smtpd[18261]: NOQUEUE: reject: RCPT from mail-ie0-f181.google.com[209.85.223.181]: 554 5.7.1 <joe.barge@mydomain.com>: Relay access denied; from=<myemail@myemail.com> to=<kevin@mydomain.com> proto=ESMTP helo=<mail-ie0-f181.google.com>
Jun  4 17:33:18 mydomain postfix/smtpd[18261]: disconnect from mail-ie0-f181.google.com[209.85.223.181]
Jun  4 17:33:41 mydomain postfix/smtpd[18261]: connect from mta41.charter.net[216.33.127.83]
Jun  4 17:33:52 mydomain postfix/smtpd[18261]: warning: 83.127.33.216.dnsbl.njabl.org: RBL lookup error: Host or domain name not found. Name service error for name=83.127.33.216.dnsbl.njabl.org type=A: Host not found, try again
Jun  4 17:33:52 mydomain postfix/smtpd[18261]: NOQUEUE: reject: RCPT from mta41.charter.net[216.33.127.83]: 554 5.7.1 <kevin@my domain.com>: Relay access denied; from=<kevinxsalerno@charter.net> to=<kevin@mydomain.com> proto=ESMTP helo=<mta41.charter.net>
Jun  4 17:33:52 mydomain postfix/smtpd[18261]: disconnect from mta41.charter.net[216.33.127.83]
Jun  4 17:34:52 mydomain postfix/smtpd[18261]: connect from mail-vc0-f172.google.com[209.85.220.172]
Jun  4 17:34:52 mydomain postfix/smtpd[18261]: Anonymous TLS connection established from mail-vc0-f172.google.com[209.85.220.172]: TLSv1 with cipher ECDHE-RSA-RC4-SHA (128/128 bits)
Jun  4 17:35:03 mydomain postfix/smtpd[18261]: warning: 172.220.85.209.dnsbl.njabl.org: RBL lookup error: Host or domain name not found. Name service error for name=172.220.85.209.dnsbl.njabl.org type=A: Host not found, try again
Jun  4 17:35:03 mydomain postfix/smtpd[18261]: NOQUEUE: reject: RCPT from mail-vc0-f172.google.com[209.85.220.172]: 554 5.7.1 <kevin@mydomain.com>: Relay access denied; from=<kevin@myemail.com> to=<kevin@mydomain.com> proto=ESMTP helo=<mail-vc0-f172.google.com>
Jun  4 17:35:03 mydomain postfix/smtpd[18261]: disconnect from mail-vc0-f172.google.com[209.85.220.172][/B]


```

---

### Post by kevinxsalerno on 2013-06-05
> **kevinxsalerno said:**
> Now I am having relay access problems...

```


Delivery to the following recipient failed permanently:       kevin@mydomain.com  Technical details of permanent failure:  Google tried to deliver your message, but it was rejected by the server for the recipient domain mydomain.com by mail.mydomain.com. [66.227.234.53].  The error that the other server returned was: 554 5.7.1 kevin@mydomain.com: Relay access denied 
```


Some of my log file (recent towards bottom, bold is the stuff regarding the 2 messages I sent):

```

[B]Jun  4 17:33:07 mydomain postfix/smtpd[18261]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Jun  4 17:33:07 mydomain postfix/smtpd[18261]: connect from mail-ie0-f181.google.com[209.85.223.181]
Jun  4 17:33:18 mydomain postfix/smtpd[18261]: warning: 181.223.85.209.dnsbl.njabl.org: RBL lookup error: Host or domain name not found. Name service error for name=181.223.85.209.dnsbl.njabl.org type=A: Host not found, try again
Jun  4 17:33:18 mydomain postfix/smtpd[18261]: NOQUEUE: reject: RCPT from mail-ie0-f181.google.com[209.85.223.181]: 554 5.7.1 <joe.barge@mydomain.com>: Relay access denied; from=<myemail@myemail.com> to=<kevin@mydomain.com> proto=ESMTP helo=<mail-ie0-f181.google.com>
Jun  4 17:33:18 mydomain postfix/smtpd[18261]: disconnect from mail-ie0-f181.google.com[209.85.223.181]
Jun  4 17:33:41 mydomain postfix/smtpd[18261]: connect from mta41.charter.net[216.33.127.83]
Jun  4 17:33:52 mydomain postfix/smtpd[18261]: warning: 83.127.33.216.dnsbl.njabl.org: RBL lookup error: Host or domain name not found. Name service error for name=83.127.33.216.dnsbl.njabl.org type=A: Host not found, try again
Jun  4 17:33:52 mydomain postfix/smtpd[18261]: NOQUEUE: reject: RCPT from mta41.charter.net[216.33.127.83]: 554 5.7.1 <kevin@my domain.com>: Relay access denied; from=<kevinxsalerno@charter.net> to=<kevin@mydomain.com> proto=ESMTP helo=<mta41.charter.net>
Jun  4 17:33:52 mydomain postfix/smtpd[18261]: disconnect from mta41.charter.net[216.33.127.83]
Jun  4 17:34:52 mydomain postfix/smtpd[18261]: connect from mail-vc0-f172.google.com[209.85.220.172]
Jun  4 17:34:52 mydomain postfix/smtpd[18261]: Anonymous TLS connection established from mail-vc0-f172.google.com[209.85.220.172]: TLSv1 with cipher ECDHE-RSA-RC4-SHA (128/128 bits)
Jun  4 17:35:03 mydomain postfix/smtpd[18261]: warning: 172.220.85.209.dnsbl.njabl.org: RBL lookup error: Host or domain name not found. Name service error for name=172.220.85.209.dnsbl.njabl.org type=A: Host not found, try again
Jun  4 17:35:03 mydomain postfix/smtpd[18261]: NOQUEUE: reject: RCPT from mail-vc0-f172.google.com[209.85.220.172]: 554 5.7.1 <kevin@mydomain.com>: Relay access denied; from=<kevin@myemail.com> to=<kevin@mydomain.com> proto=ESMTP helo=<mail-vc0-f172.google.com>
Jun  4 17:35:03 mydomain postfix/smtpd[18261]: disconnect from mail-vc0-f172.google.com[209.85.220.172][/B]


```


mysql_virtual_domains_maps.cf had the wrong settings (literally copied an entire different file on accident). The postfix service was blind. This is solved.

---

