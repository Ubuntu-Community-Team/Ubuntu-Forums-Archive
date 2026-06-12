---
title: "ProFTPd and inetd"
date: 2006-01-04
forum: Server Platforms
---

### Post by t0bb3 on 2006-01-04
When I try to connect to my ftp server I get an error saying "Connect call failed!". I think the reason is that the ftp server isn't actually running, but I don't know how to check.

My proftpd.conf
```
#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

AllowOverwrite                  on
AuthAliasOnly                   on
AuthUserFile                    /etc/proftpd.passwd

UserAlias                       upload userftp
UserAlias                       mp3 ftpmp3

ServerName                      "htpc"
ServerType                      inetd
DeferWelcome                    on

MasqueradeAddress               t0bb3.gotdns.com
#this is a range, not just two ports:
PassivePorts                    60000 60100

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    off

TimeoutNoTransfer               600
TimeoutStalled                  100
TimeoutIdle                     2200

DisplayFirstChdir               .message
ListOptions                     "-l"

RequireValidShell               off

TimeoutLogin 20

RootLogin                       off

# It's better for debugging purposes to create log files
ExtendedLog                     /var/log/ftp/ftp.log
TransferLog                     /var/log/ftp/xferlog
SystemLog                       /var/log/ftp/syslog.log

#DenyFilter                     \*.*/

UseFtpUsers                     on
- Hide quoted text -

# Allow to restart a download
AllowStoreRestart               on

# Port 21 is the standard FTP port, so don't use it for security
reasons (choose here the port you want)
Port                            2121

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                            nobody
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022     022

PersistentPasswd                off

MaxClients                      8
MaxClientsPerHost               8
MaxClientsPerUser               8
MaxHostsPerUser                 8

# Display a message after a successful login
AccessGrantMsg                  "welcome to t0bb3's ftp server"
# This message is displayed for each access good or not
ServerIdent                     on       "HTPC ftp server"

# Set /home/FTP-shared directory as home directory
DefaultRoot                     /home/FTP-shared

# Lock all the users in home directory,
#    ***** really important *****
DefaultRoot                     ~

# It will look like the current user owns all files
# This is good when using virtual users
DirFakeUser                     on ~
DirFakeGroup                    on ~

MaxLoginAttempts                3

#VALID LOGINS
<Limit LOGIN>
       AllowUser userftp
       AllowUser ftpmp3
       DenyALL
</Limit>

<Directory /home/FTP-shared>
       Umask 022 022
       AllowOverwrite off
       HideNoAccess on

       <Limit ALL>
               Order Allow,Deny
               IgnoreHidden on
               AllowUser userftp
               AllowUser mp3
               Deny ALL
       </Limit>

       <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
               DenyAll
       </Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
       Umask 022 022
       AllowOverwrite off

       <Limit ALL>
               Order Allow,Deny
               AllowUser userftp
               AllowUser ftpmp3
               Deny ALL
       </Limit>

       <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
               DenyAll
       </Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
       Umask 022 022
       AllowOverwrite on

       <Limit READ RMD DELE>
               DenyAll
       </Limit>

       <Limit STOR CWD MKD>
               AllowAll
       </Limit>
</Directory>

<Directory /home/FTP-shared/mp3/*>
       Umask 022 022
       AllowOverwrite off

       <Limit ALL>
               Order Allow,Deny
               AllowUser ftpmp3
               Deny ALL
       </Limit>

       <Limit MKD>
               Order Allow,Deny
               AllowUser ftpmp3
               Deny ALL
       </Limit>

       <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
               DenyAll
       </Limit>
</Directory>
```

And inetd.conf
```
ftp     stream  tcp     nowait  root    /usr/sbin/tcpd /usr/sbin/proftpd
```

Does anyone see anything wrong?

---

### Post by linuxfan on 2006-01-20
[QUOTE=t0bb3]When I try to connect to my ftp server I get an error saying "Connect call failed!". I think the reason is that the ftp server isn't actually running, but I don't know how to check.

My proftpd.conf
```
#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

AllowOverwrite                  on
AuthAliasOnly                   on
AuthUserFile                    /etc/proftpd.passwd

UserAlias                       upload userftp
UserAlias                       mp3 ftpmp3

ServerName                      "htpc"
ServerType                      inetd
DeferWelcome                    on

MasqueradeAddress               t0bb3.gotdns.com
#this is a range, not just two ports:
PassivePorts                    60000 60100

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    off

TimeoutNoTransfer               600
TimeoutStalled                  100
TimeoutIdle                     2200

DisplayFirstChdir               .message
ListOptions                     "-l"

RequireValidShell               off

TimeoutLogin 20

RootLogin                       off

# It's better for debugging purposes to create log files
ExtendedLog                     /var/log/ftp/ftp.log
TransferLog                     /var/log/ftp/xferlog
SystemLog                       /var/log/ftp/syslog.log

#DenyFilter                     \*.*/

UseFtpUsers                     on
- Hide quoted text -

# Allow to restart a download
AllowStoreRestart               on

# Port 21 is the standard FTP port, so don't use it for security
reasons (choose here the port you want)
Port                            2121

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                            nobody
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022     022

PersistentPasswd                off

MaxClients                      8
MaxClientsPerHost               8
MaxClientsPerUser               8
MaxHostsPerUser                 8

# Display a message after a successful login
AccessGrantMsg                  "welcome to t0bb3's ftp server"
# This message is displayed for each access good or not
ServerIdent                     on       "HTPC ftp server"

# Set /home/FTP-shared directory as home directory
DefaultRoot                     /home/FTP-shared

# Lock all the users in home directory,
#    ***** really important *****
DefaultRoot                     ~

# It will look like the current user owns all files
# This is good when using virtual users
DirFakeUser                     on ~
DirFakeGroup                    on ~

MaxLoginAttempts                3

#VALID LOGINS
<Limit LOGIN>
       AllowUser userftp
       AllowUser ftpmp3
       DenyALL
</Limit>

<Directory /home/FTP-shared>
       Umask 022 022
       AllowOverwrite off
       HideNoAccess on

       <Limit ALL>
               Order Allow,Deny
               IgnoreHidden on
               AllowUser userftp
               AllowUser mp3
               Deny ALL
       </Limit>

       <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
               DenyAll
       </Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
       Umask 022 022
       AllowOverwrite off

       <Limit ALL>
               Order Allow,Deny
               AllowUser userftp
               AllowUser ftpmp3
               Deny ALL
       </Limit>

       <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
               DenyAll
       </Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
       Umask 022 022
       AllowOverwrite on

       <Limit READ RMD DELE>
               DenyAll
       </Limit>

       <Limit STOR CWD MKD>
               AllowAll
       </Limit>
</Directory>

<Directory /home/FTP-shared/mp3/*>
       Umask 022 022
       AllowOverwrite off

       <Limit ALL>
               Order Allow,Deny
               AllowUser ftpmp3
               Deny ALL
       </Limit>

       <Limit MKD>
               Order Allow,Deny
               AllowUser ftpmp3
               Deny ALL
       </Limit>

       <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
               DenyAll
       </Limit>
</Directory>
```

And inetd.conf
```
ftp     stream  tcp     nowait  root    /usr/sbin/tcpd /usr/sbin/proftpd
```

Does anyone see anything wrong?[/QUOTE]
Did you try refreshing inetd by using the command ...

# sudo /etc/init.d/inetd restart

If you have Firestarter running, make sure you create an inbound rule to accept connections.

Cheers

---

### Post by t0bb3 on 2006-01-20
Thanks for your reply. I uninstalled proFTPd, removed all config files, installed it again and disabled xinetd. And now it works :)

Ohh, and I added a new line to /etc/services because I didn't want my ftp to run on port 21...

---

