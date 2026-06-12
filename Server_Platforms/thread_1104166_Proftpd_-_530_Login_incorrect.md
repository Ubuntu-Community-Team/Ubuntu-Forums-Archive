---
title: "Proftpd - 530 Login incorrect"
date: 2009-03-23
forum: Server Platforms
---

### Post by woland on 2009-03-23
Hi!

I'm using Ubuntu 8.10 server.

Each time I'm trying to login I'm getting error 530.

I've installed proftpd via apt-get.

I've created a user to login with.
The user is not listed in ftpusers.

Any ideas?

Thanks!

The proftpd.conf file contents are:
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

ServerName			"GATE"
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
DefaultRoot			~

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

```

---

### Post by mcfly1337 on 2009-03-23
My ProFTPd uses my Ubuntu users. Try logging in to the ftp with the same username / password you use to access your system.

---

### Post by woland on 2009-03-23
I've tried that as well.

---

### Post by mcfly1337 on 2009-03-23
Hmm... 

[http://ubuntuforums.org/showpost.php?p=446961&postcount=10](http://ubuntuforums.org/showpost.php?p=446961&postcount=10)

---

### Post by Praill on 2009-06-25
For me this took forever to solve and noone had the correct resolution. For some reason I had to comment out:
```

# Set the user and group that the server normally runs at.
User ftp
Group nogroup

```

to

```

# Set the user and group that the server normally runs at.
#User ftp
#Group nogroup

```

This completely fixed the problem for me.

---

### Post by rjbell on 2010-05-03
This took me forever to figure out and numerous Google searches turned up nothing.

I installed ProFTPd via Webmin and kept getting 530 errors even when logging in as root.

However, I noticed that one of the settings in Webmin's module showed "Deny users in /etc/ftpusers" set to 'Default' I set this to "Off" and now I can log in.

In the proftpd.conf file, you need to set (or add) the line:

```
UseFtpUsers off
```

Hope this helps someone else with a similar issue.

---

### Post by tekknokrat on 2010-06-01
> **rjbell said:**
> This took me forever to figure out and numerous Google searches turned up nothing.

I installed ProFTPd via Webmin and kept getting 530 errors even when logging in as root.

However, I noticed that one of the settings in Webmin's module showed "Deny users in /etc/ftpusers" set to 'Default' I set this to "Off" and now I can log in.

In the proftpd.conf file, you need to set (or add) the line:

```
UseFtpUsers off
```

Hope this helps someone else with a similar issue.

Sorry if I miss the topic. But */etc/ftpusers* is exactly for disabling root access. root access via ftp is a high security impact.

---

