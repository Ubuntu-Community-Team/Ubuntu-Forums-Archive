---
title: "proftpd weird login errors"
date: 2007-01-08
forum: Server Platforms
---

### Post by andytof47 on 2007-01-08
Hi I am trying to get proftpd up and running but i try a test login from the outside world and get the following

* About to connect() to community.ftpaccess.cc port 21
* Trying 219.90.145.253... connected
* Connected to community.ftpaccess.cc (219.90.145.253) port 21
< 220 My FTPD

> USER userftp
< 331 Anonymous login ok, send your complete email address as your password.

> PASS *****
< 230 Anonymous access granted, restrictions apply.

> PWD
< 257 "/" is current directory.
* Entry path is '/'

> CLNT Testing from [http://www.g6ftpserver.com/ftptest](http://www.g6ftpserver.com/ftptest) from IP xxx.xxx.xxx.xxx
< 500 CLNT not understood
* QUOT command failed with 500
* Connection #0 to host community.ftpaccess.cc left intact

* Closing connection #0


](*,) ](*,) ](*,) ](*,) 

anyhelp pleeeeeeeeaaaaasssssseeeeeee

---

### Post by asb on 2007-05-26
Hello,

Did you find an answer to this problem ?
I am trying to do the same thing using vsftpd and have exactly the same error.

Under Ubuntu Feisty.

thanks

Anthony

---

### Post by andytof47 on 2007-05-27
no unfortunately not.... gonna try it on fedora though

---

