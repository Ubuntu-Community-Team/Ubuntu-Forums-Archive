---
title: "Ubuntu server ispconfig3"
date: 2012-04-03
forum: Server Platforms
---

### Post by pehden on 2012-04-03
Email error, 


MAILER-DAEMON
(temporary failure. Command output: ERR: authdaemon: s_connect() failed: Permission denied sh: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory sh: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory sh: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory /usr/bin/maildrop: Unable to create a dot-lock at /var/vmail/

---

### Post by pehden on 2012-04-03
BUMP


Also found 

/bin/bash: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory

So I'm guessing there related.


Based on this 
[http://www.linuxquestions.org/questions/linux-general-1/error-while-loading-shared-libraries-libncurses-so-5-a-840057/](http://www.linuxquestions.org/questions/linux-general-1/error-while-loading-shared-libraries-libncurses-so-5-a-840057/)

It says something about 

> 

i installed glibc with "--prefix=target/usr" instead of "--prefix=/usr" and "make install_root=target install".
according to strace bash searches libncurses.so.5 at the directory i installed glibc wich is a different
i'll try to recompile glibc and see what happens
You can just copy libnurses to where bash looks for it and be done,
without need to recompile lib



I have check the locations and they match, so i guess theres something else?

---

### Post by pehden on 2012-04-08
Bump

---

### Post by roelforg on 2012-04-08
Boot in a live cd,
Try to locate the libncurses so file on the hd
if it ain't there, you could try to copy it from the live cd to /lib and then reboot to the hd, should work enough to get apt-get to reinstall it.

---

### Post by pehden on 2012-04-08
> **roelforg said:**
> Boot in a live cd,
Try to locate the libncurses so file on the hd
if it ain't there, you could try to copy it from the live cd to /lib and then reboot to the hd, should work enough to get apt-get to reinstall it.

I am running 64bit... will the live cd be running it.

---

