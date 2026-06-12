---
title: "Where to find SSH Server Configuration Howto for Dummies?"
date: 2010-11-28
forum: Server Platforms
---

### Post by rule-of-three on 2010-11-28
Where to find SSH Server Configuration Howto for Dummies?

To Ubuntu 10.04 LTS Server?

Must work like FTP/SFTP and user accounts must be in MySQL.

Just for File Transfer and user can open only his / her own ./ where is public_html in root..

???

---

### Post by HermanAB on 2010-11-28
Howdy,

The man pages are pretty good:
$ man sshd

Also see the snail book:
[http://www.snailbook.com/](http://www.snailbook.com/)

---

### Post by James78 on 2010-11-28
You could also start reading some stuff [here]("https://help.ubuntu.com/community/SSH").

---

### Post by eeffoc on 2010-11-28
Your best bet is installing the OpenSSH client and server:

 	Code:
 	sudo apt-get install openssh-client 

 	Code:
 	sudo apt-get install openssh-server 

Then, you will want to install and configure vsftpd as your primary FTP|SFTP software.

 	Code:
 	sudo apt-get install vsftpd 
__Here is a good write-up on vsftpd: 
[vsftpd installation and configuration]("http://ubuntuforums.org/showthread.php?t=518293")

To connect to your SSH server, simply run:
 	Code:
 	ssh remoteusername@remoteusermachine 
 You can transfer files via SSH, but I think with what you described, you will want to setup vsftpd.

For a bit more information on OpenSSH:
[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

Hopefully, that is enough information to get you on the right path. 

Good luck! :p

---

### Post by apollothethird on 2010-11-28
> **rule-of-three said:**
> Where to find SSH Server Configuration Howto for Dummies?

To Ubuntu 10.04 LTS Server?

Must work like FTP/SFTP and user accounts must be in MySQL.

Just for File Transfer and user can open only his / her own ./ [color=green]**where is public_html in root..**[/color]

???

You shouldn't, and shouldn't want to open up any public access to root.  By default the /root directory is only accessible (read and executable) to root.

Most people consider the root directory of the html default area the root of their server.  Why not use that for what you want the public to access?

Consider using your Apache root directory which by default is /var/www; or you can make a subdirectory up from there for this purpose.  This way you'll know exactly what has been specified for public access on the web.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

