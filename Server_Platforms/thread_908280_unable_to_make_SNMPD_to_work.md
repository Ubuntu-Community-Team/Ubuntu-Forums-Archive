---
title: "unable to make SNMPD to work"
date: 2008-09-02
forum: Server Platforms
---

### Post by kosc on 2008-09-02
Hi

I need some linux guru to help me here :)

I have Ubuntu server LTS 8.04 and I have installed snmpd without problem but I'm unable to read any data from it.

here is what is installed:
sudo apt-show-versions | grep snmp

[COLOR="DarkRed"]libsnmp-session-perl/hardy uptodate 1.11-1
snmpd/hardy uptodate 5.4.1~dfsg-4ubuntu4
libsnmp15/hardy uptodate 5.4.1~dfsg-4ubuntu4
libsnmp-base/hardy uptodate 5.4.1~dfsg-4ubuntu4
snmp/hardy uptodate 5.4.1~dfsg-4ubuntu4[/COLOR]

I tried 2 snmpd.conf files first(default) was:
[COLOR="DarkRed"]com2sec readonly   default         public 
view all included  .1              80
view system included  .iso.org.dod.internet.mgmt.mib-2.system
[/COLOR]
and second:

[COLOR="DarkRed"]rocommunity  public
rwcommunity  public 
[/COLOR]

after /etc/init.d/snmpd restart here is what is in syslog:
[COLOR="Navy"]Sep  2 16:48:24 collin snmpd[16051]: Received TERM or STOP signal...  shutting down... 
Sep  2 16:48:26 collin snmpd[16457]: netsnmp_assert !"registration != duplicate" failed agent_registry.c:535 netsnmp_subtree_load() 
Sep  2 16:48:26 collin last message repeated 2 times
Sep  2 16:48:26 collin snmpd[16457]: NET-SNMP version 5.4.1 
[/COLOR]

and snmpwalk is dead, no response
(snmpwalk -v 1 localhost -c public)
[COLOR="DarkRed"]Timeout: No Response from 127.0.0.1[/COLOR]

UDP port is open
nmap -sU 
Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-09-02 16:55 CEST
Interesting ports on cod4master.activision.com (127.0.0.1):
Not shown: 1485 closed ports
PORT    STATE         SERVICE
161/udp open|filtered snmp


Don't know what to try next
I found that error from syslog is fixed in new version of snmpd but 5.4.1 is newest.

---

### Post by koenn on 2008-09-02
verify that snmpd is running
```

sudo -i
ps -e |grep snmp
exit
```

try your snmpwalk without the -v1 (unless you're absolutely sure you've setup snmpd to do SNMPv1)

---

### Post by kosc on 2008-09-03
> **koenn said:**
> verify that snmpd is running
```

sudo -i
ps -e |grep snmp
exit
```

try your snmpwalk without the -v1 (unless you're absolutely sure you've setup snmpd to do SNMPv1)


here what code produced:
[COLOR="DarkRed"]16457 ?        00:00:06 snmpd
[/COLOR]

You are right, snmpwalk -v 2c localhost -c public
shows lots of data.

my snmpd.conf look like this:
[COLOR="DarkRed"]# rocommunity: a SNMPv1/SNMPv2c read-only access community name
#   arguments:  community [default|hostname|network/bits] [oid]
rocommunity  public

# rwcommunity: a SNMPv1/SNMPv2c read-write access community name
#   arguments:  community [default|hostname|network/bits] [oid]
rwcommunity  public
[/COLOR]

what I need to put in snmpd.conf to work with "v 1" ?

---

### Post by koenn on 2008-09-03
> **kosc said:**
> 

what I need to put in snmpd.conf to work with "v 1" ?

Don't know if you can.
I don't have that much experience with snmp, but judging from the man files, it looks plausible that snmpd runs at a specific version, and you use the -v switch to modify the behaviour of the client (like snmpwalk),  to make it compatible with the daemon. But I could be wrong.

Any particular reason you want v1 ?

man 5 snmpf.conf says you can specify version with the 'trap' keyword, but that might be only when you want snmpd to trap events and notify a client, not when a client queries the daemon. Again, not sure. 

You *should* change the community names. 
You've seen how much information about your system a simple query reveils. querying a specific MIB reveils often even more (such as installed software versions, user account names, network and routing info, ... ),  all sorts of stuff you don't want anyone who happens to know the default community names to find out.

---

### Post by kosc on 2008-09-04
> **koenn said:**
> Don't know if you can.
I don't have that much experience with snmp, but judging from the man files, it looks plausible that snmpd runs at a specific version, and you use the -v switch to modify the behaviour of the client (like snmpwalk),  to make it compatible with the daemon. But I could be wrong.

Reason for this post was to setup MRTG to draw ethernet traffic from my servers

I have 2 Linux boxes
first is called ubuntu(LTS 8.4 server version) and have IP 192.168.2.4 (and snmpd)
second is called MRTG(LTS 8.4 server version) and have IP 192.168.2.5

I have problem setting up SNMPd on my ubuntu server(192.168.2.4), that MRTG(192.168.2.5) can read ethernet data from it and draw bandwidth usage.

currentrly I was able to read data from localhost on v1 and v2c ubuntu(192.168.2.4)
[COLOR="DarkRed"]snmpwalk -v 2c -c public localhost
snmpwalk -v 1 -c public localhost[/COLOR]
but was unable to read SNMP data from MRTG(192.168.2.5) to ubuntu(192.168.2.4)

This command from MRTG(192.168.2.5) didn't give me any result
[COLOR="DarkRed"]snmpwalk -v 2c -c public 192.168.2.4
snmpwalk -v 1 -c public 192.168.2.4[/COLOR]


snmpd.conf on ubuntu(192.168.2.4) looks like this:
[COLOR="DarkRed"]rocommunity  public default[/COLOR]

but I even try this:
[COLOR="DarkRed"]rocommunity  public 192.168.2.0/24
rocommunity  public[/COLOR]

also if snmpwalk is started from ubuntu with IP address (instead of localhost) nothing happens.
[COLOR="DarkRed"]snmpwalk -v 2c -c public 192.168.2.4
snmpwalk -v 1 -c public 192.168.2.4[/COLOR]



> **koenn said:**
> 
Any particular reason you want v1 ?

man 5 snmpf.conf says you can specify version with the 'trap' keyword, but that might be only when you want snmpd to trap events and notify a client, not when a client queries the daemon. Again, not sure. 

You *should* change the community names. 
You've seen how much information about your system a simple query reveils. querying a specific MIB reveils often even more (such as installed software versions, user account names, network and routing info, ... ),  all sorts of stuff you don't want anyone who happens to know the default community names to find out.

security in not proglem now, since computer are behing firewall & NAT, but I'll change public to something else when everything works :)

---

### Post by kosc on 2008-09-04
Problem is solved!

here is solution.
There is file [COLOR="DarkRed"]/etc/default/snmpd[/COLOR]

in it there is line
[COLOR="DarkRed"]SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 127.0.0.1'[/COLOR]

it should be like this:
[COLOR="DarkRed"]SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid'[/COLOR]

this default settings forbid reading SNMP data from other IP then localhost

**koenn** thanks for help :)

---

