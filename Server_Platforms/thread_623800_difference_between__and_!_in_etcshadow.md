---
title: "difference between * and ! in /etc/shadow"
date: 2007-11-26
forum: Server Platforms
---

### Post by hlynur on 2007-11-26
Does anyone know the exact  difference between ! * in the password field in the /etc/shadow file e.g. 


bla:!:13404:0:99999:7:::     
or
bla:*:13404:0:99999:7:::

I've used ! previously with on older debian servers for accounts that have passord authentication disabled i.e. only ssh key authentication. 

on ubuntu 6.06  i have to use * instead of !, else key authentication wont work.


Best Regards

---

### Post by koenn on 2007-11-26
man 5 shadow says
>        If the password field contains some string that is not valid result of
       crypt(3), for instance ! or *, the user will not be able to use a unix
       password to log in, subject to pam(7).

doesn't really help, does it ?

---

### Post by netlogic on 2007-11-26
* : User cannot login by password
! : User cannot login to the system

**examples**
* - core accounts lke daemon, bin, sys, sync, games, man, lp, mail, news, uucp, proxy, www-data,backup, list, irc,nobody
! - services and daemons like sshd, klog,syslog, bind, postfix,ftp.

i hope it helps

---

### Post by hlynur on 2007-11-27
ok thanks a lot

cheers / Thor

---

### Post by MJN on 2007-11-27
> **netlogic said:**
> * : User cannot login by password
! : User cannot login to the system
 
Well done that man - I couldn't find that info anywhere (why isn't such a fundamental aspect of configuration in the man pages..?)
 
Of course, this is where someone points out that it *is* in the man pages... ;)
 
Mathew

---

### Post by koenn on 2007-11-27
> **MJN said:**
> 
Of course, this is where someone points out that it *is* in the man pages... ;)
 

well, i looked in man 5 shadow, and then man 5 passwd, because that's where the passwords were before shadow, but i didn't see it. 
If it is in a man page, I' love to know where.

---

