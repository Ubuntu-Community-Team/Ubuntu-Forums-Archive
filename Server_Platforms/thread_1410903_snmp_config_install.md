---
title: "snmp config install"
date: 2010-02-19
forum: Server Platforms
---

### Post by Walter-Bishop on 2010-02-19
HI all I am new to the Ubuntu world, is a little different that RedHat or Fedora Core. Hope this is the correct place to place this type of question.

I am trying to setup snmp on Ubuntu 9.1 servers.  Looks like I managed to get the software installed via apt-get install snmp.  My problem is that I am unable to find the config file. did find some stuff under /usr/shrare/snmp.  A find from root does not locate the snmpd dameon either.


Any help or suggestions would be deeply appreciated.:P

---

### Post by heidfirst on 2010-02-19
To get the snmpd daemon you need to install snmpd.

sudo apt-get install snmpd

Not sure which config file you are looking for, sorry

---

### Post by Walter-Bishop on 2010-02-19
thank you very much I will do that.

---

