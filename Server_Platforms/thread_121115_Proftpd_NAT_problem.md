---
title: "Proftpd NAT problem"
date: 2006-01-24
forum: Server Platforms
---

### Post by hawking on 2006-01-24
I have proftpd installed on my machine which is on a NAT.The server works normal when I run it with internal IP ([ftp://localhost](ftp://localhost)) but when I use the external IP for that it asks for username and password but then it gives this error :  530 : Login failed. Below is my proftpd.conf file. I'll appreciate if you can help me with this 

##*PROFTPD.conf

# To really apply changes reload proftpd after modifications.
AllowOverwrite on
#AuthAliasOnly on
PersistentPasswd on
# Choose here the user alias you want !!!!
UserAlias sauron userftp

ServerName                      "ChezFrodon"
ServerType                      standalone
DeferWelcome                    on

MultilineRFC2228 on
DefaultServer                   on
ShowSymlinks                    off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                     "-l"

RequireValidShell               off

TimeoutLogin 20

RootLogin                       off

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

#DenyFilter                     \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart               on
#AllowForeignAddress             on
# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port                            21
MasqueradeAddress     81.214.221.189
PassivePorts 60000 65535 
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
Umask                           022     022

#PersistentPasswd                off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
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

---

### Post by frodon on 2006-01-24
You should keep the "AuthAliasOnly on" option if you use aliasing (it's the case as i see in your config file). 
Did you use "sauron" or "userftp" as username ?
Have you well created the userftp user ?

---

### Post by hawking on 2006-01-24
[QUOTE=frodon]You should keep the "AuthAliasOnly on" option if you use aliasing (it's the case as i see in your config file). 
Did you use "sauron" or "userftp" as username ?
Have you well created the userftp user ?[/QUOTE]

well I just turned it off as I was desperate about finding any solutions.. it doesn't change the result .. I tried it as it's on and I got the same error and yes there is a userftp user in my computer. :/

---

### Post by robinl on 2006-01-25
I've had the exact same problem before, but with Windows and Filezilla. The solution? Turn off ftp access to router (you have to gain access to the router's config page first), forward ports if you haven't already done so, turn on DMZ (optional, but I have to) and change the http config of your router to a different port in case you need http server is well.
Currently your firend is trying to access your router's ftp and I don't think it's what you wanted... ;)

---

