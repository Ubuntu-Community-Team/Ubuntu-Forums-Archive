---
title: "Unable to connect through ftp on VSFTPD"
date: 2013-11-25
forum: Server Platforms
---

### Post by colby.shores on 2013-11-25
[COLOR=#000000][FONT=verdana]I created a user named test from the command line.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]The users home directory is created and used passwd to create his password. I have also simplified my vsftpd.conf file to trace down the issue with authentication.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]My intention is to log in using test and have them have read write access to their home folder. It is not working however. What changes would you suggest to allow that to happen?[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Thanks in advance, [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Colby Shores


```

[/FONT][/COLOR]background=yes
listen=YES




# No anonymous login
anonymous_enable=NO
# Let local users login
# If you connect from the internet with local users, you should enable TLS/SSL/FTPS
local_enable=YES


# Write permissions
write_enable=YES[COLOR=#000000][FONT=verdana]
```
[/FONT][/COLOR]

---

### Post by thufirhawat2 on 2013-11-26
Is the code you posted currently the entire vsftpd.conf file? 

How are you testing to make sure the FTP site is working, and what error message are you getting specifically?

---

