---
title: "Adding users to Proftpd wont work."
date: 2009-05-14
forum: Server Platforms
---

### Post by Macmee on 2009-05-14
I followed this guide here: [http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp+server+howto](http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp+server+howto) to setup an FTP server on Ubuntu Hardy 8.04. My FTP client finds the server, but cannot login, saying password incorrect. Even if I type a totally bogus username it says password incorrect. Here's my proftpd.conf file:
```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				on
# If set on you can experience a longer connection delay in many cases.
IdentLookups			off

ServerName			"Macmee's Server"
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
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd		off

# This is required to use both PAM-based authentication and local passwords
# AuthOrder			*mod_auth_pam.c mod_auth_unix.c

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



# here are my improvements

# chroot for all users of the group ftpuser
DefaultRoot ~ ftpuser

# grant login only for members of the group
<Limit LOGIN>
DenyGroup !ftpuser
</Limit>

# disable root login and require a valid shell (from /etc/shells)
<Global>
RootLogin off
RequireValidShell on
</Global>

# increase
UseReverseDNS off
IdentLookups off

# Logging formats
LogFormat default "%h %l %u %t \"%r\" %s %b"
LogFormat auth "%v [%P] %h %t \"%r\" %s"
LogFormat write "%h %l %u %t \"%r\" %s %b"

# activate logging

# every login
ExtendedLog /var/log/ftp_auth.log AUTH auth

# file/dir access
ExtendedLog /var/log/ftp_access.log WRITE,READ write

# forr paranoid (big logfiles!)
#ExtendedLog /var/log/ftp_paranoid.log ALL default


```

---

### Post by a9k3d on 2009-05-14
Maybe change this to add AllowUser for your login for testing. 
> # grant login only for members of the group
<Limit LOGIN>
DenyGroup !ftpuser
</Limit>
If that works then check your ftpuser group has members you want.

---

### Post by Macmee on 2009-05-15
> **a9k3d said:**
> Maybe change this to add AllowUser for your login for testing. 

If that works then check your ftpuser group has members you want.

Nope, same error. 

Is there some way to just load users from a config file?

---

### Post by Kareeser on 2009-05-15
By default, proftpd allows all users who have an account on the host computer to log in. At the point, all you have to do to add a new user is run "adduser" in the terminal. Is that the functionality you want?

---

### Post by Macmee on 2009-05-16
> **Kareeser said:**
> By default, proftpd allows all users who have an account on the host computer to log in. At the point, all you have to do to add a new user is run "adduser" in the terminal. Is that the functionality you want?

Yes, but I can't login to any accounts on my system.


Edit: I ditched pftpd and got vsftpd. It worked like a charm. However say I login to account bob, and bob's home directory is /data/bob. Upon logging in it shows me /data/bob, but I can navigate back into the parent directories. Can I prevent this?

---

### Post by Kareeser on 2009-05-16
Not having used VSFTPd, I can't say, but ProFTPd has an option to "jail" users in their home directories. (In the conf file)

... and it's serious about that, there's no way you can navigate around that, so users won't be able to access places like /var/www.

---

