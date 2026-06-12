---
title: "UFW &amp;linux-igd &amp;Chain FORWARD (policy ACCEPT)"
date: 2012-09-05
forum: Security
---

### Post by CalvinZA on 2012-09-05
[FOUND SOLUTION]
/etc/default/ufw
```

DEFAULT_FORWARD_POLICY="ACCEPT"

```


Good day,

I have UFW configured as follows
```

$ sudo ufw status verbose 
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
Anywhere                   ALLOW IN    10.0.0.0/24
65432/tcp                  ALLOW IN    Anywhere
65432/udp                  ALLOW IN    Anywhere
65432/tcp                  ALLOW IN    Anywhere (v6)
65432/udp                  ALLOW IN    Anywhere (v6)


```I would like Chain FORWARD to ACCEPT, as these are the ports opened by linux-igd for UPnP services on the network. 
Examples listed bellow.

My gratitude to anybody who may assist, thank you.

UFW Disabled
```

$ sudo iptables -L FORWARD
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             10.0.0.100           udp dpt:55914
ACCEPT     tcp  --  anywhere             10.0.0.100           tcp dpt:55914
ACCEPT     tcp  --  anywhere             10.0.0.103           tcp dpt:54117
ACCEPT     udp  --  anywhere             10.0.0.103           udp dpt:54117
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            
ACCEPT     all  --  10.0.0.0/8           anywhere             ctstate NEW
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED



```UFW Enabled
```
$ sudo iptables -L FORWARD
Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             10.0.0.100           udp dpt:55914
ACCEPT     tcp  --  anywhere             10.0.0.100           tcp dpt:55914
ACCEPT     tcp  --  anywhere             10.0.0.103           tcp dpt:54117
ACCEPT     udp  --  anywhere             10.0.0.103           udp dpt:54117
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            
ACCEPT     all  --  10.0.0.0/8           anywhere             ctstate NEW
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
  
```

---

