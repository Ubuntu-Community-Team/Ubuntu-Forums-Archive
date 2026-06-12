---
title: "Printer driver has messed up the OS and couldn't update other package"
date: 2016-03-18
forum: Ubuntu, Linux and OS Chat
---

### Post by Grey08 on 2016-03-18
Hello everyone

I have recently tried to install Brother's printer, model MFC260C and unfortunately i wasn't able to install the driver and the worst thing is, whenever i tried to update/install package, the following error messages appears:

```
Installing package(s) with command apt-get -y install libpam-modules ..
Reading package lists...
Building dependency tree...
Reading state information...
E: The package mfc260clpr:i386 needs to be reinstalled, but I can't find an archive for it.
.. install failed!
```

I have googled as well as search all the posts in the forum, still couldn't installed nor solved the problem, please help!

p/s: It is an ubuntu 15.10 server without GUI hosting web pages.
I wanted to install cups (the purpose is to let all my family members so printing through their smart phones)

Thanks in advance

---

### Post by grahammechanical on 2016-03-18
As the message says it is trying to re-install the printer driver and it is doing that because it has a record that the printer driver is a package on the system. May be if you removed/purged the printer driver this problem would go away. May be?

Another idea, and this is all ideas on my part, would be to put the printer driver onto a CD and then put the CD as a repository. So, that when there is a need to re-install the printer driver the system looks to the CD as a repository for the driver.

Regards.

---

### Post by Grey08 on 2016-03-20
Thanks for reply 

I have tried the following:
```
grey08@Server:~$ sudo apt-get purge mfc260c*                               
[sudo] password for grey08:                                                     
Reading package lists... Done                                                   
Building dependency tree                                                        
Reading state information... Done                                               
E: The package mfc260clpr:i386 needs to be reinstalled, but I can't find an arch
ive for it.                                                                     
grey08@Server:~$
```

This means that even i wanted to remove/purge the drivers and it seems like a mission impossible for me.

Is there any methods to remove the driver?

---

### Post by ian-weisser on 2016-03-20
One solution is to follow the instruction of the package manager: Re-download and re-install the package from wherever you originally got it from. Then it can be safely and easily removed.

Another solution is to remove the package using --force options detailed in the dpkg manpage.

---

### Post by Grey08 on 2016-03-22
Thanks for your idea, I downloaded the driver again and tried to reinstall, how the following error codes appeared:

```
grey08@Server:/home/FTP-shared/upload$ sudo dpkg -i --force-all mfc260clpr-1.0.1-1.i386.deb
Selecting previously unselected package mfc260clpr:i386.
(Reading database ... 172113 files and directories currently installed.)
Preparing to unpack mfc260clpr-1.0.1-1.i386.deb ...
Unpacking mfc260clpr:i386 (1.0.1-1) over (1.0.1-1) ...
dpkg: warning: subprocess old post-removal script returned error exit status 5
dpkg: trying script from the new package instead ...
dpkg: error processing archive mfc260clpr-1.0.1-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 5
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 5
Errors were encountered while processing:
 mfc260clpr-1.0.1-1.i386.deb
grey08@Server:/home/FTP-shared/upload$

```

what does it mean by error exit status 5?

---

### Post by Grey08 on 2016-03-23
Anyone?

Help please?

---

### Post by ian-weisser on 2016-03-23
Error 5 has no standard meaning - it's a code emitted by the post-removal script.
Look at the script to find out what error 5 means.

Look for the script in less /var/lib/dpkg/info/
It will be something like /var/lib/dpkg/info/mfc260clpr.postrm

---

### Post by Grey08 on 2016-03-25
Thanks for your reply, Ian-Weisser

in the /info there are:

mfc260clpr.conffiles
mfc260clpr.list
mfc260clpr.md5sums
mfc260clpr.postinst
mfc260clpr.postrm
mfc260clpr.prerm

the file mfc260clpr.postrm is as follow:

```
#!/bin/sh
# ESP Package Manager v4.0
if [ -e /etc/init.d/lprng ]; then
/etc/init.d/lprng restart
elif [ -e /etc/init.d/lpd ]; then
/etc/init.d/lpd restart
fi



```

Does it have anything to do with the re-installation of the driver?

---

### Post by Grey08 on 2016-03-27
Anyone help please?

---

### Post by Grey08 on 2016-03-28
I have tried force uninstall, but still the same.

Reinstall and force remove were not able to fix the problem, how can the problem to be solved??


```
grey08@Server$ sudo dpkg --remove --force-remove-reinstreq mfc260clpr:i386
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
(Reading database ... 172116 files and directories currently installed.)
Removing mfc260clpr:i386 (1.0.1-1) ...
dpkg: error processing package mfc260clpr:i386 (--remove):
 subprocess installed post-removal script returned error exit status 5
Errors were encountered while processing:
 mfc260clpr:i386
grey08@Server$ 
```

purge command
```
grey08@Server$ sudo dpkg --purge mfc260clpr:i386
dpkg: error processing package mfc260clpr:i386 (--purge):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
Errors were encountered while processing:
 mfc260clpr:i386
grey08@Server$ 
```

---

