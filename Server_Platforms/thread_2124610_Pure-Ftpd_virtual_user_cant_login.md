---
title: "Pure-Ftpd virtual user cant login"
date: 2013-03-11
forum: Server Platforms
---

### Post by pawan_lal on 2013-03-11
Hi All,

i have made pure-ftpd on ubuntu machine,problem is that when i am running ftp its giving error.below is tha code and  error message.

#!/bin/bash
groupadd ftpgroup
useradd -g ftpgroup -d /dev/null -s /etc ftpuser
echo "
[*] Setting up FTP user abc\n"
pure-pw useradd abc -u ftpuser -d /ftphome/offsec
pure-pw mkdb
cd /etc/pure-ftpd/auth
ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/60pdb
echo "
[*] Setting home directory in /ftphome/\n"
mkdir /ftphome
chown -R ftpuser:ftpgroup /ftphome/offsec
echo "
[*] Starting FTP server\n"
/etc/init.d/pure-ftpd restart

#######################

root@bt:/var/www# ftp 127.0.0.1
Connected to 127.0.0.1.
220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 1 of 50 allowed.
220-Local time is now 22:54. Server port: 21.
220-This is a private system - No anonymous login
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.
Name (127.0.0.1:root): abc
331 User abc OK. Password required
Password:
530 Login authentication failed
Login failed.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp>

******************************

root@:/var/www# vim /etc/pure-ftpd/auth/
60pdb   65unix  70pam

root@:/var/www# cat /etc/pure-ftpd/auth/60pdb
root@:/var/www#

root@:/var/www# cat /etc/pure-ftpd/auth/65unix
no

root@:/var/www# cat /etc/pure-ftpd/auth/70pam
no                                       

Any help or guidance will be highly appreciated.

thx

---

### Post by fragtion on 2013-04-30
Your PureDB (60pdb) file seems empty. It needs to point (internal reference, not symlink) to the db file made by pure-pw. To do that, try this:
> 
echo /etc/pure-ftpd/pureftpd.pdb > /etc/pure-ftpd/conf/PureDB
service pure-ftpd restart

Let me know if this works for you

---

### Post by mbnoimi on 2013-05-29
I've similar problem but I configured pureFtpd by another way:
```
mbnoimi-pc conf # apt-get install pure-ftpd
mbnoimi-pc conf # cd /etc/pure-ftpd/conf/
mbnoimi-pc conf # echo yes > ChrootEveryone
mbnoimi-pc conf # echo yes > CreateHomeDir
mbnoimi-pc conf # echo 10 > MaxClientsNumber
mbnoimi-pc conf # echo 3 > MaxClientsPerIP
mbnoimi-pc conf # echo yes > NoAnonymous
mbnoimi-pc conf # echo no > DisplayDotFiles
mbnoimi-pc conf # echo yes > DontResolve
mbnoimi-pc conf # echo 5 > MaxIdleTime
mbnoimi-pc conf # echo yes > PAMAuthentication
mbnoimi-pc conf # echo no > AnonymousCanCreateDirs 
mbnoimi-pc conf # echo 007 007 > Umask
mbnoimi-pc conf # echo yes > ProhibitDotFilesWrite
mbnoimi-pc conf # echo yes > ProhibitDotFilesRead
mbnoimi-pc conf # echo no > AutoRename
mbnoimi-pc conf # echo yes > NoChmod
mbnoimi-pc conf # echo no > KeepAllFiles
mbnoimi-pc conf # echo 0 > TLS
mbnoimi-pc conf # /etc/init.d/pure-ftpd restart
Restarting ftp server: Running: /usr/sbin/pure-ftpd -l pam -j -x -X -C 3 -Y 0 -H -I 5 -R -E -u 1000 -U 007:007 -A -O clf:/var/log/pure-ftpd/transfer.log -8 UTF-8 -c 10 -B
```

Then I opened PureAdmin and added a new user "test" as shown below
[ATTACH=CONFIG]243219[/ATTACH]

but I'm unable to login!!!
```
220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 1 of 10 allowed.
220-Local time is now 13:01. Server port: 21.
220-This is a private system - No anonymous login
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 5 minutes of inactivity.
       USER test
331 User test OK. Password required
       PASS (password not shown)
530 Login authentication failed
```

The content of /etc/pure-ftpd
```
mbnoimi-pc pure-ftpd # ls auth/
65unix  70pam
mbnoimi-pc pure-ftpd # cat auth/65unix 
no
mbnoimi-pc pure-ftpd # cat auth/70pam 
yes
mbnoimi-pc pure-ftpd # cat pureftpd.passwd 
test:$1$O1zF99b0$oH7S4lxScfwMoPpyvBywr.:119:130::/home/ftpusers/./::::::::::::
mbnoimi-pc pure-ftpd # 
```

---

### Post by mbnoimi on 2013-05-30
Bump

---

