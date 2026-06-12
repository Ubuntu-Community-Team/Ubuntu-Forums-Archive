---
title: "Proftpd MySQL Issues"
date: 2015-08-26
forum: Server Platforms
---

### Post by patrickfrog on 2015-08-26
Hello everyone,

I have been struggling for a while now to get Proftpd working with a MySQL database for authentication.  I have followed many tutorials and read the documentation on the MySQL module and the Proftpd configuration files.  It appears that the module is loaded (as far as I can tell) and not throwing any errors, however I cannot get any indication in the mod_sql logs or the MySQL query logs that Proftpd is even attempting to interact with my database.  Here are my configuration files as reference, if this is caused by a simple mistake, please let me know:

proftpd.conf
```

#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes, reload proftpd after modifications, if
# it runs in daemon mode. It is not required in inetd/xinetd mode.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6                off
# If set on you can experience a longer connection delay in many cases.
IdentLookups            off

ServerName            "Storecaster Radio"
ServerType            standalone
DeferWelcome            off

MultilineRFC2228        on
DefaultServer            on
ShowSymlinks            on

TimeoutNoTransfer        600
TimeoutStalled            600
TimeoutIdle            1200

DisplayLogin                    welcome.msg
DisplayChdir                   .message true
ListOptions                    "-l"

DenyFilter            \*.*/

# Use this to jail all users in their homes 
DefaultRoot            ~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
RequireValidShell        off

# Port 21 is the standard FTP port.
Port                21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress        1.2.3.4

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
MaxInstances            30

# Set the user and group that the server normally runs at.
User                proftpd
Group                nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                022  022
# Normally, we want files to be overwriteable.
AllowOverwrite            on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd        off

# This is required to use both PAM-based authentication and local passwords
AuthOrder            mod_sql.c mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile            off

TransferLog /var/log/proftpd/xferlog
SystemLog /var/log/proftpd/proftpd.log

# Logging onto /var/log/lastlog is enabled but set to off by default
#UseLastlog on

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
Include /etc/proftpd/sql.conf

#
# This is used for FTPS connections
#
#Include /etc/proftpd/tls.conf

#
# Useful to keep VirtualHost/VirtualRoot directives separated
#
#Include /etc/proftpd/virtuals.conf

# Include other custom configuration files
Include /etc/proftpd/conf.d/
<Global>
</Global>

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
# 'SQLBackend mysql' or 'SQLBackend postgres' (or any other valid backend) directives 
# are required to have SQL authorization working. You can also comment out the
# unused module here, in alternative.
#

SQLBackend mysql

# Install proftpd-mod-mysql and decomment the previous
# mod_sql.c module to use this.
LoadModule mod_sql_mysql.c

# Install proftpd-mod-pgsql and decomment the previous 
# mod_sql.c module to use this.
#LoadModule mod_sql_postgres.c

# Install proftpd-mod-sqlite and decomment the previous
# mod_sql.c module to use this
#LoadModule mod_sql_sqlite.c

# Install proftpd-mod-odbc and decomment the previous
# mod_sql.c module to use this
#LoadModule mod_sql_odbc.c

# Install one of the previous SQL backends and decomment 
# the previous mod_sql.c module to use this
LoadModule mod_sql_passwd.c

LoadModule mod_radius.c
LoadModule mod_quotatab.c
LoadModule mod_quotatab_file.c

# Install proftpd-mod-ldap to use this
#LoadModule mod_quotatab_ldap.c

# Install one of the previous SQL backends and decomment 
# the previous mod_sql.c module to use this
#LoadModule mod_quotatab_sql.c
LoadModule mod_quotatab_radius.c
LoadModule mod_wrap.c
LoadModule mod_rewrite.c
LoadModule mod_load.c
LoadModule mod_ban.c
LoadModule mod_wrap2.c
LoadModule mod_wrap2_file.c
# Install one of the previous SQL backends and decomment 
# the previous mod_sql.c module to use this
#LoadModule mod_wrap2_sql.c
LoadModule mod_dynmasq.c
LoadModule mod_exec.c
LoadModule mod_shaper.c
LoadModule mod_ratio.c
LoadModule mod_site_misc.c

LoadModule mod_sftp.c
LoadModule mod_sftp_pam.c
# Install one of the previous SQL backends and decomment 
# the previous mod_sql.c module to use this
#LoadModule mod_sftp_sql.c

LoadModule mod_facl.c
LoadModule mod_unique_id.c
LoadModule mod_copy.c
LoadModule mod_deflate.c
LoadModule mod_ifversion.c
LoadModule mod_tls_memcache.c

# Install proftpd-mod-geoip to use the GeoIP feature
#LoadModule mod_geoip.c

# keep this module the last one
LoadModule mod_ifsession.c

<VirtualHost 184.75.202.75>
DefaultChdir /var/www
DefaultRoot /var/www
<Directory /var/www/html/>
GroupOwner www-data
AllowOverwrite on
</Directory>
Group www-data
</VirtualHost>

```
sql.conf
```

#
# Proftpd sample configuration for SQL-based authentication.
#
# (This is not to be used if you prefer a PAM-based SQL authentication)
#

<IfModule mod_sql.c>
#Create a log
SQLLogFile /var/log/proftpd/mod_sql.log

#
# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend 
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
SQLBackend    mysql
#
SQLEngine on
SQLAuthenticate on
#
# Use both a crypted or plaintext password 
#SQLAuthTypes Crypt Plaintext
#
SQLPasswordEngine on
SQLAuthTypes SHA512
SQLPasswordEncoding hex

#
# Connection 
SQLConnectInfo ftp@localhost proftpd ***********
#
# Describes both users/groups tables
#
SQLUserInfo users userid passwd uid gid homedir shell
SQLGroupInfo groups groupname gid members
#SQLUserInfo    ftpuser userid passwd uid gid homedir shell
#SQLGroupInfo    ftpgroup groupname gid members
#
# Update the users.last_accessed column on successful login in the userdb
SQLNamedQuery last_accessed UPDATE "last_accessed = NOW() WHERE userid='%u'" users
SQLLog PASS last_accessed
#
RootLogin off
RequireValidShell off
</IfModule>

```

Thank you in advance for any help and advice.

Patrick

---

### Post by lisati on 2015-08-27
*Thread moved to **Server Platforms**.*

---

### Post by dgoosens on 2015-08-27
hi

not an expert but had to struggle with a Proftpd setup a while ago...

Seems to me, modules.conf is not the proper location to setup your Virtualhost
Also, just checked, but in my sql.conf file I have a line with
```
 CreateHome on 
```
([http://www.proftpd.org/docs/howto/CreateHome.html](http://www.proftpd.org/docs/howto/CreateHome.html))

---

### Post by patrickfrog on 2015-08-27
I actually didn't put the virtual host in the modules.conf file. I use Webmin to manager the basic parts of my server's services and it looks like it chooses to put the hosts there.  However, I am having no trouble accessing the FTP server on the virtual host and am even able to login using my UNIX account.  The problem occurs when I try to use one of my users from the MySQL database.  On the client end I get the message "Login incorrect" and in the proftpd log I get "USER bob: no such user found". The former would lead me to belive that the passord is simply incorrect of the encyption type is wrong and the latter would seem to indicate that the user cannot be found at all.  When I inspect proftpd's mod_sql log I see no attempts at even using MySQL and when I look through MySQL's logs, I see that no queries were made.

---

### Post by patrickfrog on 2015-08-27
I also made the change you suggested and added CreateHome on to the config, but that appears to have not made a difference.

---

### Post by patrickfrog on 2015-09-05
Does anyone have any other ideas as to what could be the issue?

Thanks,
Patrick

---

