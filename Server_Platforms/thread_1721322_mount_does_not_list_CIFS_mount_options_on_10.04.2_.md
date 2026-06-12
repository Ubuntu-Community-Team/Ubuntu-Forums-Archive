---
title: "mount does not list CIFS mount options on 10.04.2 LTS"
date: 2011-04-04
forum: Server Platforms
---

### Post by vtknightmare on 2011-04-04
-= INFO =-

Linux box info:
root@mytestbox:~# uname -a
Linux mytestbox 2.6.32-30-generic-pae #59-Ubuntu SMP Tue Mar 1 23:01:33 UTC 2011 i686 GNU/Linux

Windows box info:
Windows Server 2008 SP2 Enterprise

-= ISSUE =-

I've verified via --verbose output that mount.cifs is indeed processing the passed on options.

i.e. 

root@mytestbox:~# mount -t cifs //10.1.1.10/Test /root/testwin --verbose -o credentials=/root/testcreds,rw,nocase,noperm,noacl,nounix,noserverino,iocharset=utf8,file_mode=0777,dir_mode=0777

Domain TestWinBox


mount.cifs kernel mount options: unc=//10.1.1.10\Test,user=tstsmb,domain=TestWinBox,ver=1,rw,credentials=/root/testcreds,nocase,noperm,noacl,nounix,noserverino,iocharset=utf8,file_mode=0777,dir_mode=0777,prefixpath=IS,ip=10.1.1.10,pass=********

Yet, when I type mount all it reports is (rw,mand). The share works just fine, and I can see the masking (all files are showing as rwxrwxrwx as expected etc) but mount is not listing the options?!

Is this normal expected behavior? Is there a bug report on this? I've google'd to the best of my capabilities and could not locate any such information which is why I decided to hit the forums prior to filing a bug.

Thanks,
--VTK

---

### Post by vtknightmare on 2011-04-05
^^ BUMP ^^
:popcorn:

---

