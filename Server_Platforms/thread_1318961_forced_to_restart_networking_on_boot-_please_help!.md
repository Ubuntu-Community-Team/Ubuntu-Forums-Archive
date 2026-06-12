---
title: "forced to restart networking on boot- please help!"
date: 2009-11-08
forum: Server Platforms
---

### Post by kylegio on 2009-11-08
ive been beating my head on a wall for a few days now, can someone please help im sure SOMEONE has a useful suggestion. ubuntu 9.10, was working great before upgrade. now upon boot i MUST run either 

sudo service networking restart

or 

sudo /etc/init.d/networking restart

if i do not re-start networking then i have no networking. 

ifconfig before doing a networking restart is blank, afterwards it is normal. 
this is causing havoc on my system because 
1) i must have a keyboard and monitor attached to my server, and have direct access to it at all times because if it gets restarted for any reason then i can not ssh into it (no networking = no ssh access)
2) other services have to be restarted afterwards (like apache2)



something i have noticed which is also new and might be related is apache takes about 5+mins to restart, as well as to shut down. so a shutdown command sits at stopping apache for about 5 mins before the computer will shutdown, an apache restart command sits for about 5 mins before restarting. it used to be about 2 seconds tops


im certain someone has a suggestion please help, i cant afford to wipe and fresh install my entire server, and its useless to me if i have to babysit it all the time. 

any help greatly appreciated.

---

### Post by ian dobson on 2009-11-08
Hi,

Why not just add "/etc/init.d/networking restart" to the /etc/rc.local file.

It's not a solution for your problem but it's a work around.

Regards
Ian Dobson

---

