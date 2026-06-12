---
title: "SNMP problems on Ubuntu 8.04 Hardy"
date: 2008-07-18
forum: Server Platforms
---

### Post by jenga2012000 on 2008-07-18
Hello,

I'm having a problem with using a udc/net SNMP host template on my new ubuntu 8.04 hardy box. I have cacti and snmp setup on an ubuntu 7.10 server and it is getting data from two other ubuntu 7.10 servers...everything is fine up until this point.

I tried to setup SNMP on the new 8.04 server, but the only graphs the 7.10 server creates shows only 0kB for traffic. example:

[http://chi.nibl.co.uk/cacti/graph_image.php?action=view&local_graph_id=19&rra_id=1](http://chi.nibl.co.uk/cacti/graph_image.php?action=view&local_graph_id=19&rra_id=1)

My configuration for snmp on the new 8.04 server is in '/etc/snmp/snmpd.conf' i have 'rocommunity public'
and in '/etc/default/snmpd' i have 'SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid''

I have this exact same configuration on the 7.10 server, which is working fine.

If i debug the graph, i don't see any errors...it's almost like the snmp queries aren't pulling any data from the remote 8.04 machine.
```


RRDTool Command:

/usr/bin/rrdtool graph - \
--imgformat=PNG \
--start=-86400 \
--end=-300 \
--title="nibl.co.uk - Traffic - eth0" \
--rigid \
--base=1000 \
--height=120 \
--width=500 \
--alt-autoscale-max \
--lower-limit=0 \
--vertical-label="bits per second" \
--slope-mode \
--font TITLE:12: \
--font AXIS:8: \
--font LEGEND:10: \
--font UNIT:8: \
DEF:a="/var/lib/cacti/rra/nibl_co_uk_traffic_in_14.rrd":traffic_in:AVERAGE \
DEF:b="/var/lib/cacti/rra/nibl_co_uk_traffic_in_14.rrd":traffic_in:MAX \
DEF:c="/var/lib/cacti/rra/nibl_co_uk_traffic_in_14.rrd":traffic_out:AVERAGE \
DEF:d="/var/lib/cacti/rra/nibl_co_uk_traffic_in_14.rrd":traffic_out:MAX \
CDEF:cdefa=a,8,* \
CDEF:cdefd=b,8,* \
CDEF:cdeff=c,8,* \
CDEF:cdefi=d,8,* \
AREA:cdefa#00CF00FF:"Inbound"  \
GPRINT:cdefa:LAST:" Current\:%8.2lf %s"  \
GPRINT:cdefa:AVERAGE:"Average\:%8.2lf %s"  \
GPRINT:cdefd:MAX:"Maximum\:%8.2lf %s"  \
COMMENT:"Total In\:  0 bytes\n"  \
LINE1:cdeff#002A97FF:"Outbound"  \
GPRINT:cdeff:LAST:"Current\:%8.2lf %s"  \
GPRINT:cdeff:AVERAGE:"Average\:%8.2lf %s"  \
GPRINT:cdefi:MAX:"Maximum\:%8.2lf %s"  \
COMMENT:"Total Out\: 0 bytes"

RRDTool Says:

OK
```


Does anybody have any ideas on how i can find the problem on my problematic ubuntu 8.04 machine?

Thank you

---

### Post by jenga2012000 on 2008-07-18
also, i just tried to snmpwalk what i think is the out bytes for my interface.

snmpwalk -Os -c public -v 1 localhost .1.3.6.1.2.1.2.2.1.16

returned:
ifOutOctets.1 = Counter32: 2518374344
ifOutOctets.2 = Counter32: 2820326285
ifOutOctets.3 = Counter32: 0
ifOutOctets.4 = Counter32: 0
ifOutOctets.5 = Counter32: 0


I'm hesitant to say this is a problem with cacti, because i am able to pull data correctly with the cacti on the 8.04 server from the 7.10 server.

---

### Post by jenga2012000 on 2008-07-20
so, nobody is having problems with cacti on hardy?

---

### Post by promodus on 2008-07-20
> **jenga2012000 said:**
> also, i just tried to snmpwalk what i think is the out bytes for my interface.

snmpwalk -Os -c public -v 1 localhost .1.3.6.1.2.1.2.2.1.16

returned:
ifOutOctets.1 = Counter32: 2518374344
ifOutOctets.2 = Counter32: 2820326285
ifOutOctets.3 = Counter32: 0
ifOutOctets.4 = Counter32: 0
ifOutOctets.5 = Counter32: 0


I'm hesitant to say this is a problem with cacti, because i am able to pull data correctly with the cacti on the 8.04 server from the 7.10 server.

Yes those are the output bytes from your interface.
Similarly there will be an ifInOctets.{1,2,3,4,5...}

The two servers, are the network cards both eth0?

---

### Post by jenga2012000 on 2008-07-20
yes, the two cards show up as eth0.

cacti shows the card as
2	Up	eth0	eth0	ethernetCsmacd(6)    100000000 mac_address ip_address

---

### Post by meshugga on 2008-08-17
This might be a bit offtopic,  but since i can't reply to the archived version of the post which addressed this problem, i will post it here.

i had the problem of cacti and snmpwalk telling me something like:

```
No more variables left in this MIB View (It is past the end of the MIB tree)
```

this could be mitigated by changing the appropriate section in /etc/snmp/snmpd.conf:

```
com2sec paranoid  default         public
#com2sec readonly  default         public
#com2sec readwrite default         private

```
to
```
i#com2sec paranoid  default         public
com2sec readonly  default         public
#com2sec readwrite default         private

```

then restart snmpd...

in cacti, you need to re-add (delete+add) "SNMP interface statistics" after that change.

everything works as usual now.

---

### Post by Jenga201 on 2008-08-17
if i put in

```
com2sec readonly  default public
```

to /etc/snmp/snmpd.conf

I get the snmp error when trying to make graphs.

The only thing that works for me in the conf file is 'rocommunity public'

---

### Post by Viruk on 2008-09-29
Did you ever solve this one?

I am getting some strange results when monitoring 8.04 servers that I never saw when monitoring 6.06 servers. I wondered if there may be a bug in a package somewhere, but don't really know how to isolate where the problem might be.

---

### Post by Jenga201 on 2008-10-09
no, i never figured this problem out.  It works 100% on 6.06, but not on the 7.10 servers.

I haven't tried an 8.04 install, though.

---

### Post by Jenga201 on 2009-02-28
btw, i figured it out a while ago.

/proc/net could not be read by the snmp user, so adding the '-g root' in the /etc/default/snmpd "lsnmpdots" line <--forget what it was called.

and then chmod 750 -R /proc/net will fix it.

---

