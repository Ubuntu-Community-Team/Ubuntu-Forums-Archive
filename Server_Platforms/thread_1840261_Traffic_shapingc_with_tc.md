---
title: "Traffic shapingc with tc"
date: 2011-09-07
forum: Server Platforms
---

### Post by mark47 on 2011-09-07
Hello

I'm optimizing a mail server (postfix+cyrus) and I want to limit the maximum outbound bandwith of the port 25 only, for not saturate all the bandwith of the office.
For example, here we have 2 Mb in upload. I want to leave to the server 1 Mb max

Reading the LARTC and other articles on the web I tried some filtering with tc command and they actually work, but they do no respect my policies: if i write 10kbit the maximum speed is 6x (costant) fast!

Here there is the script I ran:

#################################################################

# path of iptables
IPTABLES=/sbin/iptables
# ethernet interface that I want to limit
nic=eth0
# Port I want to limit
port=25
# Maximum upload limit...
upload=10
# ...and relative unit
unit=kbit
# Maximum LAN speed (we have 100Mb switch so..)
maxspeed=100Mbit
# weight of the limit...
weight=1
# ...and relative unit
unit2=kbit

tc qdisc del dev $nic root && iptables -t mangle -F
$IPTABLES -t mangle -A OUTPUT -p tcp --sport $port -j MARK --set-mark 1
tc qdisc add dev $nic root handle 10: cbq bandwidth $maxspeed avpkt 1000 mpu 64
tc class add dev $nic parent 10:0 classid 10:1 cbq rate $upload$unit weight $weight$unit2 allot 1514 prio 1 avpkt 1000 bounded
tc filter add dev $nic parent 10:0 protocol ip handle 1 fw flowid 10:1
#################################################################

I tried also with the u32 filter, instead of iptables + handle fw, but with the same speed moltiplicative constant:

#################################################################
tc qdisc del dev $nic root && iptables -t mangle -F
$IPTABLES -t mangle -A OUTPUT -p tcp --sport $port -j MARK --set-mark 1
tc qdisc add dev $nic root handle 10: cbq bandwidth $maxspeedt avpkt 1000 mpu 64
tc filter add dev $nic protocol ip parent 10: prio 1 u32 match ip sport $port 0xffff flowid 10:1
#################################################################

For calculating the real speed I use the "size" value (in bytes) that I find in postfix's log, then I convert in bits and I divide fr the number of seconds between the connection and the disconnection of the mail client.

Any ideas for resolving the problem?

---

### Post by David006 on 2011-11-17
I'm researching a similar issue (with TC as a possible solution) for: **Ubuntu 11.10 (Oneiric)** and **Ubuntu 10.04.3 LTS** ..


( Will report back .. )

---

