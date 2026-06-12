---
title: "Imap and Authdaemon authentification"
date: 2010-07-22
forum: Server Platforms
---

### Post by najel on 2010-07-22
Hello
I have a ubuntu server installed with postfix, pop, imap, authdeamon ...
Pop work great, I can authenticate in the server , read mails ...
Currently I am looking to install roundcube which runs under IMAP ...
with imap i still have some trooubles when i try to be authetified ...
I enabled debugging mode of authdeamon
Logs results:
```
Jul 21 12:03:49 ks308711 imapd: Connection, ip=[::ffff:93.23.239.100]
Jul 21 12:03:49 ks308711 authdaemond: received auth request, service=imap, authtype=login
Jul 21 12:03:49 ks308711 authdaemond: authpam: trying this module
Jul 21 12:03:49 ks308711 authdaemond: authpam: sysusername=informaticien, sysuserid=<null>, sysgroupid=100, homedir=/home/informaticien, address=informaticien, fullname=, maildir=<null>, quota=<null>, options=<null>
Jul 21 12:03:49 ks308711 authdaemond: authpam: clearpasswd=<null>, passwd=x
Jul 21 12:03:49 ks308711 authdaemond: pam_service=imap, pam_username=informaticien
Jul 21 12:03:49 ks308711 authdaemond: dopam successful
Jul 21 12:03:49 ks308711 authdaemond: Authenticated: sysusername=informaticien, sysuserid=<null>, sysgroupid=100, homedir=/home/informaticien, address=informaticien, fullname=, maildir=<null>, quota=<null>, options=<null>
Jul 21 12:03:49 ks308711 authdaemond: Authenticated: clearpasswd=pass, passwd=$1$62692540$bJPzlM4HQB5f3WmYHJpjV/
```authdaemonrd conf:
```
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
authmodulelist="authpam"
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
DEBUG_LOGIN=2
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
```My imapd conf:
```
##VERSION: $Id: imapd.dist.in,v 1.41 2008/06/21 16:01:23 mrsam Exp $
#
# imapd created from imapd.dist by sysconftool
#
# Do not alter lines that begin with ##, they are used when upgrading
# this configuration.
#
#  Copyright 1998 - 2008 Double Precision, Inc.  See COPYING for
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
# ADDRESS=127.0.0.1
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
# DEFDOMAIN="@domaine.com"
##NAME: IMAP_CAPABILITY:1
#
# IMAP_CAPABILITY specifies what most of the response should be to the
# CAPABILITY command.
#
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
#
# IMAP_KEYWORDS=2 also enables custom IMAP keywords, but uses a slower
# algorithm. Use this setting if keyword-related problems occur when
# multiple IMAP clients are updating keywords on the same message.
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
# Set IMAP_OBSOLETE_CLIENT if your IMAP client expects [\\NoInferiors]("file://%5C%5CNoInferiors") to mean
# what [\\HasNoChildren]("file://%5C%5CHasNoChildren") really means.
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
```The port 143 responds to inquiries in telnet
When i try to be logued in using root it's work, but not with other users, and no visible errors in the logs ... 
for permissions i have try to chown every Maildir with his corresponding user, and put 777 chmod for all directories to be sure that the problem isn't comming from this...
If anyone has an idea about this problem.
Thank you

---

### Post by najel on 2010-07-26
Some news...

I activated roundcube logs:

> [26-Jul-2010 09:42:44 +0200]: S: * OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2008 Double Precision, Inc.  See COPYING for distribution information.
[26-Jul-2010 09:42:44 +0200]: C: a001 LOGIN "info" "password"
[26-Jul-2010 09:42:44 +0200]: S: * BYE [ALERT] Fatal error: **Account's mailbox directory is not owned by the correct uid or gid:****_For permissions i put a chown -R of the user in Maildir, With a chmod  777 to try... _**i still have the same problem

I someone have any idea?****

---

