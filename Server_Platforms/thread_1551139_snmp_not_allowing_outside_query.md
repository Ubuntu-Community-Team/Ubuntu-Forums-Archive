---
title: "snmp not allowing outside query"
date: 2010-08-11
forum: Server Platforms
---

### Post by xkaliburx on 2010-08-11
Not sure if I'm tired, shot, or just missing something obvious, but our 9.x servers are running perfect.  Just setup 5 new webservers, running 10.04LTS.  Have SNMPD running, installed and the same config for all the servers I just copied over, by config, I mean one line, that's it.  So the servers have the following /etc/snmp/snmpd.conf file
rocommunity public

That's it.  Now the only difference is looking at the ps on the local box's, a working one shows;

snmp      1096  0.0  0.0  50480  3756 ?        S    Jul02   9:21 /usr/sbin/snmpd -Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid

where this one shows
snmp      4962  0.3  0.0  48540  5884 ?        S    22:26   0:04 /usr/sbin/snmpd -Lsd -Lf /dev/null -u snmp -g snmp -I -smux -p /var/run/snmpd.pid [COLOR="Red"]127.0.0.1[/COLOR]

Notice (I did flag it red) the local 127.0.0.1, but that co-incides with my issue.  A local command of;
snmpwalk -cpublic -v1 127.0.0.1 reveals the data, where the zenoss monitoring server when tested shows;
snmpwalk -cpublic -v1 192.168.2.151
Timeout: No Response from 192.168.2.151

It almost seems something firewall is blocking, apparmor is not running, is there something else out of the box 10.04 has that I am just completly brain farting on?

Thanks

---

### Post by xkaliburx on 2010-08-12
finally found it.  In the /etc/default/snmp there is this line;

SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 127.0.0.1'

Simply remove the ip replacing it with nothing, or 0.0.0.0 restart and your done!

---

