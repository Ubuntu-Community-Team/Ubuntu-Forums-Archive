---
title: "Problem with DansGuardian"
date: 2009-02-26
forum: Server Platforms
---

### Post by namwons on 2009-02-26
Server is 8.04.2 upgraded from 7.10 which was running DG just fine. 

Now when I try to start DG it get the following error. 

root@elroy:~# /etc/init.d/dansguardian restart
Restarting DansGuardian:  * Restarting DansGuardian: 
Config problem; check allowed values for maxcontentfilecachescansize
Error parsing the dansguardian.conf file or other DansGuardian configuration files
   ...fail!



It is running Dansguardian 2.9.9.7-2~hardy1   

Found one post that they "fixed" this in 8.10. I really do not want to upgrade. Anyone have any idea? 

Thanks.

---

### Post by brian_p on 2009-02-26
> **namwons said:**
>   

Found one post that they "fixed" this in 8.10. I really do not want to upgrade. Anyone have any idea? 

Thanks.

Comment out the maxcontentfilecachescansize line?

Upgrade dansguardian from hardy-backports?

---

### Post by namwons on 2009-02-26
The line is not there. I added it and it did not help. I have backports enable and have reinstalled it multiple times. 


aptitude reinstall dansgaurdian
aptitude remove --purge dansguardian && aptitude install dansguardian. 


All to no success



So I deleted all references to dansguardian in /var/lib/dpkg/info and reinstalled..... all is good. I am guessing aptitude autoclean is not doing all it can.

---

