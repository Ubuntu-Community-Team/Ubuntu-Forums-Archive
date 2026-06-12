---
title: "FTP Server problem"
date: 2012-01-29
forum: Server Platforms
---

### Post by poolet on 2012-01-29
Ok, A little bit of strange here maybe you have any ideas... I am trying to build a ftp server... I had a clear installation of proftpd. ( no error or warning messages no nothing ) I have also edit the proftpd.conf below it's my edited file, my problem is that at the beginning I had an error with  DispalyFirstChdir with that line and I figure out my self ( DispalyChdir) but now I have another fatal error  

```
Fatal: <Directory>: missing arguments on line 98 of '/etc/proftpd/proftpd.conf'   [fail]
```Dose anyone knows what that hell is that ? I have search all over the net and I didn't find anything about that error... the bad thing is that the message isn't determine what exactly is the problem just on line 98  at this line is the::::   

```
MaxClientsPerHost             1
```if anyone knows something please let me know as soon as possible.... Thank you in advance!!!! 


```

#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

ServerName            Debian
Serverident                     on "FTP"
ServerType            standalone
DeferWelcome            off
TimesGMT                        off


MultilineRFC2228        on
#DefaultServer            on
ShowSymlinks            on

TimeoutNoTransfer        600
TimeoutStalled            600
TimeoutIdle            1200

DisplayLogin                    welcome.msg
DisplayChdir                    .message
ListOptions                    '-l'

DenyFilter            \*.*/

AllowForeignAddress             on
AllowRetrieveRestart            on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd        off

# Uncomment this if you would use TLS module:
#TLSEngine             on

# Uncomment this if you would use quota module:
#Quotas                on

# Uncomment this if you would use ratio module:
#Ratios                on

# Port 21 is the standard FTP port.
Port                21
SocketBindTight                 on

PassivePorts                    11000 20000


# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances            30

# Set the user and group that the server normally runs at.
User                nobody
Group                nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                022  022
# Normally, we want files to be overwriteable.
AllowOverwrite            on

AllowForeignAddress             on
AllowRetrieveRestart            on
AllowStoreRestart on

# Speed up the server, no DNS lookups, just plain ip's. Turn off when being hax0r3d.
UseReverseDNS off
IdentLookups off

DefaultRoot                     ~
ExtendedLog                     /var/log/proftpd.all ALL


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
DelayEngine             off

<Anonymous ~ftp>
  User                          ftp
  Group                         nogroup
  UserAlias                     anonymous ftp
  DirFakeUser                   on ftp
  DirFakeGroup                  on ftp
  RequireValidShell             off
  MaxClients                    10
  DisplayLogin                  welcome.msg
  DisplayChdir                  .message
  AccessGrantMsg                "Anonymous access granted for user %u connecting."

  MaxClientsPerHost             1

  <Directory>
    #DenyAll
    TransferRate        RETR 50
    <Limit WRITE>
      DenyAll
    </Limit>
  </Directory>



```

---

### Post by shumifan50 on 2012-01-29
You have to specify a directory in the <Directory> tag 
e.g. <Directory /etc/ftpdir>

---

### Post by poolet on 2012-01-30
> **shumifan50 said:**
> You have to specify a directory in the <Directory> tag 
e.g. <Directory /etc/ftpdir>

I have already try that.. Buy seems fine now I just remove the lines: DisplayChdir and Dispalychr and seems the ftp server works, but isn't let me access to my specific folder from another pc...  

For example, I have also re-direct (with DMZ) my internal ip address of the server etc 192.168.X.XX to my router, each time that I am not home and I want to connect to my ftp server or I just want to connect with smdb protocol I just hit the ip address etc 45.245.120.290 when I hit the current ip the   router automatic re-direct to 192.168.X.XX and just open up login pop up.. I have also add 2 user to my server and I gave to them desktop authentications with passwords, the server respond OK but the problem is that isn't let me authenticate with the users names and passwords.. I also try  with my internal network from another computer.. But still nothing isn't works, any ideas ?? Thanks for your replying...

---

### Post by poolet on 2012-02-01
"Solved"   I changed distribution into Debian :-D

---

