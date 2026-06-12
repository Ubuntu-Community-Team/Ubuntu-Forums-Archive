---
title: "Error 530 Proftpd + LDAP"
date: 2009-05-19
forum: Server Platforms
---

### Post by wrrzag on 2009-05-19
Hello everyone,
I've got a problem with Proftpd log-in against LDAP.
When I try to log-in to the ftp server using samba users I've got this prompt answer:
```

root@ubuntu-server:~# ftp localhost
Connected to localhost.
220 ProFTPD 1.3.1 Server (Ubuntu-Server) [::ffff:127.0.0.1]
Name (localhost:ruut): mohara
331 Password required for mohara
Password:
530 Login incorrect.
Login failed.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp>

```

My /etc/proftpd/proftpd.conf

```

#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				on

ServerName			"Ubuntu-Server"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayChdir               	.message true
ListOptions                	"-l"

DenyFilter			\*.*/

# Use this to jail all users in their homes 
# DefaultRoot			~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell		off

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

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				proftpd
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022

# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd		off

# This is required to use both PAM-based authentication and local passwords
#AuthOrder			*mod_auth_pam.c mod_auth_unix.c
AuthOrder			mod_ldap.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile			off

# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend 
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
#<IfModule mod_sql.c>
# SQLBackend			mysql
#</IfModule>

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
#   DisplayFirstChdir		.message
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


```

And then, my /etc/proftpd/ldap.conf:
```

#
# Proftpd sample configuration for LDAP authentication.
#
# (This is not to be used if you prefer a PAM-based SQL authentication)
#

<IfModule mod_ldap.c>
#
# This is used for ordinary LDAP connections, with or without TLS
#
LDAPServer ldap://localhost
LDAPDNInfo "cn=admin,dc=dominisintesi,dc=local" "123456"
LDAPDoAuth on "dc=Users,dc=dominisintesi,dc=local"
#
# To be set on only for LDAP/TLS on ordinary port, for LDAP+SSL see below
#LDAPUseTLS on
#

#
# This is used for encrypted LDAPS connections
#
#LDAPServer ldaps://ldap.example.com
#LDAPDNInfo "cn=admin,dc=example,dc=com" "admin_password"
#LDAPDoAuth on "dc=users,dc=example,dc=com"
#
</IfModule>


```

If anyone has any idea please, post it :p

Thanks!

---

