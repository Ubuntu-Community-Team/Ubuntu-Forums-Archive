---
title: "bind automatically start problem"
date: 2014-10-28
forum: Server Platforms
---

### Post by secoonder on 2014-10-28
Hello
 i am using bind for ubuntu 12.04 GU&#304; LTS.
 when i reboot machine,bind cant automatically start.But i start to run succesfully manually.( /etc/init.d/bind9 start)
 my run level is 2
 chkconfig --list bind9
 0 : off 1 : 0ff **2 : 0n** 3 : on 4 : off 5 : 0n 6 : off 
i added /etc/init.d/bind9 start to /etc/rc.local.But it could not automatically start when i rebooted.
 how to autostart bind9 ?
 Thank you very Much for your help

---

### Post by Hugo_Serrano on 2014-10-28
Hi!

Can you try:
[COLOR=#000000]sudo update-rc.d bind9 defaults
and see if will fix it?

Cheers,
Hugo.[/COLOR]

---

### Post by secoonder on 2014-10-28
Hello
i try it
"System start/stop links for /etc/init.d/bind9 already exist"

---

