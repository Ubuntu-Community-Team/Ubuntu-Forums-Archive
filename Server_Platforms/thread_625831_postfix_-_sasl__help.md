---
title: "postfix - sasl  help"
date: 2007-11-28
forum: Server Platforms
---

### Post by savages on 2007-11-28
I have read many different post about how to get sasl working with postfix, on gutsy.  I have tested it with  "testsaslauthd" and it works. but when I try using it with postfix it fails.  The main.cf, master.cf, smtpd.conf, saslauthd, and directories are all setup using the instructions on ubuntu.  I have put saslauthd in debug mode but that does not help.  I am sure it is something easy that I can't see.

Help Please!

shaun

---- main.cf ------
 # See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name SavageS
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.savages.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = savages.net, savages.com, hemp.org, mozapps.com, xpsql.org, convictbush.org, tvlinux.org
relayhost = 
mynetworks = 10.10.224.0/27
#mynetworks = 10.10.224.0/27, 24.22.78.244/31
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = 0
inet_interfaces = all
inet_protocols = all
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit

smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client relays.ordb.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org 

smtpd_recipient_restrictions = permit_sasl_authenticated, reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit

smtpd_helo_required = yes

smtpd_delay_reject = yes
disable_vrfy_command = yes

#alias_maps = hash:/etc/postfix/aliases
#alias_database = hash:/etc/postfix/aliases

smtp_sender_dependent_authentication = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
#smtpd_sasl_local_domain = $myhostname
smtpd_sasl_local_domain =
smtpd_sasl_application_name = smtpd
#smtpd_sasl_application_name = var/run/saslauthd/mux
#broken_sasl_auth_clients = yes
#smtp_sasl_authenticated_header = yes
#smtpd_sasl_path = smtpd
smtpd_sasl_exceptions_networks = $mynetworks

---- master.cf ------
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd 
  -o content_filter=spamassassin
submission inet n       -       -       -       -       smtpd
  -o smtpd_enforce_tls=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
smtps     inet  n       -       -       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o content_filter=spamassassin
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
        -o smtp_fallback_relay=
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
mailman         unix    -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
spamassassin    unix    -       n       n       -       -       pipe
  user=spamd argv=/usr/bin/spamc -f -e
  /usr/sbin/sendmail -oi -f ${sender} ${recipient}


---- sasl/smtpd.conf ------
pwcheck_method: saslauthd
mech_list: PLAIN LOGIN

--- default/saslauthd -----
#
# Settings for saslauthd daemon
#

# Should saslauthd run automatically on startup? (default: no)
START=yes

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
THREADS=2

# Other options (default: -c)
# See the saslauthd man page for information about these options.
#
# Example for postfix users: "-c -m /var/spool/postfix/var/run/saslauthd"
# Note: See /usr/share/doc/sasl2-bin/README.Debian
OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd -r"

----  
savages@savages-laptop:~$ telnet mail.savages.net 25Trying 66.93.39.24...
Connected to mail.savages.net.
Escape character is '^]'.
220 mail.savages.net ESMTP Postfix SavageS
ehlo localhost
250-mail.savages.net
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN NTLM CRAM-MD5 DIGEST-MD5
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
auth plain XXXXXXX
535 5.7.0 Error: authentication failed: authentication failure
quit
221 2.0.0 Bye
Connection closed by foreign host.

----- mail.log ----
Nov 28 09:47:35 gateway postfix/smtpd[10256]: warning: SASL authentication failure: Password verification failed
Nov 28 09:47:35 gateway postfix/smtpd[10256]: warning: unknown[70.103.67.194]: SASL plain authentication failed: authentication failure

---- output from test ----
system@gateway:~$ testsaslauthd -f /var/spool/postfix/var/run/saslauthd/mux -u savages -p XXXXXX
0: OK "Success."


I am at a lost

---

### Post by MJN on 2007-11-28
Hi Shaun,

> **savages said:**
> 

----  
savages@savages-laptop:~$ telnet mail.savages.net 25Trying 66.93.39.24...
Connected to mail.savages.net.
Escape character is '^]'.
220 mail.savages.net ESMTP Postfix SavageS
ehlo localhost
250-mail.savages.net
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN NTLM CRAM-MD5 DIGEST-MD5
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
auth plain XXXXXXX
535 5.7.0 Error: authentication failed: authentication failure
quit
221 2.0.0 Bye
Connection closed by foreign host.

You didn't say exactly what XXXXXXX represented - just the password? Whilst the authentication method is PLAIN the username/password actually needs to be Base64 encoded.

Try converting your password beforehand into Base64 using:

```
 perl -MMIME::Base64 -e 'print encode_base64("username\0username\0password");'
```(yes, that is **username**\0**username**\0**password - **substitute as necessary)

Then authenticate with **auth plain dXNlcm5hbWUAdXNlcm5hbWUAcGFzc3dvcmQ= **(as an example).

Apologies if this is what you were doing...

Mathew

---

