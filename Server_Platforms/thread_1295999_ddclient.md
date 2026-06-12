---
title: "ddclient"
date: 2009-10-20
forum: Server Platforms
---

### Post by any.linux12 on 2009-10-20
Hi!

I have an email server and the dns is given by dyndns.com. My modem changes the ip address everyday (sometimes 2x), so I decided to install ddclient. The configuration was fine the thing is that it's sending the ip from my server and not the ip of my modem. Basically is sending the ip 192.168.1.3 which is my server (where I installed the ddclient software) and I want it to send the ip gateway from my modem (ip 192.168.1.1).

Is there any way to do that? or for example any command to receive the ip address on my machine?

thanks

---

### Post by crazyasyou on 2009-10-20
My config works, change the below and see how it goes, the check web bit uses your extrernal IP

root@server-lin-01:~# cat /etc/ddclient.conf
# Basic configuration file for ddclient
#
# /etc/ddclient.conf

daemon=600
cache=/tmp/ddclient.cache
pid=/var/run/ddclient.pid
ssl=yes
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
login=YOURDYNDNSUSERNAMEHERE
password=YOURPASSWORDHERE
protocol=dyndns2
server=members.dyndns.org
wildcard=no
SOMEDOMAINHERE.gotdns.com
custom=yes, SOMEDOMAINHERE.gotdns.com

---

### Post by any.linux12 on 2009-10-20
> **crazyasyou said:**
> My config works, change the below and see how it goes, the check web bit uses your extrernal IP

root@server-lin-01:~# cat /etc/ddclient.conf
# Basic configuration file for ddclient
#
# /etc/ddclient.conf

daemon=600
cache=/tmp/ddclient.cache
pid=/var/run/ddclient.pid
ssl=yes
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
login=YOURDYNDNSUSERNAMEHERE
password=YOURPASSWORDHERE
protocol=dyndns2
server=members.dyndns.org
wildcard=no
SOMEDOMAINHERE.gotdns.com
custom=yes, SOMEDOMAINHERE.gotdns.com

cool dude thanks a lot. Before me use was if="eth1"

---

