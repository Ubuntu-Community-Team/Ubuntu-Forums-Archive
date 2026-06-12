---
title: "postfix+dovecot not working as expected"
date: 2010-11-08
forum: Server Platforms
---

### Post by Edifier1007 on 2010-11-08
Hi all,

I have tried to find solution in existing posts but could not specifically find any with my kind of issues and hence a new post on oft repeated subject !! -- and apologies for  a long long post here.

Here is where I am ..

On a AMD 64bit machine - I have ubuntu 10.10 desktop installed. I want this development machine to support virtual mailboxes so that I can use them from multiple apps and create real life deployment situations.

I installed postfix + dovecot following the tutorials available here and current state is - I can send mails using telnet sessions and I see that the mail files are getting created in /Maildir form as I have directed in the conf files. I have configured Thunderbird mail client as well. 

Issue #1: Mail sending works from Thunderbird but it always responds back with 'No mail on server' message when I try to receive mails. SMTP is configured with STARTTLS and POP3 with None (i.e. plain text password).

Issue #2: Also, while going thru conf, logs and during testing - I found a few things which defer in this installation for authentication. I have given the session transcripts here.

Issue #3: That being major issue - I also want to configure my virtual users to use TB client to access their mails - I did not find any tutorials or pointers towards that in my search for past few days. Any pointers here would help. If I send mails to a non-Unix virtual user - the mail gets stored into /home/vmail/<domain>/<user>/new directory.

Here are the conf files. 

main.cf for postfix
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
smtp_use_tls = yes
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = localhost.localdomain
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myorigin, localhost.localdomin, localhost
relayhost = 
mynetworks = 127.0.0.1/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
default_transport = error
relay_transport = error
home_mailbox = Maildir/
mailbox_command = 
inet_protocols = all


# addition of virtual aliases 
virtual_alias_domains = localhost.localdomain 
virtual_alias_maps = hash:/etc/postfix/virtual
# addition of virutal 
virtual_mailbox_domains = /etc/postfix/vhosts
virtual_mailbox_base = /home/vmail
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000

smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_sasl_authenticated permit_mynetworks reject_unauth_destination
smtpd_tls_auth_only = yes
broken_sasl_auth_clients = yes
smtpd_sasl_local_domain = localhost.localdomain
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 2
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
debug_peer_list = localhost

smtpd_sasl_security_options = noanonymous

```

dovecot.conf
```

base_dir = /var/run/dovecot/
protocols = imap pop3 imaps pop3s
disable_plaintext_auth = yes
shutdown_clients = yes
log_path = /var/log/dovecot
info_log_path = /var/log/dovecot.info
log_timestamp = "%Y-%m-%d %H:%M:%S "
#ssl_disable = no
ssl = no
#In Ubuntu 10.04 Lucid Lynx: ssl = no
login_dir = /var/run/dovecot/login
login_chroot = yes
login_user = dovecot
login_greeting = Dovecot ready.
mail_location = maildir:/home/vmail/%d/%n
mmap_disable = no
valid_chroot_dirs = /var/spool/vmail
protocol imap {
  login_executable = /usr/lib/dovecot/imap-login
  mail_executable = /usr/lib/dovecot/imap
}
protocol pop3 {
  login_executable = /usr/lib/dovecot/pop3-login
  mail_executable = /usr/lib/dovecot/pop3
pop3_uidl_format = %08Xu%08Xv
}

auth_executable = /usr/lib/dovecot/dovecot-auth
auth_verbose = yes
auth_default_realm=localhost
auth default {
  mechanisms = plain cram-md5 login
  passdb passwd-file {
    args = /etc/dovecot/passwd
  }
  userdb passwd-file {
    args = /etc/dovecot/users
  }
  user = root
socket listen {
    master {
        path = /var/run/dovecot/auth-master
        mode = 0600
        user = vmail
    }

    client {
        path = /var/spool/postfix/private/auth
        mode = 0660
        user = postfix
        group = postfix
    }
}
}

ssl_cert_file = /etc/postfix/smtpd.cert
ssl_key_file = /etc/postfix/smptd.key


```

telnet sessions  - sending mail
```

root@trivedis:~# telnet localhost.localdomain 25
Trying ::1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 localhost.localdomain ESMTP Postfix (Ubuntu)
ehlo localhost.localdomain
250-localhost.localdomain
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from:tapant@localhost.localdomain 
250 2.1.0 Ok
rcpt to:tdtrivedi@localhost.localdomain
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
subject: testing postfix+dovecot

Hi 
this is a test message .
Re Admin
.
250 2.0.0 Ok: queued as CC860A41B2B
quit
221 2.0.0 Bye
Connection closed by foreign host.
root@trivedis:~# ls /home/tdtrivedi/Maildir/new
1289109343.V801I11a02d1M841130.localhost.localdomain  1289188776.V801I11a058aM682843.localhost.localdomain
1289138078.V801I11a066cM267659.localhost.localdomain
root@trivedis:~# cat  /home/tdtrivedi/Maildir/new/1289188776.V801I11a058aM682843.localhost.localdomain 
Return-Path: <tapant@localhost.localdomain>
X-Original-To: tdtrivedi@localhost.localdomain
Delivered-To: tdtrivedi@localhost.localdomain
Received: from localhost.localdomain (unknown [IPv6:::1])
	by localhost.localdomain (Postfix) with ESMTP id CC860A41B2B
	for <tdtrivedi@localhost.localdomain>; Mon,  8 Nov 2010 09:28:58 +0530 (IST)
subject: testing postfix+dovecot
Message-Id: <20101108035909.CC860A41B2B@localhost.localdomain>
Date: Mon,  8 Nov 2010 09:28:58 +0530 (IST)
From: tapant@localhost.localdomain
To: undisclosed-recipients:;

Hi 
this is a test message .
Re Admin

```

telnet session - pop3 check
```

root@trivedis:~# telnet localhost.localdomain pop3
Trying ::1...
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
+OK Dovecot ready.
[B]auth
+OK
PLAIN
CRAM-MD5
LOGIN[/B]
.
quit
+OK Logging out
Connection closed by foreign host.

```

*** Issues that I see above -- ehlo for localhost earlier does not give me AUTH responses but when I do connect for pop3 - they are shown as configured.  I did not see a comment anywhere stating this is expected behaviour. See what I get if I try AUTH command while connected to smtp. 

```
root@trivedis:~# telnet localhost.localdomain 25
Trying ::1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 localhost.localdomain ESMTP Postfix (Ubuntu)
auth
[B]503 5.5.1 Error: authentication not enabled
[/B]quit
221 2.0.0 Bye
Connection closed by foreign host.
root@trivedis:~# 

```

---

### Post by Edifier1007 on 2010-11-11
Ok. so update on this is ... I had to reinstall dovecot for this to be able to work. 

Answers to my Q's 

#1 - TB setup - after reinstall, TB is able to find the SMTP and POP3 servers automatically. They work in STARTTLS mode.

#2 Seems like 'auth not enabled' is standard message once you install dovecot. The earlier settings get overwritten... and this is normal - though, I need a confirmation on this one. 

#3 .. still working on this one !! no solution yet.. 

... and I install things using Software Centre (as against all earlier attempts of using apt-get (not that this should be an issue - IMHO).

---

