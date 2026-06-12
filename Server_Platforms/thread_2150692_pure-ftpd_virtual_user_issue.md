---
title: "pure-ftpd virtual user issue"
date: 2013-06-01
forum: Server Platforms
---

### Post by mbnoimi on 2013-06-01
All virtual users of pure-ftpd can't login although I configured them without any error message!

Login error message:
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

Here's pure-ftpd configurations:
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

[img]https://imageshack.us/a/img24/5412/pureadminusers001.png[/img]

---

### Post by mbnoimi on 2013-06-03
Bump

---

