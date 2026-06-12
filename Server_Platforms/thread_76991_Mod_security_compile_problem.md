---
title: "Mod_security compile problem ???"
date: 2005-10-16
forum: Server Platforms
---

### Post by dbee on 2005-10-16
I'm trying to compile mod_sec using gcc but I only get this ...

root@ubuntu:/home/apachesrc/modsecurity-1.8.7/apache1 # gcc -o mod_security.o mod_security.c
mod_security.c:31:19: httpd.h: No such file or directory
mod_security.c:32:25: http_config.h: No such file or directory
mod_security.c:33:26: http_request.h: No such file or directory
mod_security.c:34:27: http_protocol.h: No such file or directory
mod_security.c:35:23: http_core.h: No such file or directory
mod_security.c:36:23: http_main.h: No such file or directory
mod_security.c:37:22: http_log.h: No such file or directory
mod_security.c:38:25: util_script.h: No such file or directory
mod_security.c:57: error: syntax error before "MODULE_VAR_EXPORT"
mod_security.c:57: warning: data definition has no type or storage class
mod_security.c:241: error: syntax error before "request_rec"
mod_security.c:241: warning: no semicolon at end of struct or union
mod_security.c:244: error: syntax error before '}' token
mod_security.c:244: warning: data definition has no type or storage class

does anyone know the problem ???

---

### Post by lithorus on 2005-10-17
Well for starters you didn't specify your include paths. This can be done with something like this :
```
gcc -o mod_security.o -I/usr/include/apache-1.3 mod_security.c
```
If the path is not there you might have to install the include files. To search for files inside not-installed .deb packages you can use apt-file :
```
apt-get install apt-file
apt-file update
apt-file search httpd.h
```

Are you sure there wasn't a make file?

---

### Post by dbee on 2005-10-17
Hi lithorus,

Thanks a bunch for the reply ... I have been having serious problems with the mod_sec install and no-one seems to have any clue.

The problem here is mainly that the 

apxs -cia mod_security.c 

function doesn't actually work so I have to compile it myself. I really don't know why the above command won't compile the mod.

I can get a pre-compiled mod though, but when I try to run it with chroot I get

The first bit is from the error_log file

[Mon Oct 17 15:15:23 2005] [notice] mod_security: chroot checkpoint #1 (pid=11846 ppid=11844)
[Mon Oct 17 15:15:23 2005] [notice] mod_security: chroot checkpoint #2 (pid=11847 ppid=11846)
[Mon Oct 17 15:15:23 2005] [notice] mod_security: chroot successful, path=/chroot/usr/local/apache2/
[Mon Oct 17 15:15:23 2005] [error] (2)No such file or directory: could not create /usr/local/apache2/logs/httpd.pid
[Mon Oct 17 15:15:23 2005] [error] httpd: could not log pid to file /usr/local/apache2/logs/httpd.pid

the httpd.pid file is there but it can't see it

root@ubuntu:/usr/local/apache2/bin # stat /chroot/usr/local/apache2/logs/httpd.pid
  File: `/chroot/usr/local/apache2/logs/httpd.pid'
  Size: 0               Blocks: 0          IO Block: 4096   regular empty file
Device: 301h/769d       Inode: 686793      Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1002/   httpd)   Gid: ( 1002/   httpd)
Access: 2005-10-17 15:11:47.212720704 +0900
Modify: 2005-10-17 15:11:47.212720704 +0900

any help here would be greatly appreciated as this problem has been taking me a little longer to sort out than I'd imagined

thanks

---

