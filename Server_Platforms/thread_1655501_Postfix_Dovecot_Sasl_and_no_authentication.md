---
title: "Postfix Dovecot Sasl and no authentication"
date: 2010-12-29
forum: Server Platforms
---

### Post by ragnarok189 on 2010-12-29
I have been following tutorials for 2 days straight now, and have already started fresh on three servers. After what appears that I have configured everything right, login authentication continues to fail.

The howto's that I have followed are.
[HowToPostfixAndDovecotSASL]("http://wiki.dovecot.org/HowTo/PostfixAndDovecotSASL")
[Postfix and Dovecot on Ubuntu Dapper Drake]("http://adomas.org/2006/08/postfix-dovecot/")
[Quick Linux Server Installation]("http://www.mysql-apache-php.com/")

Those tutorials that cover more than Postfix, Dovecot, and SASL; I just pulled the instructions related to those services.

Basically, I am trying to set up my own mail server that accepts IMAP or POP3 over TLS for my own hosting of [EGroupWare]("http://www.egroupware.org/").

I have an entire virtual machine in KVM dedicated to it.

Here is my /etc/postfix/main.cf
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

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = rajesh.domain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = serenity.domain.com, rajesh.domain.com, localhost.domain.com, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination
broken_sasl_auth_clients = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_delay_reject = no
smtpd_tls_security_level = encrypt

```

And here is a snippet of my /etc/dovecot/dovecot.conf
```

auth default {
 mechanisms = plain
passdb pam {
  }
userdb passwd {
  }
user = root
 socket listen {
  client {
  path = /var/spool/postfix/private/auth
  mode = 0660
  user = postfix
  group = postfix
  }
 }
 !include_try /etc/dovecot/auth.d/*.auth
}

```

Here is my /etc/pam.d/dovecot file
```

#%PAM-1.0

---%<-------------------------------------------------------------------------
auth    required        pam_unix.so nullok
account required        pam_unix.so
---%<-------------------------------------------------------------------------

```

Here is my output of /var/log/mail.warn
```
Dec 29 21:46:04 rajesh postfix/master[17499]: warning: process /usr/lib/postfix/smtpd pid 18884 exit status 1
Dec 29 21:46:04 rajesh postfix/master[17499]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec 29 21:51:34 rajesh postfix/smtpd[19419]: warning: unknown[10.0.10.251]: SASL plain authentication failed: 
Dec 29 21:52:28 rajesh postfix/smtpd[19419]: warning: unknown[10.0.10.251]: SASL user authentication failed: Invalid authentication mechanism
Dec 29 21:52:37 rajesh postfix/smtpd[19419]: warning: unknown[10.0.10.251]: SASL plain authentication failed: Invalid authentication mechanism
Dec 29 21:53:03 rajesh postfix/smtpd[19419]: warning: unknown[10.0.10.251]: SASL plain authentication failed: Invalid authentication mechanism
Dec 29 21:53:31 rajesh postfix/smtpd[19419]: warning: unknown[10.0.10.251]: SASL plain authentication failed: 
Dec 29 21:55:26 rajesh postfix/smtpd[19419]: warning: unknown[10.0.10.251]: SASL plain authentication failed: 
Dec 29 21:57:01 rajesh postfix/smtpd[19419]: warning: unknown[10.0.10.251]: SASL login authentication failed:
```

After trying to run this
```
openssl s_client -connect serenity.domain.com:25 -starttls smtp
auth plain AHRlc3RlcnNvbgBwYXNzd2Q=

```

Which returns this
```
535 5.7.8 Error: authentication failed:
```

If there are any other config files that would help ya'll figure this out, let me know.

And thank you so much for everybody who is willing to read through this and offer their expertise.

---

### Post by elico on 2010-12-29
why are you trying so hard?

do you want your email connection to be encrypted ?
start without encryption just with mutt or THUNDERBIRD... and go on.

---

### Post by stmiller on 2010-12-29
Of course you should use SSL for email.

What is your /etc/default/saslauthd ?

---

### Post by ragnarok189 on 2010-12-30
> why are you trying so hard?
I'm trying so hard because encryption is very important to me. This is a solution that I am putting together for my company. I have already tried non SSL/TLS to much the same results.

My /etc/default/saslauthd is
```
#
# Settings for saslauthd daemon
# Please read /usr/share/doc/sasl2-bin/README.Debian for details.
#

# Should saslauthd run automatically on startup? (default: no)
START=no

# Description of this saslauthd instance. Recommended.
# (suggestion: SASL Authentication Daemon)
DESC="SASL Authentication Daemon"

# Short name of this saslauthd instance. Strongly recommended.
# (suggestion: saslauthd)
NAME="saslauthd"

# Which authentication mechanisms should saslauthd use? (default: pam)
#
# Available options in this Debian package:
# getpwent  -- use the getpwent() library function
# kerberos5 -- use Kerberos 5
# pam       -- use PAM
# rimap     -- use a remote IMAP server
# shadow    -- use the local shadow password file
# sasldb    -- use the local sasldb database file
# ldap      -- use LDAP (configuration is in /etc/saslauthd.conf)
#
# Only one option may be used at a time. See the saslauthd man page
# for more information.
#
# Example: MECHANISMS="pam"
MECHANISMS="pam"

# Additional options for this mechanism. (default: none)
# See the saslauthd man page for information about mech-specific options.
MECH_OPTIONS=""

# How many saslauthd processes should we run? (default: 5)
# A value of 0 will fork a new process for each connection.
THREADS=5

# Other options (default: -c -m /var/run/saslauthd)
# Note: You MUST specify the -m option or saslauthd won't run!
#
# WARNING: DO NOT SPECIFY THE -d OPTION.
# The -d option will cause saslauthd to run in the foreground instead of as
# a daemon. This will PREVENT YOUR SYSTEM FROM BOOTING PROPERLY. If you wish
# to run saslauthd in debug mode, please run it by hand to be safe.
#
# See /usr/share/doc/sasl2-bin/README.Debian for Debian-specific information.
# See the saslauthd man page and the output of 'saslauthd -h' for general
# information about these options.
#
# Example for postfix users: "-c -m /var/spool/postfix/var/run/saslauthd"
OPTIONS="-c -m /var/run/saslauthd"

```

---

### Post by HermanAB on 2010-12-30
Hmm, you can keep fighting the good battle for another two weeks or so, or you can install Citadel.  The Citadel Easy Install script takes about 20 minutes, after which everything Just Works (TM).  Citadel also supports all mail protocols ever invented and it integrates easily with SpamAssassin, ClamAV and the Spamhaus Zen RBL.

I gave up with Postfix about 10 years ago.  It is a huge improvement on Sendmail, but it is still strictly for masochists.

---

### Post by stmiller on 2010-12-30
First make sure sasl is working ok. You can run

```
testsaslauthd -u username -p password
```

And see if that works. Then go from there.

My /etc/default/saslauthd has this at the bottom:

(Commented out default options, added postfix entry)

```
#OPTIONS="-c -m /var/run/saslauthd"
OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd"

```

---

