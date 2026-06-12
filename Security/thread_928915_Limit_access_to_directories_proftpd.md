---
title: "Limit access to directories proftpd"
date: 2008-09-24
forum: Security
---

### Post by thegodfaza on 2008-09-24
I am trying to set up a ftp server and no matter what I try I can't restrict an authenticated user from being able to access any directory. When the user logs on the default root is their home directory. But they can move about the file system freely. Here is my proftpd.conf

```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

UseReverseDNS off
<global>
IdentLookups off
</global>

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
DefaultRoot			~ ftpuser

<Directory />
AllowOverwrite off
<Limit ALL>
DenyUser *
DenyGroup *
Order Deny,Allow
Deny ALL
</Limit>
</Directory>

<Directory /var/www>
AllowOverwrite on
<limit ALL>
Order Allow,Deny
DenyGroup !ftpuser
Deny ALL
</Limit>
</Directory>

<limit LOGIN>
DenyGroup !ftpuser
</Limit>

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
#<Directory *>
#   <Limit READ WRITE>
#      DenyAll
#   </Limit>
#</Directory>
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

### Post by thegodfaza on 2008-09-25
[BUMP]
46 views and 0 replies...

---

### Post by beniji on 2008-09-27
You need to use 

DefaultRoot ~

If that doesn't work for some reason (it does for me), you should tail the proftpd log under /var/log/proftpd to see if there are any errors (e.g. containing the text "chroot").

---

### Post by pslStu on 2008-10-14
I'm having the same issue. 

I'm using **DefaultRoot ~** but that's not helped, and the log file in /var/log/proftpd isn't bringing up anything related (the last entry was a few minutes previous when I restarted the service).

If it's working for you and not us, there must be something (probably small) that differs with the configuration. Could the permissions on the individual folders make a difference? Is there a file elsewhere that needs a line adding or something?

---

### Post by hyper_ch on 2008-10-14
is there a reason to use ftp instead of sftp/scp?

---

### Post by cariboo on 2008-10-14
The way you have your config file you are trying to set two defaultroots:

```
DefaultRoot			~ ftpuser

```

The tilde "~" means the users home directory, I know this works because I have tried it my self. The way you have it setup nothing will work. you have to setup defaultroot with the full path to ftpuser for example:

```
DefaultRoot			/home/ftpuser
```

Jim

---

### Post by captain_bkx on 2008-11-28
You can use this setting:

DefaultRoot ~

and don't forget to restart your proftp using this command:
/etc/init.d/proftpd restart

I've just changed it and it works perfect

---

