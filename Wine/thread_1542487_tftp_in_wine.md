---
title: "tftp in wine"
date: 2010-07-30
forum: Wine
---

### Post by kfleten on 2010-07-30
I'm trying to install a Windows program with a tftp server in wine, and the installation fails because it says port 69 is in use - wich it is actually not if I ask netstat and lsof. 

It seems like the same problem as this:
[http://ubuntuforums.org/showthread.php?t=454848](http://ubuntuforums.org/showthread.php?t=454848)
How can I solve this ? Or is there a limitation in Wine ?

---

### Post by asdfoo on 2010-07-30
> **kfleten said:**
> I'm trying to install a Windows program with a tftp server in wine, and the installation fails because it says port 69 is in use - wich it is actually not if I ask netstat and lsof. 

It seems like the same problem as this:
[http://ubuntuforums.org/showthread.php?t=454848](http://ubuntuforums.org/showthread.php?t=454848)
How can I solve this ? Or is there a limitation in Wine ?

Ports less than 1024 are privileged, only special users can bind to them because core operating system services typically use them.

Either configure it to use a different port or go find out how to use linux capabilities to give this process the correct permissions to use port 69.  It's no different to a linux program that would want to use this port.

---

### Post by kfleten on 2010-07-31
> **asdfoo said:**
> Ports less than 1024 are privileged, only special users can bind to them because core operating system services typically use them.
Either configure it to use a different port or go find out how to use linux capabilities to give this process the correct permissions to use port 69.

Thanks ! That seems to bring me in the right direction.
I have just tried:
sudo setcap cap_net_bind_service=69 wine

but obviously I've got the syntax wrong; I get the error 
"Note <filename> must be a regular (non-symlink) file."

---

### Post by asdfoo on 2010-07-31
> **kfleten said:**
> Thanks ! That seems to bring me in the right direction.
I have just tried:
sudo setcap cap_net_bind_service=69 wine

but obviously I've got the syntax wrong; I get the error 
"Note <filename> must be a regular (non-symlink) file."

wine is a shell script, there is a wine-preloader binary, but that loads and executes your program executable which may require the cap setting, not the preloader.

---

### Post by kfleten on 2010-07-31
Of course:wink:

So, I tried to apply the command on the file itselves:
sudo setcap cap_net_bind_service=69 WCS.exe

Unfortunately still:
"Note <filename> must be a regular (non-symlink) file."

---

