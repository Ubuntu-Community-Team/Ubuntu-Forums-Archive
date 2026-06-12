---
title: "Ip route cache in 3.18 kernel"
date: 2016-10-07
forum: Server Platforms
---

### Post by danethz on 2016-10-07
Hello,
There is a server:
```

uname -a
Linux Gateway 3.18.0-031800-generic #201412071935 SMP Mon Dec 8 00:36:34 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

cat /etc/issue.net
Ubuntu 14.04.1 LTS

```


Trying to use 2 ISP with script:
```

#!/bin/sh


. /root/balance/vars


OLDIF1=0
OLDIF2=0


. /root/balance/routing.sh
. /root/iptables-rules.sh


while true; do


ping -c 3 -s 100 77.88.8.7 -I $IF1 > /dev/null
if [ $? -ne 0 ]; then
  echo "Failed IF1!"
  NEWIF1=0
else
  NEWIF1=1
fi


ping -c 3 -s 100 77.88.8.8 -I $IF2 > /dev/null
if [ $? -ne 0 ]; then
  echo "Failed IF2!"
  NEWIF2=0
else
  NEWIF2=1
fi


if (( [ $NEWIF1 -ne $OLDIF1 ] || [ $NEWIF2 -ne $OLDIF2 ] )); then
  echo "Changing routes"
  if (( [ $NEWIF1 -eq 1 ] && [ $NEWIF2 -eq 1 ] )); then
  echo "Both channels"
  ip route delete default
  ip route add default scope global nexthop via $P1 dev $IF1 weight $W1 nexthop via $P2 dev $IF2 weight $W2
  elif (( [ $NEWIF1 -eq 1 ] && [ $NEWIF2 -eq 0 ] )); then
  echo "First channel"
  ip route delete default
  ip route add default via $P1 dev $IF1


elif (( [ $NEWIF1 -eq 0 ] && [ $NEWIF2 -eq 1 ] )); then
  echo "Second channel"
  ip route delete default
  ip route add default via $P2 dev $IF2
  fi
else
  echo "Not changed"
fi


OLDIF1=$NEWIF1
OLDIF2=$NEWIF2
sleep 3

```

My main routing table looks like:
```

 ip ro sh
default
        nexthop via $ISP1_GW  dev eth1 weight 1
        nexthop via $ISP2_GW  dev eth2 weight 1
$ISP1_NET dev eth1  proto kernel  scope link  src $ISP1_MY_IP
$ISP2_NET dev eth2  proto kernel  scope link  src $ISP2_MY_IP
$LOCAL_NET dev eth0  proto kernel  scope link  src $LOCAL_IP

```

Ip rules:
```

 ip ru sh
0:      from all lookup local
32762:  from all to 77.88.8.7 lookup provider1 
32763:  from all to 77.88.8.8 lookup provider2
32764:  from $ISP2_MY_IP lookup provider2
32765:  from $ISP1_MY_IP lookup provider1
32766:  from all lookup main
32767:  from all lookup default

```

This [presentation]("http://vger.kernel.org/~davem/columbia2012.pdf") says why "ip route cache" was removed in kernel 3.6 and higher.
That's why i'm trying kernet 3.18. On kernel 3.13 was the same problem :(
But i still see nothing in cache table:
```

root@Gateway:~# ip route show cache
root@Gateway:~#

```
Using traceroute on server selecting new route in 50\50 chance, but he has to select same route after first random select.

And lnstat shows rt_cache table contains several entries:
```

 lnstat -s1 -i1 -c-5 -f rt_cache
rt_cache|rt_cache|rt_cache|rt_cache|rt_cache|rt_cache|rt_cache|rt_cache|rt_cache|rt_cache|rt_cache|rt_cache|rt_cache|rt_cache|rt_cache|rt_cache|rt_cache|
 entries|  in_hit|in_slow_|in_slow_|in_no_ro|  in_brd|in_marti|in_marti| out_hit|out_slow|out_slow|gc_total|gc_ignor|gc_goal_|gc_dst_o|in_hlist|out_hlis|
        |        |     tot|      mc|     ute|        |  an_dst|  an_src|        |    _tot|     _mc|        |      ed|    miss| verflow| _search|t_search|
      33|       0|   13730|       0|    4232|  110337|       0|  705298|       0|      67|       0|       0|       0|       0|       0|       0|       0|
      33|       0|       0|       0|       0|      15|       0|      44|       0|       0|       0|       0|       0|       0|       0|       0|       0|
      33|       0|       0|       0|       0|       6|       0|      31|       0|       0|       0|       0|       0|       0|       0|       0|       0|
      33|       0|       0|       0|       0|       6|       0|      21|       0|       0|       0|       0|       0|       0|       0|       0|       0|
      33|       0|       0|       0|       0|       7|       0|      26|       0|       0|       0|       0|       0|       0|       0|       0|       0|

```
What is that 33 rt_cache_entries? How can I look at them?

Can anyone tell me how can I use ip route cache? :)
Thanks to all :)

---

