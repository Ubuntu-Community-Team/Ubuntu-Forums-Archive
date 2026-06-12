---
title: "proftpd + TLS issues"
date: 2013-08-22
forum: Server Platforms
---

### Post by [pl]ice on 2013-08-22
Hi,
I'm having problems when trying to connect. When I tried to connect from localnetwork it's ok, but from anywhere else on the internet, the connection fails, e.g. using filezilla
:
Command:	PWD
Response:	257 "/home" is the current directory
Command:	PORT 34,254,247,1,10,235
Response:	200 PORT command successful
Command:	MLSD
Response:	425 Unable to build data connection: Connection Refused
Error:	Failed to retrieve directory listing

I've tried passive as well with similar results. It will log me in but it will fail the direcotry listing.

Connection attempt failed with "ECONNREFUSED - Connection refused by server".
Error:	Could not connect to server


Response:	227 Entering Passive Mode (82,160,229,97,240,110).
Command:	MLSD
Error:	The data connection could not be established: ECONNREFUSED - Connection refused by server
I have tried using:





 only TLSv1
TLSVerifyClient                         off

implicit /explicit  connections


Can you pls give me a hand?

 uname -a
Linux serwer 3.5.0-39-generic #60~precise1-Ubuntu SMP Wed Aug 14 15:28:09 UTC 2013 i686 i686 i386 GNU/Linux
```
cat /etc/proftpd/proftpd.conf
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes, reload proftpd after modifications, if
# it runs in daemon mode. It is not required in inetd/xinetd mode.
#

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6                         on
# If set on you can experience a longer connection delay in many cases.
IdentLookups                    off

ServerName                      "Prv"
ServerType                      standalone
DeferWelcome                    off

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    off

TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200

DisplayLogin                    welcome.msg
DisplayChdir                    .message true
ListOptions                     "-l"

DenyFilter                      \*.*/

# Use this to jail all users in their homes
# DefaultRoot                   ~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
#RequireValidShell off

# Port 21 is the standard FTP port.
Port                            21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
 PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress             1.2.3.4

# This is useful for masquerading address with dynamic IPs:
# refresh any configured MasqueradeAddress directives every 8 hours
<IfModule mod_dynmasq.c>
# DynMasqRefresh 28800
</IfModule>

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

# Set the user and group that the server normally runs at.
User                            proftpd
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd              off

# This is required to use both PAM-based authentication and local passwords
# AuthOrder                     mod_auth_pam.c* mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile                   off

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

# Logging onto /var/log/lastlog is enabled but set to off by default
UseLastlog on

# In order to keep log file dates consistent after chroot, use timezone info
# from /etc/localtime.  If this is not set, and proftpd is configured to
# chroot (e.g. DefaultRoot or <Anonymous>), it will use the non-daylight
# savings timezone regardless of whether DST is in effect.
#SetEnv TZ :/etc/localtime

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://www.securityfocus.com/bid/11430/discuss
# It is on by default.
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        off
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine off
</IfModule>

#
# Alternative authentication frameworks
#
#Include /etc/proftpd/ldap.conf
#Include /etc/proftpd/sql.conf

#
# This is used for FTPS connections
#

Include /etc/proftpd/tls.conf

#
# Useful to keep VirtualHost/VirtualRoot directives separated
#
#Include /etc/proftpd/virtuals.con

# A basic anonymous configuration, no upload directories.




# <Anonymous ~ftp>
#   User                                ftp
#   Group                               nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias                   anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser on ftp
#   DirFakeGroup on ftp
#
#   RequireValidShell           off
#
#   # Limit the maximum number of anonymous logins
#   MaxClients                  10
#
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin                        welcome.msg
#   DisplayChdir                .message
#
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
#
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask                           022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
#
# </Anonymous>

# Include other custom configuration files
Include /etc/proftpd/conf.d/

```


```
 cat tls.conf
#
# Proftpd sample configuration for FTPS connections.
#
# Note that FTPS impose some limitations in NAT traversing.
# See http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html
# for more information.
#

<IfModule mod_tls.c>
TLSEngine                               on
TLSLog                                  /var/log/proftpd/tls.log
TLSProtocol                             SSLv23
#
# Server SSL certificate. You can generate a self-signed certificate using
# a command like:
#
# openssl req -x509 -newkey rsa:1024 \
#          -keyout /etc/ssl/private/proftpd.key -out /etc/ssl/certs/proftpd.crt \
#          -nodes -days 365
#
# The proftpd.key file must be readable by root only. The other file can be
# readable by anyone.
#
# chmod 0600 /etc/ssl/private/proftpd.key
# chmod 0640 /etc/ssl/private/proftpd.key
#
TLSRSACertificateFile                   /etc/proftpd/ssl/proftpd.cert.pem
TLSRSACertificateKeyFile               /etc/proftpd//ssl/proftpd.key.pem
#
# CA the server trusts...
#TLSCACertificateFile                    /etc/ssl/certs/CA.pem
# ...or avoid CA cert and be verbose
# ... or the same with relaxed session use for some clients (e.g. FireFtp)
TLSOptions                      NoCertRequest EnableDiags NoSessionReuseRequired
TLSOptions      AllowClientRenegotiations
#
#
# Per default drop connection if client tries to start a renegotiate
# This is a fix for CVE-2009-3555 but could break some clients.
#
#
# Authenticate clients that want to use FTP over TLS?
#
TLSVerifyClient                         off
#
# Are clients required to use FTP over TLS when talking to this server?
#
TLSRequired                             on
#
# Allow SSL/TLS renegotiations when the client requests them, but
# do not force the renegotations.  Some clients do not support
# SSL/TLS renegotiations; when mod_tls forces a renegotiation, these
# clients will close the data connection, or there will be a timeout
# on an idle data connection.
#
#TLSRenegotiate                          ctrl 1500 timeout 300
#TLSSessionCache                        internal: 1800
</IfModule>

```

Restarting proftpd shows:
 serwer proftpd[5976]: mod_tls/2.4.3: compiled using OpenSSL version 'OpenSSL 1.0.0e 6 Sep 2011' headers, but linked to OpenSSL version 'OpenSSL 1.0.1 14 Mar 2012' library
serwer proftpd[5976]: mod_sftp/0.9.8: compiled using OpenSSL version 'OpenSSL 1.0.0e 6 Sep 2011' headers, but linked to OpenSSL version 'OpenSSL 1.0.1 14 Mar 2012' library
serwer proftpd[5976]: mod_tls_memcache/0.1: notice: unable to register 'memcache' SSL session cache: Memcache support not enabled



ProFTPD Version 1.3.4a

---

