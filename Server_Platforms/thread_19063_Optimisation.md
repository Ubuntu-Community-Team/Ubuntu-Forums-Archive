---
title: "Optimisation"
date: 2005-03-10
forum: Server Platforms
---

### Post by TekZonz on 2005-03-10
Hello,

I have a ubuntu server running on my local network. I have a "custom" install as in I type custom at the install prompt.

As I have not much memory, I would like to optimise my server so it uses less CPU and less RAM. The only thing I will be using it for is Counter-Strike/Steam Servers.

What can i remove safely? and how?

Thank you in advance,

Antoine "TekZone" Benkemoun

---

### Post by MadsDK on 2005-03-10
The ubuntu base system is really quite clean in that it does not start very many services that you do not need.

Do a 'ps fax' and check to see that you really need the (quite few) services that are running there. If you do not know what the different services do try to run "man servicename" to read about them. 

Thing that you can probably live without are mdadm and postfix.

You could also turn off all logging (syslogd) and the cron daemons (cron and atd)...

 - Mads

---

### Post by TekZonz on 2005-03-10
Thank you for your help I'll look into it :mrgreen:

---

