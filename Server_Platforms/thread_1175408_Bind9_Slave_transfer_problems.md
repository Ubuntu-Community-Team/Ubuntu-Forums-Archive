---
title: "Bind9 Slave transfer problems"
date: 2009-06-01
forum: Server Platforms
---

### Post by drhiii on 2009-06-01
For a couple of years, bind was transferring happily to a slave DNS server, no prob.  Performed an upgrade and it broke.  Have searched extensively and am not getting the issue solved.  Am hoping someone will be able to crack this issue as am essentially into a face melt... 

Running Linux tpl3 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009 x86_64 GNU/Linux.  Bind 9.5.1 on both primary and secondary servers.

Error I cannot overcome from /var/log/syslog:

Jun  1 03:40:14 tpl3 named[18615]: transfer of 'xxx.yyyzzz.com/IN' from 11.22.33.22#53: failed while receiving responses: REFUSED

Have disabled firewalls just in case, tho 53 on TCP and UDP is open.  I edited apparmor to allow writing to /etc/bind.  Changed permissions all over the place, eventually even trying chmod 777 (I know, bad idea but just to see if that was where the prob resided, no go).  

Have enabled and disabled as much as I understand, DNSSEC, RNDC, and everything else I saw or could think of...

I can post the .conf files on both primary and slave, but before doing so, wanted to see if someone would respond and offer to help.  Am basically brain numb trying to solve what had been working for a couple of years, until this upgrade.

Am stumped, and really appealing to the community for help...

tx

---

