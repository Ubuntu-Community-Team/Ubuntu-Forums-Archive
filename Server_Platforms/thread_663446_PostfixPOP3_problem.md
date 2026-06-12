---
title: "Postfix/POP3 problem"
date: 2008-01-10
forum: Server Platforms
---

### Post by Rhcd67 on 2008-01-10
I have installed postfix and can successfully receive mail.  However, I can't connect using Outlook/Thunderbird, and when I run telnet into the POP3 port and attempt to log in I get a login failed error, and I am sure the username and password are correct.  Also, when I telnet into the SMTP port and do an ehlo I get:

```

250-<server name>
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

```  

I know I am supposed to get 250-AUTH LOGIN PLAIN on this list or something similar, but I do not know how to fix this, and I do not know if this is related to the problem or not.  I followed the tutorial on setting up postfix at [the Server Guide here.]("http://doc.ubuntu.com/ubuntu/serverguide/C/postfix.html")

Any help would be greatly appreciated.  Thanks.

---

### Post by kvonb on 2008-01-10
-

---

### Post by k_grdn on 2008-01-10
Hi,

You need to set up an MDA to deliver messages after they've been accepted on a server.

Check out courier-imap, think there's a courier-pop3-*, you could just use imap but POP3 uses less disk space, bandwidth and resources on the server, your choice.

Good Luck,

Regards,

k_grdn

---

### Post by Rhcd67 on 2008-01-10
> **k_grdn said:**
> Hi,

You need to set up an MDA to deliver messages after they've been accepted on a server.

Check out courier-imap, think there's a courier-pop3-*, you could just use imap but POP3 uses less disk space, bandwidth and resources on the server, your choice.

Good Luck,

Regards,

k_grdn

I have both courier-pop and courier-imap installed, but still no luck-here's the config file for pop:

```

##VERSION: $Id: pop3d.dist.in,v 1.16 2005/07/05 12:42:51 mrsam Exp $
#
# pop3d created from pop3d.dist by sysconftool
#
# Do not alter lines that begin with ##, they are used when upgrading
# this configuration.
#
#  Copyright 1998 - 2004 Double Precision, Inc.  See COPYING for
#  distribution information.
#
#  Courier POP3 daemon configuration
#
##NAME: PIDFILE:0
#

PIDFILE=/var/run/courier/pop3d.pid

##NAME: MAXDAEMONS:0
#
#  Maximum number of POP3 servers started
#

MAXDAEMONS=40

##NAME: MAXPERIP:4
#
#  Maximum number of connections to accept from the same IP address

MAXPERIP=20

##NAME: POP3AUTH:1
#
# To advertise the SASL capability, per RFC 2449, uncomment the POP3AUTH
# variable:
#
# POP3AUTH="LOGIN"
#
# If you have configured the CRAM-MD5, CRAM-SHA1 or CRAM-SHA256, set POP3AUTH
# to something like this:
#
# POP3AUTH="LOGIN CRAM-MD5 CRAM-SHA1"

POP3AUTH=""

##NAME: POP3AUTH_ORIG:1
#
# For use by webadmin

POP3AUTH_ORIG="PLAIN LOGIN CRAM-MD5 CRAM-SHA1 CRAM-SHA256"

##NAME: POP3AUTH_TLS:1
#
# To also advertise SASL PLAIN if SSL is enabled, uncomment the
# POP3AUTH_TLS environment variable:
#
# POP3AUTH_TLS="LOGIN PLAIN"

POP3AUTH_TLS="LOGIN PLAIN"

##NAME: POP3AUTH_TLS_ORIG:0
#
# For use by webadmin

POP3AUTH_TLS_ORIG="LOGIN PLAIN"

##NAME: POP3_PROXY:0
#
# Enable proxying.  See README.proxy

POP3_PROXY=0

##NAME: PROXY_HOSTNAME:0
#
# Override value from gethostname() when checking if a proxy connection is
# required.

# PROXY_HOSTNAME=

##NAME: PORT:1
#
# Port to listen on for connections.  The default is port 110.
#
#  Multiple port numbers can be separated by commas.  When multiple port
#  numbers are used it is possibly to select a specific IP address for a
#  given port as "ip.port".  For example, "127.0.0.1.900,192.68.0.1.900"
#  accepts connections on port 900 on IP addresses 127.0.0.1 and 192.68.0.1
#  The ADDRESS setting is a default for ports that do not have a specified
#  IP address.

PORT=110

##NAME: ADDRESS:0
#
# IP address to listen on.  0 means all IP addresses.

ADDRESS=0

##NAME: TCPDOPTS:0
#
# Other couriertcpd(1) options.  The following defaults should be fine.
#

TCPDOPTS="-nodnslookup -noidentlookup"

##NAME: LOGGEROPTS:0
#
# courierlogger(1) options.
#

LOGGEROPTS="-name=pop3d"

##NAME: DEFDOMAIN:0

##NAME: DEFDOMAIN:0
#
# Optional default domain. If the username does not contain the
# first character of DEFDOMAIN, then it is appended to the username.
# If DEFDOMAIN and DOMAINSEP are both set, then DEFDOMAIN is appended
# only if the username does not contain any character from DOMAINSEP.
# You can set different default domains based on the the interface IP
# address using the -access and -accesslocal options of couriertcpd(1).

#DEFDOMAIN="@example.com"

##NAME: POP3DSTART:0
#
# POP3DSTART is not referenced anywhere in the standard Courier programs
# or scripts.  Rather, this is a convenient flag to be read by your system
# startup script in /etc/rc.d, like this:
#
#  . /etc/courier/pop3d
#  case x$POP3DSTART in
#  x[yY]*)
#        /usr/lib/courier/pop3d.rc start
#        ;;
#  esac

#
# Optional default domain. If the username does not contain the
# first character of DEFDOMAIN, then it is appended to the username.
# If DEFDOMAIN and DOMAINSEP are both set, then DEFDOMAIN is appended
# only if the username does not contain any character from DOMAINSEP.
# You can set different default domains based on the the interface IP
# address using the -access and -accesslocal options of couriertcpd(1).

#DEFDOMAIN="@example.com"

##NAME: POP3DSTART:0
#
# POP3DSTART is not referenced anywhere in the standard Courier programs
# or scripts.  Rather, this is a convenient flag to be read by your system
# startup script in /etc/rc.d, like this:
#
#  . /etc/courier/pop3d
#  case x$POP3DSTART in
#  x[yY]*)
#        /usr/lib/courier/pop3d.rc start
#        ;;
#  esac
#
# The default setting is going to be NO, until Courier is shipped by default
# with enough platforms so that people get annoyed with having to flip it to
# YES every time.

POP3DSTART=YES

##NAME: MAILDIRPATH:0
#
# MAILDIRPATH - directory name of the maildir directory.
#
MAILDIRPATH=Maildir


```

Can you see anything wrong?  Thanks.

---

