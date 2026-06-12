---
title: "new IMAP / Postfix installation help"
date: 2007-11-09
forum: Server Platforms
---

### Post by charmcity on 2007-11-09
Hi,  Brand new Ubuntu convert here from the land of SuSE.  All I have to say is WOW.

Problem is I have installed the Desktop version (7.10) and now am working on my IMAP / POSTFIX installation.   I suspect my problem is with the LMTP socket connection but here are my symptoms......anyone out there who can solve this problem I'll buy you a coke! Cause I'm stumped!!!!

Symptoms:
   - Mail arrives correctly to my server (DNS is correct)
   - Postfix sees the mail and initiates a hand-off to Cyrus via LMTP local connection
   - Breakdown occurs when Postfix is told it cannot access the LMTP socket (See actual error log below)
   - when installing I noted that going to /var/run (LMTP calls its socket /var/run/lmtp) there was no "lmtp" there.  maybe this is the problem?  If so how do I create the "socket" is it just a folder? a file?  I have tried creating an lmtp folder and chown to cyrus with group access shared by both postfix and cyrus but no luck.

I have included my main.cf, master.cf, imapd.conf and cyrus.conf below.  I appreciate your help!!

**relevant Mail.Log information**
```
Nov  9 16:10:32 tommy postfix/cleanup[7654]: 6BE882C0B63: message-id=<e7ea465e0711091310p36af0066m907d16b589403592@mail.gmail.com>
Nov  9 16:10:32 tommy postfix/cleanup[7653]: 6C06B2C0B64: message-id=<e7ea465e0711091310p36af0066m907d16b589403592@mail.gmail.com>
Nov  9 16:10:32 tommy postfix/qmgr[7505]: 6BE882C0B63: from=<tom.paulick@gmail.com>, size=1771, nrcpt=1 (queue active)
Nov  9 16:10:32 tommy postfix/qmgr[7505]: 6C06B2C0B64: from=<tom.paulick@gmail.com>, size=1767, nrcpt=1 (queue active)
Nov  9 16:10:32 tommy postfix/local[7655]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Nov  9 16:10:32 tommy postfix/local[7656]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Nov  9 16:10:33 tommy postfix/lmtp[7657]: 6BE882C0B63: to=<tommy@bostonst.com>, relay=none, delay=1, delays=0.88/0.04/0.1/0, dsn=4.4.1, status=deferred (connect to tommy.bostonst.com[/var/run/lmtp]: Connection refused)
Nov  9 16:10:33 tommy postfix/lmtp[7658]: 6C06B2C0B64: to=<gma@bostonst.com>, relay=none, delay=1, delays=0.88/0.04/0.1/0, dsn=4.4.1, status=deferred (connect to tommy.bostonst.com[/var/run/lmtp]: Connection refused)

```

**main.cf**
```
queue_directory = /var/spool/postfix
command_directory = /usr/sbin
daemon_directory = /usr/lib/postfix
mail_owner = postfix
myhostname = tommy.bostonst.com
mydomain = bostonst.com
myorigin = $mydomain
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
unknown_local_recipient_reject_code = 550

mynetworks_style = host

mailbox_transport = lmtp:unix:/var/run/lmtp
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
debugger_command =
	 PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin
	 xxgdb $daemon_directory/$process_name $process_id & sleep 5
sendmail_path = /usr/sbin/sendmail
newaliases_path = /usr/bin/newaliases
mailq_path = /usr/bin/mailq
setgid_group = postdrop
smtp_sasl_auth_enable = no
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $mydomain
smtpd_recipient_restrictions =
	permit_mynetworks,
	permit_sasl_authenticated,
	reject_unauth_destination

message_size_limit = 20000000
```

**master.cf**
```
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_enforce_tls=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
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
lmtp      unix  -       -       n       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache	  unix	-	-	-	-	1	scache
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
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
cyrus     unix  -   n   n   -   -   pipe
  flags=R user=cyrus argv=/usr/sbin/cyrdeliver -e -m "${extension}" ${user}
```

**cyrus.conf**
```
# Debian defaults for Cyrus IMAP server/cluster implementation
# see cyrus.conf(5) for more information
#
# All the tcp services are tcpd-wrapped. see hosts_access(5)
# $Id: cyrus.conf 567 2006-08-14 18:19:32Z sven $

START {
	# do not delete this entry!
	recover		cmd="/usr/sbin/ctl_cyrusdb -r"
  
	# this is only necessary if idlemethod is set to "idled" in imapd.conf
	#idled		cmd="idled"

	# this is useful on backend nodes of a Murder cluster
	# it causes the backend to syncronize its mailbox list with
	# the mupdate master upon startup
	#mupdatepush   cmd="/usr/sbin/ctl_mboxlist -m"

	# this is recommended if using duplicate delivery suppression
	delprune	cmd="/usr/sbin/cyr_expire -E 3"
	# this is recommended if caching TLS sessions
	tlsprune	cmd="/usr/sbin/tls_prune"
}

# UNIX sockets start with a slash and are absolute paths
# you can use a maxchild=# to limit the maximum number of forks of a service
# you can use babysit=true and maxforkrate=# to keep tight tabs on the service
# most services also accept -U (limit number of reuses) and -T (timeout)
SERVICES {
	# --- Normal cyrus spool, or Murder backends ---
	# add or remove based on preferences
	imap		cmd="imapd -U 30" listen="imap" prefork=0 maxchild=100
	#imaps		cmd="imapd -s -U 30" listen="imaps" prefork=0 maxchild=100
	pop3		cmd="pop3d -U 30" listen="pop3" prefork=0 maxchild=50
	#pop3s		cmd="pop3d -s -U 30" listen="pop3s" prefork=0 maxchild=50
	nntp		cmd="nntpd -U 30" listen="nntp" prefork=0 maxchild=100
	#nntps		cmd="nntpd -s -U 30" listen="nntps" prefork=0 maxchild=100

	# At least one form of LMTP is required for delivery
	# (you must keep the Unix socket name in sync with imap.conf)
	#lmtp		cmd="lmtpd" listen="localhost:lmtp" prefork=0 maxchild=20
	lmtpunix	cmd="lmtpd" listen="/var/run/lmtp" prefork=0 maxchild=20
	# ----------------------------------------------

	# useful if you need to give users remote access to sieve
	# by default, we limit this to localhost in Debian
  	sieve		cmd="timsieved" listen="localhost:sieve" prefork=0 maxchild=100

	# this one is needed for the notification services
	notify		cmd="notifyd" listen="/var/run/cyrus/socket/notify" proto="udp" prefork=1

	# --- Murder frontends -------------------------
	# enable these and disable the matching services above, 
	# except for sieve (which deals automatically with Murder)

	# mupdate database service - must prefork at least 1
	# (mupdate slaves)
	#mupdate       cmd="mupdate" listen=3905 prefork=1
	# (mupdate master, only one in the entire cluster)
	#mupdate       cmd="mupdate -m" listen=3905 prefork=1

	# proxies that will connect to the backends
	#imap		cmd="proxyd" listen="imap" prefork=0 maxchild=100
	#imaps		cmd="proxyd -s" listen="imaps" prefork=0 maxchild=100
	#pop3		cmd="pop3proxyd" listen="pop3" prefork=0 maxchild=50
	#pop3s		cmd="pop3proxyd -s" listen="pop3s" prefork=0 maxchild=50
	#lmtp		cmd="lmtpproxyd" listen="lmtp" prefork=1 maxchild=20
	# ----------------------------------------------
}

EVENTS {
	# this is required
	checkpoint	cmd="/usr/sbin/ctl_cyrusdb -c" period=30

	# this is only necessary if using duplicate delivery suppression
	delprune	cmd="/usr/sbin/cyr_expire -E 3" at=0401

	# this is only necessary if caching TLS sessions
	tlsprune	cmd="/usr/sbin/tls_prune" at=0401
	
	# indexing of mailboxs for server side fulltext searches

	# reindex changed mailboxes (fulltext) approximately every other hour
	#squatter_1	cmd="/usr/bin/nice -n 19 /usr/sbin/squatter -s" period=120

	# reindex all mailboxes (fulltext) daily
	#squatter_a	cmd="/usr/sbin/squatter" at=0517
}

```

**imapd.conf**

```
# Unix domain socket that lmtpd listens on.
lmtpsocket: /var/run/lmtp

# The idle backend to use for IDLE command.
# Options: poll (default), idled, no
# poll doesn't need the idled daemon and is supposed to be more robust.
# however it doesn't update as quickly as the idled backend does. "no"
# turns off IDLE support. If set to "idled", you will also need to enable
# the "idled" entry in cyrus.conf.
idlemethod: poll

# Unix domain socket that idled listens on.
idlesocket: /var/run/cyrus/socket/idle

# Unix domain socket that the new mail notification daemon listens on.
notifysocket: /var/run/cyrus/socket/notify

# Syslog prefix. Defaults to cyrus (so logging is done as cyrus/imap etc.)
syslog_prefix: cyrus

##
## DEBUGGING
##
# Debugging hook. See /usr/share/doc/cyrus-common-2.2/README.Debian.debug
# Keep the hook disabled when it is not in use
#
# gdb Back-traces
#debug_command: /usr/bin/gdb -batch -cd=/tmp -x /usr/lib/cyrus/get-backtrace.gdb /usr/lib/cyrus/bin/%s %d >/tmp/gdb-backtrace.cyrus.%1$s.%2$d <&- 2>&1 &
#
# system-call traces
#debug_command: /usr/bin/strace -tt -o /tmp/strace.cyrus.%s.%d -p %2$d <&- 2>&1 &
#
# library traces
#debug_command: /usr/bin/ltrace -tt -n 2 -o /tmp/ltrace.cyrus.%s.%d -p %2$d <&- 2>&1 &
```

---

### Post by DDuong on 2007-12-01
Hello,

You mentioned that going to /var/run you didn't see a lmtp folder.  Yes, that can be an issue.

When you first installed Cyrus and checked the cyrus.conf, did it show where the lmtp socket was located?  I believe the default location is "/var/imap/socket/lmtp".  

Speaking of /var/imap/socket/lmtp, check that location and see if you have that folder instead of /var/run/lmtp?

---

