---
title: "ProFTPd Virtual Server Issues"
date: 2011-05-01
forum: Server Platforms
---

### Post by thegodfaza on 2011-05-01
I'm trying to setup ProFTPd on my server with it's virtual servers and authenticating using ONLY MySQL. The configuration I'm using right now works perfectly as long as I ONLY use the default server on port 21. If I try to make and connect to a virtual server, on lets say port 22221, I get logs such as this in ...logs/proftpd/proftpd.log.
EDIT: Also connections to the default port are instant while connections to a virtual server port are delayed about 15 seconds on the "Connection established, waiting for welcome message..." message in my client.
```
May 01 18:26:56 singularity-vm proftpd[10117] 192.168.0.8 (::ffff:192.168.0.15[::ffff:192.168.0.15]): FTP session opened.
May 01 18:26:56 singularity-vm proftpd[10117] 192.168.0.8 (::ffff:192.168.0.15[::ffff:192.168.0.15]): USER testuser: no such user found from ::ffff:192.168.0.15 [::ffff:192.168$
May 01 18:26:56 singularity-vm proftpd[10117] 192.168.0.8 (::ffff:192.168.0.15[::ffff:192.168.0.15]): FTP session closed.
```

But when I connect using the same command in my client but change the port to the default port 21 (the default server) i get a perfect connection.
```
May 01 18:39:04 singularity-vm proftpd[10404] singularity-vm (::ffff:192.168.0.15[::ffff:192.168.0.15]): FTP session opened.
May 01 23:39:04 singularity-vm proftpd[10404] singularity-vm (::ffff:192.168.0.15[::ffff:192.168.0.15]): Preparing to chroot to directory '/data/ftp'
May 01 23:39:04 singularity-vm proftpd[10404] singularity-vm (::ffff:192.168.0.15[::ffff:192.168.0.15]): USER testuser: Login successful.
```

Here are my config files(with passwords, etc edited out):
proftpd.conf:
```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf
Include /etc/proftpd/sql.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				on
# If set on you can experience a longer connection delay in many cases.
IdentLookups			off

ServerName			"Debian"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayChdir .message true
ListOptions "-l"

DenyFilter			\*.*/

# Use this to jail all users in their homes 
# DefaultRoot			~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
RequireValidShell		off

# Port 21 is the standard FTP port.
Port				21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress		1.2.3.4

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
MaxInstances			30

# Set the user and group that the server normally runs at.
User				proftpd
Group				ftpusers

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask 022 022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd		off

# This is required to use both PAM-based authentication and local passwords
AuthOrder			mod_sql.c*
#AuthOrder			mod_auth_pam.c mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile			off

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
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
#Include /etc/proftpd/tls.conf

#
# Useful to keep VirtualHost/VirtualRoot directives separated
#
Include /etc/proftpd/virtuals.conf

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayChdir		.message
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
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>
<Global>
RootLogin off
AuthAliasOnly off
RequireValidShell on
DirFakeGroup on ~
DirFakeUser on ~
ListOptions "la"
</Global>
DefaultRoot ~

```

modules.conf
```
#
# This file is used to manage DSO modules and features.
#

# This is the directory where DSO modules reside

ModulePath /usr/lib/proftpd

# Allow only user root to load and unload modules, but allow everyone
# to see which modules have been loaded

ModuleControlsACLs insmod,rmmod allow user root
ModuleControlsACLs lsmod allow user *

LoadModule mod_ctrls_admin.c
LoadModule mod_tls.c

# Install one of proftpd-mod-mysql, proftpd-mod-pgsql or any other
# SQL backend engine to use this module and the required backend.
# This module must be mandatory loaded before anyone of
# the existent SQL backeds.
LoadModule mod_sql.c

# Install proftpd-mod-ldap to use this
#LoadModule mod_ldap.c

#
# 'SQLBackend mysql' or 'SQLBackend postgres' directives are required 
# to have SQL authorization working. You can also comment out the
# unused module here, in alternative.
#

# Install proftpd-mod-mysql and decomment the previous
# mod_sql.c module to use this.
LoadModule mod_sql_mysql.c

# Install proftpd-mod-pgsql and decommen the previous 
# mod_sql.c module to use this.
#LoadModule mod_sql_postgres.c

# Install proftpd-mod-sqlite and decomment the previous
# mod_sql.c module to use this
#LoadModule mod_sql_sqlite.c

# Install proftpd-mod-odbc and decomment the previous
# mod_sql.c moduleto use this
#LoadModule mod_sql_odbc.c

LoadModule mod_radius.c
LoadModule mod_quotatab.c
LoadModule mod_quotatab_file.c

# Install proftpd-mod-ldap to use this
#LoadModule mod_quotatab_ldap.c

# Install proftpd-mod-pgsql or proftpd-mod-mysql to use this
#LoadModule mod_quotatab_sql.c
LoadModule mod_quotatab_radius.c
LoadModule mod_wrap.c
LoadModule mod_rewrite.c
LoadModule mod_load.c
LoadModule mod_ban.c
LoadModule mod_wrap2.c
LoadModule mod_wrap2_file.c
# Install proftpd-mod-pgsql or proftpd-mod-mysql to use this
#LoadModule mod_wrap2_sql.c
LoadModule mod_dynmasq.c
LoadModule mod_vroot.c

# keep this module the last one
LoadModule mod_ifsession.c


```

sql.conf
```
#
# Proftpd sample configuration for SQL-based authentication.
#
# (This is not to be used if you prefer a PAM-based SQL authentication)
#

<IfModule mod_sql.c>
#
# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend 
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
SQLBackend	mysql
#
SQLEngine on
SQLAuthenticate on
#
# Use both a crypted or plaintext password 
#SQLAuthTypes Crypt Plaintext
#
# Use a backend-crypted or a crypted password
SQLAuthTypes Backend Crypt 
#
# Connection 
SQLConnectInfo <sql_user>@localhost <db> <passwd>
#
# Describes both users/groups tables
#
SQLUserInfo usertable userid passwd uid gid homedir shell
SQLGroupInfo grouptable groupname gid members
#
</IfModule>

```

virtuals.conf
```
#
# Proftpd sample configuration for Virtual Hosts and Virtual Roots.
#
# Note that FTP protocol requires IP based virtual host, not name based.
#

# 
# A generic sample virtual host.
#
#<VirtualHost ftp.server.com>
#ServerAdmin             ftpmaster@server.com
#ServerName              "Big FTP Archive"
#TransferLog             /var/log/proftpd/xfer/ftp.server.com
#MaxLoginAttempts        3
#RequireValidShell       no
#DefaultRoot             /srv/ftp_root
#AllowOverwrite          yes
#</VirtualHost>

#
# The vroot module is not required, but can be useful for shared
# directories.
#
<IfModule mod_vroot.c>
#VRootEngine on

#DefaultRoot ~
#VRootAlias upload /var/ftp/upload
#
#<VirtualHost a.b.c.d>
#VRootEngine on
#VRootServerRoot /etc/ftpd/a.b.c.d/
#VRootOptions allowSymlinks
#DefaultRoot ~
#</VirtualHost>
#
</IfModule>

<VirtualHost 192.168.0.8>
Port 22221
ServerName "Webroot"
<Directory /var/www>
GroupOwner www-data
UserOwner www-data
</Directory>
Group www-data
User www-data
DefaultChdir /var/www www
DefaultRoot /var/www www
DefaultRoot ~
</VirtualHost>

```

---

### Post by Lars Noodén on 2011-05-02
Are you sure you need FTP?  If you can get to the machine via SSH, then you already have SFTP installed and configured. That's the secure option and you can use [regular GUI clients](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients) with it.

---

