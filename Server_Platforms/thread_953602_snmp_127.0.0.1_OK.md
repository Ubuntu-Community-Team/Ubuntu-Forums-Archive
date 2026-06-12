---
title: "snmp 127.0.0.1 OK"
date: 2008-10-20
forum: Server Platforms
---

### Post by mlum on 2008-10-20
Hi,
I've installed snmpd on to 8.04. When I do a snmpget and use 127.0.0.1 as the target I get results for the queries. e.g:

#snmpget -v2c -c public 127.0.0.1 system.sysDescr.0

gives me:

#SNMPv2-MIB::sysDescr.0 = STRING: Linux nfs4svr 2.6.24-19-server #1 SMP Wed Jun 18 15:18:00 UTC 2008 i686


However, if I try and query from a remote machine i get a Timeout: no response error.

There is no firewall being used and I used 'snmpconf -g basic_setup' to create /etc/snmp/snmpd.conf. I have amended the line:

rocommunity  public

to: 

rocommunity  public IPaddress

rocommunity  public subnet
 
etc... But nothing seems to work.

I realise I should perhaps contact net-snmp forums but I thought I check out here first to see if anyone has seen this before.

mlum

---

### Post by gombadi on 2008-10-20
I think that snmpd listens on localhost only by default.

Have a look on a terminal with this command to see what snmpd is listening on -

```

sudo netstat -plntu

```

I don't have a machine running snmpd handy, but I think you will have to look in /etc/default/snmpd to change the settings.

---

### Post by mlum on 2008-10-21
Thanks gombadi,

I changed this line in /etc/snmp/snmpd.conf

SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 127.0.0.1'

to

SNMPDOPTS='-Lsd -Lf /dev/null -p /var/run/snmpd.pid'

and rebooted and I can connect to the server from the SNMP management station. Perhaps not the most secure config but this is readonly so it will suffice for the moment.

Many thanks gombadi!!!

mlum

---

### Post by mlum on 2008-10-21
oops. I changed the line to:

SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid'

Not sure where I got that previous line form :)

---

### Post by mlum on 2008-10-21
I changed the lines in this file NOT snmpd.conf. 

/etc/default/snmpd

I am going to bed now.

:confused:

---

