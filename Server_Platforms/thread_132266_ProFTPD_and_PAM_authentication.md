---
title: "ProFTPD and PAM authentication"
date: 2006-02-18
forum: Server Platforms
---

### Post by Tokuma on 2006-02-18
I am new to both Linux and Ubuntu so please forgive my ignorance. I recentally setup a computer as a linux server using xampp. The entire server works fine except the ftp part of it. I keep getting the error 503 Login Incorrect. After looking around on the interrnet I saw that the error I was experiecing had somthing to do with the PAM authorization system. No matter what I do I cant figure it out. Basically what I want is that every user that I have on my pc can have their own ftp directory. So for example if I want to give a friend some free webhosting all I have to do is make then a user, make a new dir in my htdocs folder, add a symbolic link in their home dir called www, then add that user to the group ftp. Any help would be appreciated.

here is my proftpd.conf file
```

ServerName                      "Caffeine-Overdose" 
ServerType                      standalone 
Port                            21
Umask                           022
MaxInstances                    30
User                            ftp
Group                           ftp

DefaultRoot ~/www

<Directory /*>
    AllowOverwrite                on 
</Directory>

<Limit WRITE>
    Allow from all
</Limit>

<limit PortPasv>
    AllowAll
</limit> 

<Anonymous /home/ftp>
  User                          ftp
  Group                         ftp
  UserAlias                     anonymous ftp
  MaxClients                    10
  RequireValidShell             no
  AccessGrantMsg                "Welcome to my FTP Server!"

  <Limit WRITE>
    Deny from all
  </Limit>

</Anonymous>

```

---

