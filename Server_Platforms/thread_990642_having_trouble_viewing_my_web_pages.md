---
title: "having trouble viewing my web pages"
date: 2008-11-22
forum: Server Platforms
---

### Post by meomike2000 on 2008-11-22
i am having trouble viewing my web pages from outside of my network.

here is my setup. i have setup two servers. on one i have set up a lamp, ubuntu 8.04, (will call this one s1 )the other is ubuntu 8.04 also but it only has dns (bind9) installed (will call this one dns ). the dns setup of both servers make (s1) the master for my domain and (dns) the slave. (dns) has 2 eth ports one configed with static ip from isp (eth1) and the other for my internal network (eth0), also configed static (192.168.x.x). i followed the how-to from this forum ( [http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874) ) on how to set up the connection sharing. here is a copy of my /etc/rc.local file:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sysctl -w net.ipv4.ip_forward=1
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth1 -j MASQUERADE
#/sbin/iptables --table nat -A POSTROUTING -j MASQUERADE

exit 0

i am registered with godaddy and i have set up the hosts there and set up the nameservers there to point to my server. i can ping my nameservers by name or ip and get response from both nameservers. i can view my web page, ftp, mail etc... from a client on the internal network just fine. but not from the internet, i can only ping the nameservers. 

this is my first setup. it works perfect on my internal client, 
also this client and both servers can reach the internet just fine.

any help with this would be greatly appreciated.
tia..... mike

---

### Post by meomike2000 on 2008-11-26
solved.....

---

### Post by CrucifiedEgo on 2008-11-26
For posterity's sake, how?

---

