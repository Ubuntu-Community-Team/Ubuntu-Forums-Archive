---
title: "Postfix POP Authenication"
date: 2007-10-27
forum: Server Platforms
---

### Post by notaloafer on 2007-10-27
Right now I finally have a successful installation of postfix/courier/smtpd-auth.

Here is what I currently can do:
1) Send email using plain-text SMTP authentication 
2) Send emial using TLS SMTP authentication 
3) Download email (POP) using plain-text authentication 

What I want to do is be able to download email through a secure TLS connection just like I send email... how do I go about doing this?

Thanks!
-Eric

---

### Post by MJN on 2007-10-27
The downloading of mail is done via your POP server (Courier) so that's where you need to be looking (not Postfix).

I don't use Courier so can't help specifically, but hopefully this at least points you more in the right direction!

Mathew

---

### Post by tkharris on 2007-10-27
It's IMAP, but will likely help: [http://www.phparchitecture.com/howto_show.php?id=2](http://www.phparchitecture.com/howto_show.php?id=2)

---

### Post by notaloafer on 2007-10-27
> **MJN said:**
> The downloading of mail is done via your POP server (Courier) so that's where you need to be looking (not Postfix).

I don't use Courier so can't help specifically, but hopefully this at least points you more in the right direction!

Mathew

Thanks! I'll look in this direction... what exactly does Postfix do then if it doesn't store mail..? I'm still a bit confused I presume. Does Postfix still just handle SMTP out?

-Eric

---

### Post by MJN on 2007-10-27
It sends mail out, and accepts it back in - but only as far as dropping it into user's mailboxes. It's then down to another service (a POP or IMAP server usually) to handle users fetching the mail from these boxes.

Does that make sense?

Mathew

---

### Post by notaloafer on 2007-10-27
> **MJN said:**
> It sends mail out, and accepts it back in - but only as far as dropping it into user's mailboxes. It's then down to another service (a POP or IMAP server usually) to handle users fetching the mail from these boxes.

Does that make sense?

Mathew

ooh I see. So when you send a email to someone, postfix checks it and drops it into their designated mailbox. When you connect to your server to download emails, courier is responsible for handling the authentication and letting you download the emails out of the mailboxes.

I think I get it.

---

### Post by notaloafer on 2007-10-27
Okay I installed courier-pop-ssl and courier-imap-ssl

The problem now is I cannot connect to mail.notaloafer.com 995 ... I get a connection failed message. However if I telnet localhost 995 on my server's terminal, it connects just fine. It's defently not a firewall issue (I use firestarter and opened up port 995 for pop3s). What am I missing in my configuration?

Thanks
-Eric

Here is my imapd-ssl configuration file:

```

##VERSION: $Id: imapd-ssl.dist.in,v 1.12 2005/07/02 01:13:57 mrsam Exp $
#
# imapd-ssl created from imapd-ssl.dist by sysconftool
#
# Do not alter lines that begin with ##, they are used when upgrading
# this configuration.
#
#  Copyright 2000 - 2004 Double Precision, Inc.  See COPYING for
#  distribution information.
#
#  This configuration file sets various options for the Courier-IMAP server
#  when used to handle SSL IMAP connections.
#
#  SSL and non-SSL connections are handled by a dedicated instance of the
#  couriertcpd daemon.  If you are accepting both SSL and non-SSL IMAP
#  connections, you will start two instances of couriertcpd, one on the
#  IMAP port 143, and another one on the IMAP-SSL port 993.
#
#  Download OpenSSL from http://www.openssl.org/
#
##NAME: SSLPORT:1
#
#  Options in the imapd-ssl configuration file AUGMENT the options in the
#  imapd configuration file.  First the imapd configuration file is read,
#  then the imapd-ssl configuration file, so we do not have to redefine
#  anything.
#
#  However, some things do have to be redefined.  The port number is
#  specified by SSLPORT, instead of PORT.  The default port is port 993.
#
#  Multiple port numbers can be separated by commas.  When multiple port
#  numbers are used it is possibly to select a specific IP address for a
#  given port as "ip.port".  For example, "127.0.0.1.900,192.68.0.1.900"
#  accepts connections on port 900 on IP addresses 127.0.0.1 and 192.68.0.1
#  The SSLADDRESS setting is a default for ports that do not have
#  a specified IP address.

SSLPORT=993

##NAME: SSLADDRESS:0
#
#  Address to listen on, can be set to a single IP address.
#
# SSLADDRESS=127.0.0.1

SSLADDRESS=0

##NAME: SSLPIDFILE:0
#
# That's the SSL IMAP port we'll listen on.
# Feel free to redefine MAXDAEMONS, TCPDOPTS, and MAXPERIP.

SSLPIDFILE=/var/run/courier/imapd-ssl.pid

##NAME: SSLLOGGEROPTS:0
#
# courierlogger(1) options.                                        
#

SSLLOGGEROPTS="-name=imapd-ssl"

##NAME: IMAPDSSLSTART:0
#
# Different pid files, so that both instances of couriertcpd can coexist
# happily.
#
# You can also redefine IMAP_CAPABILITY, although I can't
# think of why you'd want to do that.
#
#
# Ok, the following settings are new to imapd-ssl:
#
#  Whether or not to start IMAP over SSL on simap port:

IMAPDSSLSTART=YES

##NAME: IMAPDSTARTTLS:0
#
#  Whether or not to implement IMAP STARTTLS extension instead:

IMAPDSTARTTLS=YES

##NAME: IMAP_TLS_REQUIRED:1
#
# Set IMAP_TLS_REQUIRED to 1 if you REQUIRE STARTTLS for everyone.
# (this option advertises the LOGINDISABLED IMAP capability, until STARTTLS
# is issued).

IMAP_TLS_REQUIRED=0


#########################################################################
#
# The following variables configure IMAP over SSL.  If OpenSSL is available
# during configuration, the couriertls helper gets compiled, and upon
# installation a dummy TLS_CERTFILE gets generated.  courieresmtpd will
# automatically advertise the ESMTP STARTTLS extension if both TLS_CERTFILE
# and COURIERTLS exist.
#
# WARNING: Peer certificate verification has NOT yet been tested.  Proceed
# at your own risk.  Only the basic SSL/TLS functionality is known to be
# working. Keep this in mind as you play with the following variables.
#
##NAME: COURIERTLS:0
#

COURIERTLS=/usr/bin/couriertls

##NAME: TLS_PROTOCOL:0
# 
# TLS_PROTOCOL sets the protocol version.  The possible versions are:
#
# SSL2 - SSLv2
# SSL3 - SSLv3
# TLS1 - TLS1

TLS_PROTOCOL=SSL3

##NAME: TLS_STARTTLS_PROTOCOL:0
# 
# TLS_STARTTLS_PROTOCOL is used instead of TLS_PROTOCOL for the IMAP STARTTLS
# extension, as opposed to IMAP over SSL on port 993.
#

TLS_STARTTLS_PROTOCOL=TLS1

##NAME: TLS_CIPHER_LIST:0
#
# TLS_CIPHER_LIST optionally sets the list of ciphers to be used by the
# OpenSSL library.  In most situations you can leave TLS_CIPHER_LIST
# undefined
#
# TLS_CIPHER_LIST="ALL:!ADH:RC4+RSA:+SSLv2:@STRENGTH"

##NAME: TLS_TIMEOUT:0
# TLS_TIMEOUT is currently not implemented, and reserved for future use.
# This is supposed to be an inactivity timeout, but its not yet implemented.
#

##NAME: TLS_DHCERTFILE:0
#
# TLS_DHCERTFILE - PEM file that stores our Diffie-Hellman cipher pair.
# When OpenSSL is compiled to use Diffie-Hellman ciphers instead of RSA
# you must generate a DH pair that will be used.  In most situations the
# DH pair is to be treated as confidential, and the file specified by
# TLS_DHCERTFILE must not be world-readable.
#
# TLS_DHCERTFILE=

##NAME: TLS_CERTFILE:0
#
# TLS_CERTFILE - certificate to use.  TLS_CERTFILE is required for SSL/TLS
# servers, and is optional for SSL/TLS clients.  TLS_CERTFILE is usually
# treated as confidential, and must not be world-readable.
#
TLS_CERTFILE=/etc/courier/imapd.pem

##NAME: TLS_TRUSTCERTS:0
#
# TLS_TRUSTCERTS=pathname - load trusted certificates from pathname.
# pathname can be a file or a directory. If a file, the file should
# contain a list of trusted certificates, in PEM format. If a
# directory, the directory should contain the trusted certificates,
# in PEM format, one per file and hashed using OpenSSL's c_rehash
# script. TLS_TRUSTCERTS is used by SSL/TLS clients (by specifying
# the -domain option) and by SSL/TLS servers (TLS_VERIFYPEER is set
# to PEER or REQUIREPEER).
#
#
# TLS_TRUSTCERTS=

##NAME: TLS_VERIFYPEER:0
#
# TLS_VERIFYPEER - how to verify client certificates.  The possible values of
# this setting are:
#
# NONE - do not verify anything
#
# PEER - verify the client certificate, if one's presented
#
# REQUIREPEER - require a client certificate, fail if one's not presented
#
#
TLS_VERIFYPEER=NONE

##NAME: TLS_CACHE:0
#
# A TLS/SSL session cache may slightly improve response for IMAP clients
# that open multiple SSL sessions to the server.  TLS_CACHEFILE will be
# automatically created, TLS_CACHESIZE bytes long, and used as a cache
# buffer.
#
# This is an experimental feature and should be disabled if it causes
# problems with SSL clients.  Disable SSL caching by commenting out the
# following settings:

TLS_CACHEFILE=/var/lib/courier/couriersslcache
TLS_CACHESIZE=524288

##NAME: MAILDIRPATH:0
#
# MAILDIRPATH - directory name of the maildir directory.
#
MAILDIRPATH=Maildir


```


Here is my pop3d-ssl file:

```

##VERSION: $Id: pop3d-ssl.dist.in,v 1.13 2005/07/02 01:13:57 mrsam Exp $
#
# pop3d-ssl created from pop3d-ssl.dist by sysconftool
#
# Do not alter lines that begin with ##, they are used when upgrading
# this configuration.
#
#  Copyright 2000-2004 Double Precision, Inc.  See COPYING for
#  distribution information.
#
#  This configuration file sets various options for the Courier-IMAP server
#  when used to handle SSL POP3 connections.
#
#  SSL and non-SSL connections are handled by a dedicated instance of the
#  couriertcpd daemon.  If you are accepting both SSL and non-SSL POP3
#  connections, you will start two instances of couriertcpd, one on the
#  POP3 port 110, and another one on the POP3-SSL port 995.
#
#  Download OpenSSL from http://www.openssl.org/
#
##NAME: SSLPORT:0
#
#  Options in the pop3d-ssl configuration file AUGMENT the options in the
#  pop3d configuration file.  First the pop3d configuration file is read,
#  then the pop3d-ssl configuration file, so we do not have to redefine
#  anything.
#
#  However, some things do have to be redefined.  The port number is
#  specified by SSLPORT, instead of PORT.  The default port is port 995.
#
#  Multiple port numbers can be separated by commas.  When multiple port
#  numbers are used it is possibly to select a specific IP address for a
#  given port as "ip.port".  For example, "127.0.0.1.900,192.68.0.1.900"
#  accepts connections on port 900 on IP addresses 127.0.0.1 and 192.68.0.1
#  The SSLADDRESS setting is a default for ports that do not have
#  a specified IP address.

SSLPORT=995

##NAME: SSLADDRESS:0
#
#  Address to listen on, can be set to a single IP address.
#
# SSLADDRESS=127.0.0.1

SSLADDRESS=127.0.0.1

##NAME: SSLPIDFILE:0
#
#
#

SSLPIDFILE=/var/run/courier/pop3d-ssl.pid

##NAME: SSLLOGGEROPTS:0
#
# courierlogger(1) options.                                              
#

SSLLOGGEROPTS="-name=pop3d-ssl"

##NAME: POP3DSSLSTART:0
#
#  Whether or not to start POP3 over SSL on spop3 port:

POP3DSSLSTART=YES

##NAME: POP3_STARTTLS:0
#
# Whether or not to implement the POP3 STLS extension:

POP3_STARTTLS=YES

##NAME: POP3_TLS_REQUIRED:1
#
# Set POP3_TLS_REQUIRED to 1 if you REQUIRE STARTTLS for everyone.
# (this option advertises the LOGINDISABLED POP3 capability, until STARTTLS
# is issued).

POP3_TLS_REQUIRED=0

##NAME: COURIERTLS:0
#
# The following variables configure POP3 over SSL.  If OpenSSL is available
# during configuration, the couriertls helper gets compiled, and upon
# installation a dummy TLS_CERTFILE gets generated.  courieresmtpd will
# automatically advertise the ESMTP STARTTLS extension if both TLS_CERTFILE
# and COURIERTLS exist.
#
# WARNING: Peer certificate verification has NOT yet been tested.  Proceed
# at your own risk.  Only the basic SSL/TLS functionality is known to be
# working. Keep this in mind as you play with the following variables.

COURIERTLS=/usr/bin/couriertls

##NAME: TLS_PROTOCOL:0
# 
# TLS_PROTOCOL sets the protocol version.  The possible versions are:
#
# SSL2 - SSLv2
# SSL3 - SSLv3
# TLS1 - TLS1

TLS_PROTOCOL=SSL3

##NAME: TLS_STARTTLS_PROTOCOL:0
# 
# TLS_STARTTLS_PROTOCOL is used instead of TLS_PROTOCOL for the POP3 STARTTLS
# extension, as opposed to POP3 over SSL on port 995.
#

TLS_STARTTLS_PROTOCOL=TLS1

##NAME: TLS_CIPHER_LIST:0
#
# TLS_CIPHER_LIST optionally sets the list of ciphers to be used by the
# OpenSSL library.  In most situations you can leave TLS_CIPHER_LIST
# undefined
#
# TLS_CIPHER_LIST="ALL:!ADH:RC4+RSA:+SSLv2:@STRENGTH"

##NAME: TLS_TIMEOUT:0
# TLS_TIMEOUT is currently not implemented, and reserved for future use.
# This is supposed to be an inactivity timeout, but its not yet implemented.
#

##NAME: TLS_DHCERTFILE:0
#
# TLS_DHCERTFILE - PEM file that stores our Diffie-Hellman cipher pair.
# When OpenSSL is compiled to use Diffie-Hellman ciphers instead of RSA
# you must generate a DH pair that will be used.  In most situations the
# DH pair is to be treated as confidential, and the file specified by
# TLS_DHCERTFILE must not be world-readable.
#
# TLS_DHCERTFILE=

##NAME: TLS_CERTFILE:0
#
# TLS_CERTFILE - certificate to use.  TLS_CERTFILE is required for SSL/TLS
# servers, and is optional for SSL/TLS clients.  TLS_CERTFILE is usually
# treated as confidential, and must not be world-readable.
#
TLS_CERTFILE=/etc/courier/pop3d.pem

##NAME: TLS_TRUSTCERTS:0
#
# TLS_TRUSTCERTS=pathname - load trusted certificates from pathname.
# pathname can be a file or a directory. If a file, the file should
# contain a list of trusted certificates, in PEM format. If a
# directory, the directory should contain the trusted certificates,
# in PEM format, one per file and hashed using OpenSSL's c_rehash
# script. TLS_TRUSTCERTS is used by SSL/TLS clients (by specifying
# the -domain option) and by SSL/TLS servers (TLS_VERIFYPEER is set
# to PEER or REQUIREPEER).
#
#
# TLS_TRUSTCERTS=

##NAME: TLS_VERIFYPEER:0
#
# TLS_VERIFYPEER - how to verify client certificates.  The possible values of
# this setting are:
#
# NONE - do not verify anything
#
# PEER - verify the client certificate, if one's presented
#
# REQUIREPEER - require a client certificate, fail if one's not presented
#
#
TLS_VERIFYPEER=NONE

##NAME: TLS_CACHE:0
#
# A TLS/SSL session cache may slightly improve response for long-running
# POP3 clients. TLS_CACHEFILE will be automatically created, TLS_CACHESIZE
# bytes long, and used as a cache buffer.
#
# This is an experimental feature and should be disabled if it causes
# problems with SSL clients.  Disable SSL caching by commenting out the
# following settings:

TLS_CACHEFILE=/var/lib/courier/couriersslcache
TLS_CACHESIZE=524288

##NAME: MAILDIRPATH:0
#
# MAILDIRPATH - directory name of the maildir directory.
#
MAILDIRPATH=Maildir


```




Thank you all for all your support!
now what's wrong with my configuration? :P
-Eric

---

### Post by notaloafer on 2007-10-27
bump..?

---

