---
title: "ProFTPd Times out before login..."
date: 2009-08-19
forum: Server Platforms
---

### Post by Surd on 2009-08-19
ProFTPd (The latest one from apt-get) times out when it trys to get the welcome message.
FileZilla gives this output:
```

[SIZE=1]Status: Resolving address of dhnet.co.uk[/SIZE]
[SIZE=1]Status: Connecting to XX.XXX.XXX.XX:21...[/SIZE]
[SIZE=1]Status: Connection established, waiting for welcomemessage...[/SIZE]
[SIZE=1][COLOR=#ff0000][SIZE=1][COLOR=#ff0000]Error: Connection timed out[/COLOR][/SIZE][/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000][SIZE=1][COLOR=#ff0000]Error: Could not connect to server[/COLOR][/SIZE]
[/COLOR][/SIZE]
```
 
Ive checked my proftpd.conf files' syntax using the build in tool so that is correct. The passive ports, Port 21 are alll unblocked in UFW and forwarded to the server via my router.
The system is fine as i briefly used Pure-Ftpd but it was too complicated for virtual users. Im sure its a problem with the software. Im using Ubuntu Server 9.04
 
If you need any things copied, give me a shout.

---

### Post by Surd on 2009-08-20
here is proftpd.conf
```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#
# Includes DSO modules
Include /etc/proftpd/modules.conf
# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6                         off
# If set on you can experience a longer connection delay in many cases.
IdentLookups                    off
ServerName                      "DeltaHost Networks -=- FTP Service"
ServerType                      standalone
DeferWelcome                    off
MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    on
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
# RequireValidShell             off
# Port 21 is the standard FTP port.
Port                            21
# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
PassivePorts                  50000 50100
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
User                            ftp
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
<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>
<IfModule mod_ratio.c>
Ratios off
</IfModule>

# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
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
<Anonymous ~ftp>
   User                         ftp
   Group                        nogroup
   # We want clients to be able to login with "anonymous" as well as "ftp"
   UserAlias                    anonymous ftp
   # Cosmetic changes, all files belongs to ftp user
   DirFakeUser  on ftp
   DirFakeGroup on ftp
   RequireValidShell            off
   # Limit the maximum number of anonymous logins
   MaxClients                   10
   # We want 'welcome.msg' displayed at login, and '.message' displayed
   # in each newly chdired directory.
   DisplayLogin                 welcome.msg
   DisplayChdir                 .message
   # Limit WRITE everywhere in the anonymous chroot
   <Directory *>
     <Limit WRITE>
       DenyAll
     </Limit>
   </Directory>
   # Uncomment this if you're brave.
   # <Directory incoming>
   #   # Umask 022 is a good standard umask to prevent new files and dirs
   #   # (second parm) from being group and world writable.
   #   Umask                            022  022
   #            <Limit READ WRITE>
   #            DenyAll
   #            </Limit>
   #            <Limit STOR>
   #            AllowAll
   #            </Limit>
   # </Directory>
</Anonymous>

```
As a webhost, FTP is one of the major components of my company and we have customers waiting to upload their sites so it is importnant that this problem gets fixed soon.
Thanks,
Conor. M

---

### Post by hessiess on 2009-08-20
You have probably got some firewalls somewhere misbehaving, the FTP protocol is a outdated mess and dousen't work well with firewalls or NAT. May I suggest using SFTP instead, it is much more secure and dousen't have any of the problems of FTP.

---

### Post by Surd on 2009-08-20
Hmm, im new to the web hosting business. Will SFTP mean my customers will have to use special clients?
Also, I used ProFTPd before but then i installed ispCP Omega, didnt like it, Completely removed it then switched back to ProFTPd so it was working before but it suddenly stopped.

---

### Post by hessiess on 2009-08-21
> **Surd said:**
> Hmm, im new to the web hosting business. Will SFTP mean my customers will have to use special clients?


For windows, yes: [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php), for everything else, no. but the advantages (vastly improved security and up to date protocol design) outweigh the need for a spatial client.

If your users are developing web applications then sftp is also a better option as it can be mounted as a part of the local file system without being unbearably slow, removing the need to manually re upload files(which is a pain if your app consists of more than one or two files).

---

### Post by Surd on 2009-08-23
Ok, well i have to use SFTP to work with my site now. I still am looking for a method of FTP as Dreamweaver etc cant use SFTP. Ive also noticed that SFTP relies on the UNIX user authentication. Is there a way of virtual users AND unix users?

---

