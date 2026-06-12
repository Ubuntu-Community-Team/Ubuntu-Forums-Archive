---
title: "Unable to install VMWare Server 2 in ubuntu 9.04 (desktop)"
date: 2009-10-16
forum: Virtualisation
---

### Post by prashantsays on 2009-10-16
Hi All,

My first post in this community.

My machine details:
Intel Pentium Core2Duo 2.66 GHz
DDR 2 RAM 4 GB
80 GB HDD
OS: Windows 7
OS: ubuntu 9.04 desktop (kernel 2.6)
________________________________________________________________________________________

My system is dual boot between Windows 7 & ubuntu. I downloaded VMWare Server 2 for Linux (& extracted). I follow the article ([COLOR=Blue]http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-9.04[/COLOR]) to install VMWare Server.
Successfully executed: [COLOR=Blue][I]sudo aptitude install linux-headers-`uname -r` build-essential xinetd

[/I][COLOR=Black]But when I execute: [COLOR=Blue]*sudo ./vmware-install.pl* [COLOR=Black], nothing happens. My screen (terminal) just goes to # prompt & nothing happens :(

I tried searching internet, but no use.

Please help, I'm trying to migrate from Windows to ubuntu/linux permanently. I need to install VMWare Server & create/migrate virtual machines...

Regards,
PS
[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by prashantsays on 2009-10-17
Friends, Please help me!! ](*,)

---

### Post by prashantsays on 2009-10-17
[COLOR=Blue]:razz: I got the solution!!! Actually I extracted the VMWare Server 2.0 tar.gz file in Windows itself which might have done something (I don't know what) to the archive.
I dowloaded again & extracted using ubuntu only, worked like charm...

So anyone who has same issue, try downloading the archive once again & extract in ubuntu only...
[/COLOR]

---

