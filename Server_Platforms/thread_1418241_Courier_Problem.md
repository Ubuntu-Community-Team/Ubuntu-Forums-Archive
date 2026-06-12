---
title: "Courier Problem"
date: 2010-02-28
forum: Server Platforms
---

### Post by WardLoockx on 2010-02-28
Hello,

I'm trying to setup a mailserver using postfix. I'm still having 2problems

== PROBLEM1 ==
I'm unable to connect to imap or pop. I'm using authdaemon that (should) check the mysql tables for auth. Looks like the IMAP/POP daemons aren't running and can't find any errors..

I'm trying to start them with this command
/etc/init.d/courier-imap start
but I don't get any output.. 

When I see what things are running of courier I found this 
root     15916  0.0  0.0   1988   628 ?        S    18:35   0:00 /usr/lib/courier/courier-authlib/authdaemond
root     15917  0.0  0.0   1988   236 ?        S    18:35   0:00 /usr/lib/courier/courier-authlib/authdaemond
root     15918  0.0  0.0   1988   236 ?        S    18:35   0:00 /usr/lib/courier/courier-authlib/authdaemond
root     15919  0.0  0.0   1988   236 ?        S    18:35   0:00 /usr/lib/courier/courier-authlib/authdaemond
root     15920  0.0  0.0   1988   236 ?        S    18:35   0:00 /usr/lib/courier/courier-authlib/authdaemond
root     15921  0.0  0.0   1988   236 ?        S    18:35   0:00 /usr/lib/courier/courier-authlib/authdaemond

Anybody knows how I can start them or find errors in logs ? Because can't find any info in logfiles..

== Problem 2 ==
The postfix SMTP server is running and I can connect to it using telnet on the VPS machine. But when I try to telnet it from my own computer the connections isn't denied but I get an empty screen and no info.. When connecting an email client (thunderbird) I'm unable to connect too.

== Config files ==

main.cf
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h
unknown_local_recipient_reject_code = 450


# how long to keep message on queue before return as failed.
maximal_queue_lifetime = 7d
readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.html-5.be
alias_maps = /etc/postfix/mysql-aliases.cf
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.html-5.be, html-5.be,www.html-5.be, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = 109.70.1.238
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
# max and min time in seconds between retries if connection failed
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s

# how long to wait when servers connect before receiving rest of data
smtp_helo_timeout = 60s

# how many address can be used in one message.
smtpd_recipient_limit = 35

# how many error before back off.
smtpd_soft_error_limit = 3

# how many max errors before blocking it.
smtpd_hard_error_limit = 12


# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
# Requirements for the sender details
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_un                                auth_pipelining, permit

# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dn                                sbl.njabl.org

# Requirement for the recipient address
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination


# require proper helo at connections
smtpd_helo_required = yes

# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes
smtpd_data_restrictions = reject_unauth_pipeliningi

home_mailbox = /var/spool/mailboxes/
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virt                                ual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $re                                located_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
ward@srv1:/etc/postfix$
ward@srv1:/etc/postfix$ cat main.cf
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h
unknown_local_recipient_reject_code = 450


# how long to keep message on queue before return as failed.
maximal_queue_lifetime = 7d
readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.html-5.be
alias_maps = /etc/postfix/mysql-aliases.cf
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.html-5.be, html-5.be,www.html-5.be, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = 109.70.1.238
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
# max and min time in seconds between retries if connection failed
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s

# how long to wait when servers connect before receiving rest of data
smtp_helo_timeout = 60s

# how many address can be used in one message.
smtpd_recipient_limit = 35

# how many error before back off.
smtpd_soft_error_limit = 3

# how many max errors before blocking it.
smtpd_hard_error_limit = 12


# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
# Requirements for the sender details
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org

# Requirement for the recipient address
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination


# require proper helo at connections
smtpd_helo_required = yes

# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes
smtpd_data_restrictions = reject_unauth_pipeliningi

home_mailbox = /var/spool/mailboxes/
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps

```


master.cf
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
smtp      inet  n       -       -       -       -       smtpd
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
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
proxywrite unix -       -       n       -       1       proxymap
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
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}


```

imapd courier 
```

# This setting controls how often
# the server polls for changes to the folder, in IDLE mode (in seconds).

IMAP_IDLE_TIMEOUT=60

##NAME: IMAP_MAILBOX_SANITY_CHECK:0
#
# Sanity check -- make sure home directory and maildir's ownership matches
# the IMAP server's effective uid and gid

IMAP_MAILBOX_SANITY_CHECK=1

##NAME: IMAP_CAPABILITY_TLS:0
#
# The following setting will advertise SASL PLAIN authentication after
# STARTTLS is established.  If you want to allow SASL PLAIN authentication
# with or without TLS then just comment this out, and add AUTH=PLAIN to
# IMAP_CAPABILITY

IMAP_CAPABILITY_TLS="$IMAP_CAPABILITY AUTH=PLAIN"

##NAME: IMAP_TLS_ORIG:0
#
# For use by webadmin

IMAP_CAPABILITY_TLS_ORIG="$IMAP_CAPABILITY_ORIG AUTH=PLAIN"

##NAME: IMAP_DISABLETHREADSORT:0
#
# Set IMAP_DISABLETHREADSORT to disable the THREAD and SORT commands -
# server side sorting and threading.
#
# Those capabilities will still be advertised, but the server will reject
# them.  Set this option if you want to disable all the extra load from
# server-side threading and sorting.  Not advertising those capabilities
# will simply result in the clients reading the entire folder, and sorting
# it on the client side.  That will still put some load on the server.
# advertising these capabilities, but rejecting the commands, will stop this
# silliness.
#

IMAP_DISABLETHREADSORT=0

##NAME: IMAP_CHECK_ALL_FOLDERS:0
#
# Set IMAP_CHECK_ALL_FOLDERS to 1 if you want the server to check for new
# mail in every folder.  Not all IMAP clients use the IMAP's new mail
# indicator, but some do.  Normally new mail is checked only in INBOX,
# because it is a comparatively time consuming operation, and it would be
# a complete waste of time unless mail filters are used to deliver
# mail directly to folders.
#
# When IMAP clients are used which support new mail indication, and when
# mail filters are used to sort incoming mail into folders, setting
# IMAP_CHECK_ALL_FOLDERS to 1 will allow IMAP clients to announce new
# mail in folders.  Note that this will result in slightly more load on the
# server.
#

IMAP_CHECK_ALL_FOLDERS=0

##NAME: IMAP_OBSOLETE_CLIENT:0
#
# Set IMAP_OBSOLETE_CLIENT if your IMAP client expects \\NoInferiors to mean
# what \\HasNoChildren really means.

IMAP_OBSOLETE_CLIENT=0

##NAME: IMAP_UMASK:0
#
# IMAP_UMASK sets the umask of the server process.  The value of IMAP_UMASK is
# simply passed to the "umask" command.  The default value is 022.
#
# This feature is mostly useful for shared folders, where the file permissions
# of the messages may be important.

IMAP_UMASK=022

##NAME: IMAP_ULIMITD:0
#
# IMAP_ULIMITD sets the maximum size of the data segment of the server
# process.  The value of IMAP_ULIMITD is simply passed to the "ulimit -d"
# command (or ulimit -v).  The argument to ulimi sets the upper limit on the
# size of the data segment of the server process, in kilobytes.  The default
# value of 65536 sets a very generous limit of 64 megabytes, which should
# be more than plenty for anyone.
#
# This feature is used as an additional safety check that should stop
# any potential denial-of-service attacks that exploit any kind of
# a memory leak to exhaust all the available memory on the server.
# It is theoretically possible that obscenely huge folders will also
# result in the server running out of memory when doing server-side
# sorting (by my calculations you have to have at least 100,000 messages
# in a single folder, for that to happen).

IMAP_ULIMITD=65536

##NAME: IMAP_USELOCKS:0
#
# Setting IMAP_USELOCKS to 1 will use dot-locking to support concurrent
# multiple access to the same folder.  This incurs slight additional
# overhead.  Concurrent multiple access will still work without this setting,
# however occasionally a minor race condition may result in an IMAP client
# downloading the same message twice, or a keyword update will fail.
#
# IMAP_USELOCKS=1 is strongly recommended when shared folders are used.

IMAP_USELOCKS=1

##NAME: IMAP_SHAREDINDEXFILE:0
#
# The index of all accessible folders.  Do not change this setting unless
# you know what you're doing.  See README.sharedfolders for additional
# information.

IMAP_SHAREDINDEXFILE=/etc/courier/shared/index

##NAME: IMAP_ENHANCEDIDLE:0
#
# If Courier was compiled with the File Alteration Monitor, setting
# IMAP_ENHANCEDIDLE to 1 enables enhanced IDLE mode, where multiple
# clients may open the same folder concurrently, and receive updates to
# folder contents in realtime.  See the imapd(8) man page for additional
# information.
#
# IMPORTANT: IMAP_USELOCKS *MUST* also be set to 1, and IDLE must be included
# in the IMAP_CAPABILITY list.
#

IMAP_ENHANCEDIDLE=0

##NAME: IMAP_TRASHFOLDERNAME:0
#
# The name of the magic trash Folder.  For MSOE compatibility,
# you can set IMAP_TRASHFOLDERNAME="Deleted Items".
#
# IMPORTANT:  If you change this, you must also change IMAP_EMPTYTRASH

IMAP_TRASHFOLDERNAME=Trash

##NAME: IMAP_EMPTYTRASH:0
#
# The following setting is optional, and causes messages from the given
# folder to be automatically deleted after the given number of days.
# IMAP_EMPTYTRASH is a comma-separated list of folder:days.  The default
# setting, below, purges 7 day old messages from the Trash folder.
# Another useful setting would be:
#
# IMAP_EMPTYTRASH=Trash:7,Sent:30
#
# This would also delete messages from the Sent folder (presumably copies
# of sent mail) after 30 days.  This is a global setting that is applied to
# every mail account, and is probably useful in a controlled, corporate
# environment.
#
# Important: the purging is controlled by CTIME, not MTIME (the file time
# as shown by ls).  It is perfectly ordinary to see stuff in Trash that's
# a year old.  That's the file modification time, MTIME, that's displayed.
# This is generally when the message was originally delivered to this
# mailbox.  Purging is controlled by a different timestamp, CTIME, which is
# changed when the file is moved to the Trash folder (and at other times too).
#
# You might want to disable this setting in certain situations - it results
# in a stat() of every file in each folder, at login and logout.
#

IMAP_EMPTYTRASH=Trash:7

##NAME: IMAP_MOVE_EXPUNGE_TO_TRASH:0
#
# Set IMAP_MOVE_EXPUNGE_TO_TRASH to move expunged messages to Trash.  This
# effectively allows an undo of message deletion by fishing the deleted
# mail from trash.  Trash can be manually expunged as usually, and mail
# will get automatically expunged from Trash according to IMAP_EMPTYTRASH.
#
# NOTE: shared folders are still expunged as usual.  Shared folders are
# not affected.
#

IMAP_MOVE_EXPUNGE_TO_TRASH=0


##NAME: OUTBOX:0
#
# The next set of options deal with the "Outbox" enhancement.
# Uncomment the following setting to create a special folder, named
# INBOX.Outbox
#
# OUTBOX=.Outbox

##NAME: SENDMAIL:0
#
# If OUTBOX is defined, mail can be sent via the IMAP connection by copying
# a message to the INBOX.Outbox folder.  For all practical matters,
# INBOX.Outbox looks and behaves just like any other IMAP folder.  If this
# folder doesn't exist it must be created by the IMAP mail client, just
# like any other IMAP folder.  The kicker: any message copied or moved to
# this folder is will be E-mailed by the Courier-IMAP server, by running
# the SENDMAIL program.  Therefore, messages copied or moved to this
# folder must be well-formed RFC-2822 messages, with the recipient list
# specified in the To:, Cc:, and Bcc: headers.  Courier-IMAP relies on
# SENDMAIL to read the recipient list from these headers (and delete the Bcc:
# header) by running the command "$SENDMAIL -oi -t -f $SENDER", with the
# message piped on standard input.  $SENDER will be the return address
# of the message, which is set by the authentication module.
#
# DO NOT MODIFY SENDMAIL, below, unless you know what you're doing.
#

SENDMAIL=/usr/sbin/sendmail

##NAME: HEADERFROM:0
#
# For administrative and oversight purposes, the return address, $SENDER
# will also be saved in the X-IMAP-Sender mail header.  This header gets
# added to the sent E-mail (but it doesn't get saved in the copy of the
# message that's saved in the folder)
#
# WARNING - By enabling OUTBOX above, *every* IMAP mail client will receive
# the magic OUTBOX treatment.  Therefore advance LARTing is in order for
# _all_ of your lusers, until every one of them is aware of this.  Otherwise if
# OUTBOX is left at its default setting - a folder name that might be used
# accidentally - some people may be in for a rude surprise.  You can redefine
# the name of the magic folder by changing OUTBOX, above.  You should do that
# and pick a less-obvious name.  Perhaps brand it with your organizational
# name ( OUTBOX=.WidgetsAndSonsOutbox )

HEADERFROM=X-IMAP-Sender

##NAME: OUTBOX_MULTIPLE_SEND:0
#
# Remove the following comment to allow a COPY of more than one message to
# the Outbox, at a time.
#
# OUTBOX_MULTIPLE_SEND=1

##NAME: IMAPDSTART:0
#
# IMAPDSTART is not used directly.  Rather, this is a convenient flag to
# be read by your system startup script in /etc/rc.d, like this:
#
#  . /etc/courier/imapd
#
#  case x$IMAPDSTART in
#  x[yY]*)
#        /usr/lib/courier/imapd.rc start
#        ;;
#  esac
#
# The default setting is going to be NO, so you'll have to manually flip
# it to yes.

IMAPDSTART=YES

##NAME: MAILDIRPATH:0
#
# MAILDIRPATH - directory name of the maildir directory.
#
MAILDIRPATH=Maildir

```

authdaemonrc
```

##NAME: authdaemonvar:2
#
# authdaemonvar is here, but is not used directly by authdaemond.  It's
# used by various configuration and build scripts, so don't touch it!

authdaemonvar=/var/run/courier/authdaemon

##NAME: DEBUG_LOGIN:0
#
# Dump additional diagnostics to syslog
#
# DEBUG_LOGIN=0   - turn off debugging
# DEBUG_LOGIN=1   - turn on debugging
# DEBUG_LOGIN=2   - turn on debugging + log passwords too
#
# ** YES ** - DEBUG_LOGIN=2 places passwords into syslog.
#
# Note that most information is sent to syslog at level 'debug', so
# you may need to modify your /etc/syslog.conf to be able to see it.

DEBUG_LOGIN=0

##NAME: DEFAULTOPTIONS:0
#
# A comma-separated list of option=value pairs. Each option is applied
# to an account if the account does not have its own specific value for
# that option. So for example, you can set
#   DEFAULTOPTIONS="disablewebmail=1,disableimap=1"
# and then enable webmail and/or imap on individual accounts by setting
# disablewebmail=0 and/or disableimap=0 on the account.

DEFAULTOPTIONS=""

##NAME: LOGGEROPTS:0
#
# courierlogger(1) options, e.g. to set syslog facility
#

LOGGEROPTS=""

##NAME: LDAP_TLS_OPTIONS:0
#
# Options documented in ldap.conf(5) can be set here, prefixed with 'LDAP'.
# Examples:
#
#LDAPTLS_CACERT=/path/to/cacert.pem
#LDAPTLS_REQCERT=demand
#LDAPTLS_CERT=/path/to/clientcert.pem
#LDAPTLS_KEY=/path/to/clientkey.pem
ward@srv1:/etc/courier$
ward@srv1:/etc/courier$ sudo cat authdaemonrc
##VERSION: $Id: authdaemonrc.in,v 1.13 2005/10/05 00:07:32 mrsam Exp $
#
# Copyright 2000-2005 Double Precision, Inc.  See COPYING for
# distribution information.
#
# authdaemonrc created from authdaemonrc.dist by sysconftool
#
# Do not alter lines that begin with ##, they are used when upgrading
# this configuration.
#
# This file configures authdaemond, the resident authentication daemon.
#
# Comments in this file are ignored.  Although this file is intended to
# be sourced as a shell script, authdaemond parses it manually, so
# the acceptable syntax is a bit limited.  Multiline variable contents,
# with the \ continuation character, are not allowed.  Everything must
# fit on one line.  Do not use any additional whitespace for indentation,
# or anything else.

##NAME: authmodulelist:2
#
# The authentication modules that are linked into authdaemond.  The
# default list is installed.  You may selectively disable modules simply
# by removing them from the following list.  The available modules you
# can use are: authuserdb authpam authpgsql authldap authmysql authcustom authpipe

authmodulelist="authmysql"

##NAME: authmodulelistorig:3
#
# This setting is used by Courier's webadmin module, and should be left
# alone

authmodulelistorig="authuserdb authpam authpgsql authldap authmysql authcustom authpipe"

##NAME: daemons:0
#
# The number of daemon processes that are started.  authdaemon is typically
# installed where authentication modules are relatively expensive: such
# as authldap, or authmysql, so it's better to have a number of them running.
# PLEASE NOTE:  Some platforms may experience a problem if there's more than
# one daemon.  Specifically, SystemV derived platforms that use TLI with
# socket emulation.  I'm suspicious of TLI's ability to handle multiple
# processes accepting connections on the same filesystem domain socket.
#
# You may need to increase daemons if as your system load increases.  Symptoms
# include sporadic authentication failures.  If you start getting
# authentication failures, increase daemons.  However, the default of 5
# SHOULD be sufficient.  Bumping up daemon count is only a short-term
# solution.  The permanent solution is to add more resources: RAM, faster
# disks, faster CPUs...

daemons=5

##NAME: authdaemonvar:2
#
# authdaemonvar is here, but is not used directly by authdaemond.  It's
# used by various configuration and build scripts, so don't touch it!

authdaemonvar=/var/run/courier/authdaemon

##NAME: DEBUG_LOGIN:0
#
# Dump additional diagnostics to syslog
#
# DEBUG_LOGIN=0   - turn off debugging
# DEBUG_LOGIN=1   - turn on debugging
# DEBUG_LOGIN=2   - turn on debugging + log passwords too
#
# ** YES ** - DEBUG_LOGIN=2 places passwords into syslog.
#
# Note that most information is sent to syslog at level 'debug', so
# you may need to modify your /etc/syslog.conf to be able to see it.

DEBUG_LOGIN=0

##NAME: DEFAULTOPTIONS:0
#
# A comma-separated list of option=value pairs. Each option is applied
# to an account if the account does not have its own specific value for
# that option. So for example, you can set
#   DEFAULTOPTIONS="disablewebmail=1,disableimap=1"
# and then enable webmail and/or imap on individual accounts by setting
# disablewebmail=0 and/or disableimap=0 on the account.

DEFAULTOPTIONS=""

##NAME: LOGGEROPTS:0
#
# courierlogger(1) options, e.g. to set syslog facility
#

LOGGEROPTS=""

##NAME: LDAP_TLS_OPTIONS:0
#
# Options documented in ldap.conf(5) can be set here, prefixed with 'LDAP'.
# Examples:
#
#LDAPTLS_CACERT=/path/to/cacert.pem
#LDAPTLS_REQCERT=demand
#LDAPTLS_CERT=/path/to/clientcert.pem
#LDAPTLS_KEY=/path/to/clientkey.pem
ward@srv1:/etc/courier$
ward@srv1:/etc/courier$ sudo cat authdaemonrc
##VERSION: $Id: authdaemonrc.in,v 1.13 2005/10/05 00:07:32 mrsam Exp $
#
# Copyright 2000-2005 Double Precision, Inc.  See COPYING for
# distribution information.
#
# authdaemonrc created from authdaemonrc.dist by sysconftool
#
# Do not alter lines that begin with ##, they are used when upgrading
# this configuration.
#
# This file configures authdaemond, the resident authentication daemon.
#
# Comments in this file are ignored.  Although this file is intended to
# be sourced as a shell script, authdaemond parses it manually, so
# the acceptable syntax is a bit limited.  Multiline variable contents,
# with the \ continuation character, are not allowed.  Everything must
# fit on one line.  Do not use any additional whitespace for indentation,
# or anything else.

##NAME: authmodulelist:2
#
# The authentication modules that are linked into authdaemond.  The
# default list is installed.  You may selectively disable modules simply
# by removing them from the following list.  The available modules you
# can use are: authuserdb authpam authpgsql authldap authmysql authcustom authpipe

authmodulelist="authmysql"

##NAME: authmodulelistorig:3
#
# This setting is used by Courier's webadmin module, and should be left
# alone

authmodulelistorig="authuserdb authpam authpgsql authldap authmysql authcustom authpipe"

##NAME: daemons:0
#
# The number of daemon processes that are started.  authdaemon is typically
# installed where authentication modules are relatively expensive: such
# as authldap, or authmysql, so it's better to have a number of them running.
# PLEASE NOTE:  Some platforms may experience a problem if there's more than
# one daemon.  Specifically, SystemV derived platforms that use TLI with
# socket emulation.  I'm suspicious of TLI's ability to handle multiple
# processes accepting connections on the same filesystem domain socket.
#
# You may need to increase daemons if as your system load increases.  Symptoms
# include sporadic authentication failures.  If you start getting
# authentication failures, increase daemons.  However, the default of 5
# SHOULD be sufficient.  Bumping up daemon count is only a short-term
# solution.  The permanent solution is to add more resources: RAM, faster
# disks, faster CPUs...

daemons=5

##NAME: authdaemonvar:2
#
# authdaemonvar is here, but is not used directly by authdaemond.  It's
# used by various configuration and build scripts, so don't touch it!

authdaemonvar=/var/run/courier/authdaemon

##NAME: DEBUG_LOGIN:0
#
# Dump additional diagnostics to syslog
#
# DEBUG_LOGIN=0   - turn off debugging
# DEBUG_LOGIN=1   - turn on debugging
# DEBUG_LOGIN=2   - turn on debugging + log passwords too
#
# ** YES ** - DEBUG_LOGIN=2 places passwords into syslog.
#
# Note that most information is sent to syslog at level 'debug', so
# you may need to modify your /etc/syslog.conf to be able to see it.

DEBUG_LOGIN=0

##NAME: DEFAULTOPTIONS:0
#
# A comma-separated list of option=value pairs. Each option is applied
# to an account if the account does not have its own specific value for
# that option. So for example, you can set
#   DEFAULTOPTIONS="disablewebmail=1,disableimap=1"
# and then enable webmail and/or imap on individual accounts by setting
# disablewebmail=0 and/or disableimap=0 on the account.

DEFAULTOPTIONS=""

##NAME: LOGGEROPTS:0
#
# courierlogger(1) options, e.g. to set syslog facility
#

LOGGEROPTS=""

##NAME: LDAP_TLS_OPTIONS:0
#
# Options documented in ldap.conf(5) can be set here, prefixed with 'LDAP'.
# Examples:
#
#LDAPTLS_CACERT=/path/to/cacert.pem
#LDAPTLS_REQCERT=demand
#LDAPTLS_CERT=/path/to/clientcert.pem
#LDAPTLS_KEY=/path/to/clientkey.pem

```

authmysqlrc
```

MYSQL_SERVER localhost
MYSQL_USERNAME ******
MYSQL_PASSWORD ******
MYSQL_PORT 0
MYSQL_DATABASE mail
MYSQL_USER_TABLE users
MYSQL_CRYPT_PWFIELD password
#MYSQL_CLEAR_PWFIELD password
MYSQL_UID_FIELD 5000
MYSQL_GID_FIELD 5000
MYSQL_LOGIN_FIELD email
MYSQL_HOME_FIELD "/home/vmail"
MYSQL_MAILDIR_FIELD CONCAT(SUBSTRING_INDEX(email,'@',-1),'/',SUBSTRING_INDEX(email,'@',1),'/')
#MYSQL_NAME_FIELD
MYSQL_QUOTA_FIELD quota

```


I did the setup using this guide: [http://linux.justinhartman.com/Postfix_and_Courier_Installation_using_MySQL](http://linux.justinhartman.com/Postfix_and_Courier_Installation_using_MySQL)

If you guys need more info.. just ask! 

Thanks!
Ward

---

