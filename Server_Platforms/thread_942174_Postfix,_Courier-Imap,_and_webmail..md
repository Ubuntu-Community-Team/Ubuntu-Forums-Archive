---
title: "Postfix, Courier-Imap, and webmail."
date: 2008-10-08
forum: Server Platforms
---

### Post by issackelly on 2008-10-08
I'm using postfix with a mysql backend for virtual mailboxes.

I used this guide for setup:

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

The server is on EC2, and I started with the most prebuilt ami

Now, I can access my mailboxes for any domain through squirrelmail, but not from imap via these scripts
[http://www.athensfbc.com/imap_tools/](http://www.athensfbc.com/imap_tools/)

Which I routinely use for management, and I can't get to my server via Mail.app (osx) or atmail webmail, only squirrelmail (and directly through the terminal)

I haven't setup postfix in a LONG time.

receiving mesages works fine.

here is my postfix:

main.cf
```
 See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

#smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

readme_directory = no

# TLS parameters
#smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
#smtpd_use_tls=yes
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = ec2-75-101-148-70.compute-1.amazonaws.com
#alias_maps = hash:/etc/aliases
#alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = domU-12-31-35-00-06-44.z-2.compute-1.internal, localhost.z-2.compute-1.internal, , localhost
#relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +

#flurdy postfix guide settings

#myhostname = mail.yourdomain.com
myhostname = ec2-75-101-148-70.compute-1.amazonaws.com

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)

relayhost =

inet_interfaces = all
mynetworks_style = host

#masquerade_domains = mail.yourdomain.com
#masquerade_exceptions = root


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

#smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

readme_directory = no

# TLS parameters
#smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
#smtpd_use_tls=yes
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = ec2-75-101-148-70.compute-1.amazonaws.com
#alias_maps = hash:/etc/aliases
#alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = domU-12-31-35-00-06-44.z-2.compute-1.internal, localhost.z-2.compute-1.internal, , localhost
#relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +

#flurdy postfix guide settings

#myhostname = mail.yourdomain.com
myhostname = ec2-75-101-148-70.compute-1.amazonaws.com

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)

relayhost =

inet_interfaces = all
mynetworks_style = host

#masquerade_domains = mail.yourdomain.com
#masquerade_exceptions = root

local_recipient_maps =


local_recipient_maps =
mydestination =

# how long if undelivered before sending warning update to sender
delay_warning_time = 4h  
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

# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
# Requirements for the sender details
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
# Requirement for the recipient address
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service i$
smtpd_data_restrictions = reject_unauth_pipelining

# require proper helo at connections
smtpd_helo_required = yes
# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes

# not sure of the difference of the next two
# but they are needed for local aliasing
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
# this specifies where the virtual mailbox folders will be located
virtual_mailbox_base = /mnt/spool/mail/virtual
# this is for the mailbox location for each user
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
# and their user id     
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
# and group id
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
# and this is for aliases
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
# and this is for domain lookups
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
# this is how to connect to the domains (all virtual, but the option is there)
# not used yet
# transport_maps = mysql:/etc/postfix/mysql_transport.cf

#content_filter = amavis:[127.0.0.1]:10024

smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
#smtpd_sasl_path = smtpd
smtpd_sasl_security_options = noanonymous 
mtpd_sasl_local_domain =  
smtpd_sasl_authenticated_header = yes

#smtp_use_tls = no
smtp_tls_security_level = may
smtpd_use_tls=yes
#smtpd_tls_security_level = may
#smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom   
smtpd_tls_cert_file=/etc/postfix/smtpd.cert
smtpd_tls_key_file=/etc/postfix/smtpd.key
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

```

and /etc/courier/imapd
```
#VERSION: $Id: imapd.dist.in,v 1.39 2008/01/27 16:13:15 mrsam Exp $
#
# imapd created from imapd.dist by sysconftool
#
# Do not alter lines that begin with ##, they are used when upgrading
# this configuration.
#
#  Copyright 1998 - 2006 Double Precision, Inc.  See COPYING for
#  distribution information.
#
#  This configuration file sets various options for the Courier-IMAP server
#  when used with the couriertcpd server.
#  A lot of the stuff here is documented in the manual page for couriertcpd.
#
#  NOTE - do not use \ to split long variable contents on multiple lines.
#  This will break the default imapd.rc script, which parses this file.
#
##NAME: ADDRESS:0
#
#  Address to listen on, can be set to a single IP address.
#
ADDRESS=127.0.0.1

ADDRESS=0

##NAME: PORT:1
#
#  Port numbers that connections are accepted on.  The default is 143,
#  the standard IMAP port.
#
#  Multiple port numbers can be separated by commas.  When multiple port
#  numbers are used it is possible to select a specific IP address for a
#  given port as "ip.port".  For example, "127.0.0.1.900,192.68.0.1.900"
#  accepts connections on port 900 on IP addresses 127.0.0.1 and 192.68.0.1
#  The previous ADDRESS setting is a default for ports that do not have
#  a specified IP address.

PORT=143

##NAME: AUTHSERVICE:0
#
#  It's possible to authenticate using a different 'service' parameter
#  depending on the connection's port.  This only works with authentication
#  modules that use the 'service' parameter, such as PAM.  Example:
#
#  AUTHSERVICE143=imap
#  AUTHSERVICE993=imaps

##NAME: MAXDAEMONS:0
#
#  Maximum number of IMAP servers started
#
#  Maximum number of IMAP servers started
# 
 
MAXDAEMONS=40

##NAME: MAXPERIP:0
#  
#  Maximum number of connections to accept from the same IP address
 
MAXPERIP=20

##NAME: PIDFILE:0
#
#  File where couriertcpd will save its process ID
#  
 
PIDFILE=/var/run/courier/imapd.pid
 
##NAME: TCPDOPTS:0
#
# Miscellaneous couriertcpd options that shouldn't be changed.
#

TCPDOPTS="-nodnslookup -noidentlookup"

##NAME: LOGGEROPTS:0
#  
# courierlogger(1) options.
#

LOGGEROPTS="-name=imapd"

##NAME: DEFDOMAIN:0
#  
# Optional default domain. If the username does not contain the
# first character of DEFDOMAIN, then it is appended to the username.
# If DEFDOMAIN and DOMAINSEP are both set, then DEFDOMAIN is appended
# only if the username does not contain any character from DOMAINSEP.
# You can set different default domains based on the the interface IP
# address using the -access and -accesslocal options of couriertcpd(1).

#DEFDOMAIN="@example.com"

##NAME: IMAP_CAPABILITY:1
#  
# IMAP_CAPABILITY specifies what most of the response should be to the
# CAPABILITY command.
#
# If you have properly configured Courier to use CRAM-MD5, CRAM-SHA1, or
# CRAM-SHA256 authentication (see INSTALL), set IMAP_CAPABILITY as follows:
# If you have properly configured Courier to use CRAM-MD5, CRAM-SHA1, or
# CRAM-SHA256 authentication (see INSTALL), set IMAP_CAPABILITY as follows:
# 
# IMAP_CAPABILITY="IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA AUTH=CRAM-MD5 AUTH=CRAM-SHA1 AUTH=CRAM-SHA256 IDLE"
#

IMAP_CAPABILITY="IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE"
   
##NAME: KEYWORDS_CAPABILITY:0
#
# IMAP_KEYWORDS=1 enables custom IMAP keywords.  Set this option to 0 to
# disable custom keywords.

IMAP_KEYWORDS=1

##NAME: ACL_CAPABILITY:0
#
# IMAP_ACL=1 enables IMAP ACL extension. Set this option to 0 to
# disable ACL capabilities announce.

IMAP_ACL=1

##NAME: SMAP1_CAPABILITY:0
#
# EXPERIMENTAL
#
# To enable the experimental "Simple Mail Access Protocol" extensions,
# uncomment the following setting.
# 
# SMAP_CAPABILITY=SMAP1

##NAME: IMAP_CAPABILITY_ORIG:2
#
# For use by webadmin
   
IMAP_CAPABILITY_ORIG="IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA AUTH=CRAM-MD5 AUTH=CRAM-SHA1 AUTH=CRAM-SHA256 IDLE"

##NAME: IMAP_PROXY:0
# 
# Enable proxying.  See README.proxy

IMAP_PROXY=0

##NAME: PROXY_HOSTNAME:0
#
# Override value from gethostname() when checking if a proxy connection is
# required.
# 
# PROXY_HOSTNAME=

##NAME: IMAP_PROXY_FOREIGN:0
##NAME: IMAP_PROXY_FOREIGN:0
# 
# Proxying to non-Courier servers.  Re-sends the CAPABILITY command after
# logging in to the remote server.  May not work with all IMAP clients.

IMAP_PROXY_FOREIGN=0
   
##NAME: IMAP_IDLE_TIMEOUT:0
#
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

/etc/mailname content - ec2-75-101-148-70.compute-1.amazonaws.com

and my log:
/var/log/mail.info
```

Oct  8 19:10:30 (none) imapd-ssl: LOGIN, user=root@localhost, ip=[::ffff:127.0.0.1], port=[58570], protocol=IMAP
Oct  8 19:10:30 (none) imapd-ssl: LOGOUT, user=root@localhost, ip=[::ffff:127.0.0.1], headers=0, body=519, rcvd=145, sent=1170, time=0, starttls=1
Oct  8 19:10:53 (none) postfix/anvil[1931]: statistics: max connection rate 1/60s for (smtp:68.59.9.16) at Oct  8 19:07:32
Oct  8 19:10:53 (none) postfix/anvil[1931]: statistics: max connection count 1 for (smtp:68.59.9.16) at Oct  8 19:07:32
Oct  8 19:10:53 (none) postfix/anvil[1931]: statistics: max cache size 1 at Oct  8 19:07:32
Oct  8 19:16:17 (none) postfix/smtpd[1991]: connect from cpe-74-70-186-3.nycap.res.rr.com[74.70.186.3]
Oct  8 19:16:18 (none) postfix/smtpd[1991]: NOQUEUE: reject_warning: RCPT from cpe-74-70-186-3.nycap.res.rr.com[74.70.186.3]: 504 5.5.2 <ywhzi>: Helo command rejected: need fully-qualified hostname; from=<qlorena_rk@ey.com> to=<kas@threefound.com> proto=ESMTP helo=<ywhzi>
Oct  8 19:16:18 (none) postgrey: action=greylist, reason=new, client_name=cpe-74-70-186-3.nycap.res.rr.com, client_address=74.70.186.3, sender=qlorena_rk@ey.com, recipient=kas@threefound.com 
Oct  8 19:16:18 (none) postfix/smtpd[1991]: NOQUEUE: reject: RCPT from cpe-74-70-186-3.nycap.res.rr.com[74.70.186.3]: 450 4.2.0 <kas@threefound.com>: Recipient address rejected: Greylisted, see http://postgrey.schweikert.ch/help/threefound.com.html; from=<qlorena_rk@ey.com> to=<kas@threefound.com> proto=ESMTP helo=<ywhzi>
Oct  8 19:16:18 (none) postfix/smtpd[1991]: lost connection after DATA (0 bytes) from cpe-74-70-186-3.nycap.res.rr.com[74.70.186.3]
Oct  8 19:16:18 (none) postfix/smtpd[1991]: disconnect from cpe-74-70-186-3.nycap.res.rr.com[74.70.186.3]
Oct  8 19:17:32 (none) postfix/smtpd[1991]: connect from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]
Oct  8 19:17:32 (none) postfix/smtpd[1991]: setting up TLS connection from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]
Oct  8 19:17:33 (none) postfix/smtpd[1991]: SSL_accept error from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]: -1
Oct  8 19:17:33 (none) postfix/smtpd[1991]: lost connection after STARTTLS from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]
Oct  8 19:17:33 (none) postfix/smtpd[1991]: disconnect from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]
Oct  8 19:17:33 (none) postfix/smtpd[1997]: fatal: unexpected command-line argument: reject
Oct  8 19:17:34 (none) postfix/master[1736]: warning: process /usr/lib/postfix/smtpd pid 1997 exit status 1
Oct  8 19:17:34 (none) postfix/master[1736]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Oct  8 19:17:34 (none) postfix/smtpd[1998]: warning: xsasl_cyrus_server_get_mechanism_list: no applicable SASL mechanisms
Oct  8 19:17:34 (none) postfix/smtpd[1998]: fatal: no SASL authentication mechanisms
Oct  8 19:17:35 (none) postfix/master[1736]: warning: process /usr/lib/postfix/smtpd pid 1998 exit status 1
Oct  8 19:17:35 (none) postfix/master[1736]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Oct  8 19:19:06 (none) imapd: LOGOUT, ip=[::ffff:68.59.9.16], rcvd=76, sent=440
Oct  8 19:19:48 (none) imapd: LOGOUT, ip=[::ffff:68.59.9.16], rcvd=82, sent=440
Oct  8 19:20:53 (none) postfix/anvil[1992]: statistics: max connection rate 1/60s for (smtp:74.70.186.3) at Oct  8 19:16:17
Oct  8 19:20:53 (none) postfix/anvil[1992]: statistics: max connection count 1 for (smtp:74.70.186.3) at Oct  8 19:16:17
Oct  8 19:20:53 (none) postfix/anvil[1992]: statistics: max cache size 1 at Oct  8 19:16:17
Oct  8 19:27:32 (none) postfix/smtpd[2025]: connect from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]
Oct  8 19:27:33 (none) postfix/smtpd[2025]: setting up TLS connection from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]
Oct  8 19:27:33 (none) postfix/smtpd[2025]: SSL_accept error from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]: -1
Oct  8 19:27:33 (none) postfix/smtpd[2025]: lost connection after STARTTLS from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]
Oct  8 19:27:33 (none) postfix/smtpd[2025]: disconnect from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]
Oct  8 19:27:33 (none) postfix/smtpd[2027]: fatal: unexpected command-line argument: reject
Oct  8 19:27:34 (none) postfix/master[1736]: warning: process /usr/lib/postfix/smtpd pid 2027 exit status 1
Oct  8 19:27:34 (none) postfix/master[1736]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Oct  8 19:27:34 (none) postfix/smtpd[2028]: connect from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]
Oct  8 19:27:34 (none) postfix/smtpd[2028]: setting up TLS connection from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]
Oct  8 19:30:53 (none) postfix/anvil[2026]: statistics: max connection rate 1/60s for (smtp:68.59.9.16) at Oct  8 19:27:32
Oct  8 19:30:53 (none) postfix/anvil[2026]: statistics: max connection count 1 for (smtp:68.59.9.16) at Oct  8 19:27:32
Oct  8 19:30:53 (none) postfix/anvil[2026]: statistics: max cache size 1 at Oct  8 19:27:32
Oct  8 19:32:34 (none) postfix/smtpd[2028]: SSL_accept error from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]: -1
Oct  8 19:32:34 (none) postfix/smtpd[2028]: lost connection after CONNECT from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]
Oct  8 19:32:34 (none) postfix/smtpd[2028]: disconnect from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]
Oct  8 19:37:32 (none) postfix/smtpd[2030]: connect from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]
Oct  8 19:37:33 (none) postfix/smtpd[2030]: setting up TLS connection from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]
Oct  8 19:37:33 (none) postfix/smtpd[2030]: SSL_accept error from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]: -1
Oct  8 19:37:33 (none) postfix/smtpd[2030]: lost connection after STARTTLS from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]
Oct  8 19:37:33 (none) postfix/smtpd[2030]: disconnect from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]
Oct  8 19:37:33 (none) postfix/smtpd[2032]: fatal: unexpected command-line argument: reject
Oct  8 19:37:34 (none) postfix/master[1736]: warning: process /usr/lib/postfix/smtpd pid 2032 exit status 1
Oct  8 19:37:34 (none) postfix/master[1736]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Oct  8 19:37:34 (none) postfix/smtpd[2033]: connect from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]
Oct  8 19:37:34 (none) postfix/smtpd[2033]: setting up TLS connection from c-68-59-9-16.hsd1.sc.comcast.net[68.59.9.16]


```

The top two lines of my log are a successful login via squirrelmail, the rest are failures from other sources (atmail webmail, IMAP via script, and IMAP via Mail.app (both from external)

The respective ports on my firefox are open.

---

