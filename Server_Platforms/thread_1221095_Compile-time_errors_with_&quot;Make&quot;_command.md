---
title: "Compile-time errors with &quot;Make&quot; command"
date: 2009-07-23
forum: Server Platforms
---

### Post by mixtri on 2009-07-23
Hey guys. Please Help!

I am trying to build some source files to get my wifi dongle to work on ubuntu 9.04 server.
I have installed build essential and kernel specific header files.
I get the following error after using the make command. 

I have executed the 'Make' command on another file and got the same error message. 
Any help would be greatly appreciated.****

albert@mixtri:~/2008_0528_RT2870_Linux_STA_v1.3.0.0$ sudo make
[sudo] password for albert: 
make -C tools
make[1]: Entering directory `/home/albert/2008_0528_RT2870_Linux_STA_v1.3.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/albert/2008_0528_RT2870_Linux_STA_v1.3.0.0/tools'
/home/albert/2008_0528_RT2870_Linux_STA_v1.3.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/albert/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.28-11-server/build SUBDIRS=/home/albert/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux modules
make: *** /lib/modules/2.6.28-11-server/build: No such file or directory. Stop.
make: *** [LINUX] Error 2
albert@mixtri:~/2008_0528_RT2870_Linux_STA_v1.3.0.0$

---

### Post by lensman3 on 2009-07-23
This library is missing:

"/lib/modules/2.6.28-11-server/build"

Make sure you have the kernel headers installed.  By default it is not installed (I think).  

Try a "make -i".  The -i tells make to ignore all errors and keep going.  The program(s) won't build, but you will see all the errors.

I hope this helps.

---

