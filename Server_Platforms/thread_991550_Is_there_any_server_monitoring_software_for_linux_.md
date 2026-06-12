---
title: "Is there any server monitoring software for linux that monitors windows svrs?"
date: 2008-11-23
forum: Server Platforms
---

### Post by Linuxwho? on 2008-11-23
Just like the title.  For example, I would like software that I can install on my linux (ubuntu desktop/server) to monitor my windows boxes for disk thresholds and cpu or memory spikes and alerts me via email.  Is there anything out there in freeware land that does this?  Thanks!

---

### Post by carbm1 on 2008-11-23
I like to use Cacti.  There is a distro called CactiEZ that I run in a VM to monitor all my network equipment and servers via SNMP.  You have to install SNMP and configure it on your Windows servers.  I currently only monitor disk space.

Google CactiEZ.

---

### Post by cariboo on 2008-11-23
THere also is NetworkAuthority Inventory  by Alterpoint, check thier web site here

[http://inventory.alterpoint.com/](http://inventory.alterpoint.com/)

Jim

---

### Post by Linuxwho? on 2008-11-23
Thanks guys!

---

### Post by CrucifiedEgo on 2008-11-23
I'm late to the party here, but I use nagios (with nsclient++ installed on the server side) to monitor about 50 windows servers.  It does the job quite well.

---

### Post by gtdaqua on 2008-11-24
[Zenoss]("http://www.zenoss.com") is an open-source, enterprise-grade Network Management System with clientless monitoring of both Linux and Windows machines. With each new release, this product is definitely getting better.

---

### Post by Linuxwho? on 2008-11-25
Thanks but I was asking for freeware.  This is freeware?

---

### Post by carbm1 on 2008-11-25
All mentioned above I believe are free or have a community version.

Zennoss has a community version on their download page... "Recommended for do-it-yourselfers who are comfortable deploying, extending & supporting enterprise software without professional support."

[http://www.zenoss.com/community/]("http://www.zenoss.com/community/")

---

### Post by HermanAB on 2008-11-25
Zabbix is probably the easiest of the lot to configure and get to work:
[http://www.zabbix.com/](http://www.zabbix.com/)

Cheers,

H.

---

