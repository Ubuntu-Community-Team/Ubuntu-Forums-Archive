---
title: "iptables logging IPs"
date: 2012-06-07
forum: Server Platforms
---

### Post by sandyd on 2012-06-07
How can I log all IPs attempting to access port 80 on a certian ip address with iptables?

---

### Post by Doug S on 2012-06-07
Since [this]("http://ubuntuforums.org/showthread.php?t=1925458"), I have been using this:```
#
# Ver 0.40 add logging. ESTABLISHED,RELATED path is above so eliminate it here.
#
echo Allowing EXTERNAL access to the WWW server
#$IPTABLES -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $EXTIP --dport 80 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 80 -j LOG --log-prefix "NEW80:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 80 -j ACCEPT
```Where:
IPTABLES=/sbin/iptables
UNIVERSE="0.0.0.0/0"
EXTIP="209.121.28.192" (my external static IP address)
EXTIF="eth1"
 
Then I can use grep to parse out only those lines from the log files by the "NEW80:" identifier. My site is not very busy so the logs do not get too big (<500 new connections per day average).

---

### Post by Doug S on 2012-08-21
sandyd: did you ever find a solution? If you did, and if it is different than my suggestion, what was it? (Just curious, and I see you on the forums a lot today, so I thought I'd ask.)

---

