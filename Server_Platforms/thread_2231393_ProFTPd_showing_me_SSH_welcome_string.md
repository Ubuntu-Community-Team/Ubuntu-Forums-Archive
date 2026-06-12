---
title: "ProFTPd showing me SSH welcome string?"
date: 2014-06-25
forum: Server Platforms
---

### Post by fowie on 2014-06-25
I just upgraded to 14.04 and got a new internet provider for my server.  Now, when I try to FTP in (port 21), I see the SSH welcome string?  If I'm on the server itself, ftp myserver.com works just fine, but using ftp outside the server ends up connecting but showing me
SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2

Any idea why my requests to port 21 are being auto-redirected to port 22?  I don't have sftp support set up in proftd:
```

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6                         off
# If set on you can experience a longer connection delay in many cases.
IdentLookups                    off

ServerName                      "ProFTPd"
ServerIdent                     on
ServerType                      inetd
DeferWelcome                    off

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks on

TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200

DisplayLogin                    welcome.msg
DisplayChdir .message true
ListOptions "-l"

DenyFilter                      \*.*/

# Use this to jail all users in their homes
# DefaultRoot                   ~
# Port 21 is the standard FTP port.
Port         21
MaxInstances                    30

# Set the user and group that the server normally runs at.
User                            proftpd
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask 022 022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>

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

<Global>
DefaultRoot ~
ShowSymlinks on
</Global>


```
my modules.conf:
```

ModulePath /usr/lib/proftpd
  8
  9 # Allow only user root to load and unload modules, but allow everyone
 10 # to see which modules have been loaded
 11
 12 ModuleControlsACLs insmod,rmmod allow user root
 13 ModuleControlsACLs lsmod allow user *
 14
 15 LoadModule mod_ctrls_admin.c
 16 LoadModule mod_tls.c
LoadModule mod_radius.c
 50 LoadModule mod_quotatab.c
 51 LoadModule mod_quotatab_file.c
 52
 53 # Install proftpd-mod-ldap to use this
 54 #LoadModule mod_quotatab_ldap.c
 55
 56 # Install proftpd-mod-pgsql or proftpd-mod-mysql to use this
 57 #LoadModule mod_quotatab_sql.c
 58 LoadModule mod_quotatab_radius.c
 59 LoadModule mod_wrap.c
 60 LoadModule mod_rewrite.c
 61 LoadModule mod_load.c
 62 LoadModule mod_ban.c
 63 LoadModule mod_wrap2.c
 64 LoadModule mod_wrap2_file.c
 65 # Install proftpd-mod-pgsql or proftpd-mod-mysql to use this
 66 #LoadModule mod_wrap2_sql.c
 67 LoadModule mod_dynmasq.c
 68
 69
 70 # keep this module the last one
 71 LoadModule mod_ifsession.c

```

---

### Post by fowie on 2014-08-26
I'm seeing the same issue with SMTP?

---

