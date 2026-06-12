---
title: "Ubuntu server 10.10 &amp; proftpd server"
date: 2010-12-17
forum: Server Platforms
---

### Post by nats463 on 2010-12-17
So, I am having a wicked problem with my ftp config.  I originally had to install a GUI and I think that was my first big mistake (im setting it up for a client) I've since decieded to go 100% CL, but I just got my logins to work (mostly)

I had to add a all new user that is jailed into their own directory.  I figured best way to do that was to give them a login that is pointed at anonymous.  I keep getting 530 error's and I have no idea why.  

The following is my config, can someone shed some light on this.  Thanks
And, yes I hacked, copied, changed, edited the general config floating on these boards.

# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
 UserAlias sauron userftp ftpuser admin ftpadministrator omnivestftp kmg

ServerName            "Images2Data"
ServerType             standalone
DeferWelcome            on

MultilineRFC2228 on
DefaultServer            on
ShowSymlinks            off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayLogin               Welcome.msg
DisplayChdir               .message
ListOptions                    "-l"

RequireValidShell         off

TimeoutLogin 20

RootLogin             off

# It's better for debug to create log files ;-)
ExtendedLog             /var/log/ftp.log
TransferLog             /var/log/xferlog
SystemLog            /var/log/syslog.log

#DenyFilter            \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart        on

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port                21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                022    022

PersistentPasswd        off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "Welcome to ...... Images2Data"

# This message is displayed for each access good or not 
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /media/Drive2/Images To Data/Laying The Foundation/9777 corrections

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
AllowUser kmg
AllowUser omnivestftp
DenyALL
</Limit>

<Directory /media/Drive2/Images To Data/Laying The Foundation/9777 correctionsed>
Umask 022 022
AllowOverwrite off
    <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
    DenyAll
    </Limit>
</Directory>

<Directory /home/ftp/download/>
Umask 022 022
AllowOverwrite off
    <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
    DenyAll
    </Limit>
</Directory>

<Directory /home/ftp/upload/>
Umask 022 022
AllowOverwrite on
    <Limit READ RMD DELE>
          DenyAll
        </Limit>

        <Limit STOR CWD MKD>
          AllowAll
        </Limit>
</Directory>
# A basic anonymous configuration, no upload directories.  If you do not
# want anonymous users, simply delete this entire <Anonymous> section.
<Anonymous ~omnivestftp>
  User                          omnivestftp
  Group                         omnivestftp
  UserAlias                     ftp omnivestftp
  UserAlias                     anonymous omnivestftp
  AuthAliasOnly                 on

  # We want clients to be able to login with "anonymous" as well as "ftp"
  UserAlias                     anonymous ftp

  # Limit the maximum number of anonymous logins
  MaxClients                    5

  # We want 'welcome.msg' displayed at login, and '.message' displayed
  # in each newly chdired directory.
  DisplayLogin                  welcome.msg
  DisplayChdir                  .message

  # Limit WRITE everywhere in the anonymous chroot
  <Limit WRITE>
    DenyAll
  </Limit>
<Directory /home/ftp/*>
Umask 022 022
AllowOverwrite off
     <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
    DenyAll
    </Limit>
</Directory>

<Directory /home/ftp/download/>
Umask 022 022
AllowOverwrite off
    <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
    DenyAll
    </Limit>
</Directory>

<Directory /home/ftp/upload/>
Umask 022 022
AllowOverwrite on
    <Limit READ RMD DELE>
    DenyAll
    </Limit>

    <Limit STOR CWD MKD>
    AllowAll
    </Limit>
</Directory>
</Anonymous>

---

