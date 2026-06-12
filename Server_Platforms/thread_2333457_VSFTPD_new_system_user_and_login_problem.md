---
title: "VSFTPD new system user and login problem"
date: 2016-08-10
forum: Server Platforms
---

### Post by mcflay on 2016-08-10
Hi all,
today I have installed vsftpd service on my pc with Ubuntu 14.04 and I'm testing some configurations.
I started with anonymous login and it worked properly. Then I wanted to try login with system credentials, so I set these params:

```
anonymous_enable=NO
local_enable=YES
write_enable=YES

```

from /etc/vsftpd.conf. 
I have done login with my current user and also this configuration works without problems. In fact I'm able to see every files inside my home directory.
Then I have decided to create another user:

```
sudo useradd -d /home/ftpserver -m ftpserver
sudo passwd ftpserver

```

Restart the service
```
sudo service vsftpd restart
```

and login with the new user. But this time I get an error:
530 - Login incorrect

The new user is configured properly. In fact this command
```
su ftpserver

```

allows me to switch user without problems.
So I tried to find any differences inside /etc/passwd between my user (mark) and the new one. I get this:
```
mark:x:1000:1000:mark:/home/mark:/bin/bash
ftpserver:x:1002:1002::/home/ftpserver:

```

I notice that after 1002:1002 there is not any user before /home/ftpserver. I don't know if it can motivate something..
Anyway any advice is welcome! 


[COLOR=#555555][FONT=Monaco]
[/FONT][/COLOR]

---

### Post by steeldriver on 2016-08-10
The field between the 1002:1002 and the home directory is just the GECOS 'full name' - as far as I know, it has no significance and is fine to leave blank

The more significant difference is that your ftpserver user has no login shell - this will prevent interactive login, and may prevent vsftp authentication, unless you make other changes to your configuration. See for example 

[http://askubuntu.com/questions/129563/vsftpd-configuration-problems-with-12-04/](http://askubuntu.com/questions/129563/vsftpd-configuration-problems-with-12-04/)

[http://askubuntu.com/questions/617370/why-vsftpd-doesnt-work-when-pam-service-name-vsftpd](http://askubuntu.com/questions/617370/why-vsftpd-doesnt-work-when-pam-service-name-vsftpd)

NB I'm not sure which is the "right" solution in your case - hopefully someone more experienced can clarify

---

### Post by mcflay on 2016-08-10
Thanks for replay, you give me the right clue! 
In fact the problem was the code:
```
sudo useradd -d /home/ftpserver -m ftpserver
```

I had to launch instead this:
```
sudo useradd **-s /bin/bash** -d /home/ftpserver2 -m ftpserver2
```

in this way I'm able to login on ftp server also with the new user!

PS: instead of executing the articulate command *useradd* I would advise *adduser*. In fact with a simple
```
sudo adduser ftpserver3
```

every system operations will be executed automatically and also with this new user I will be able to login on ftp without problem :D

---

