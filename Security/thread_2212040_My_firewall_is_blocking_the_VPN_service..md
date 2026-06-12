---
title: "My firewall is blocking the VPN service."
date: 2014-03-19
forum: Security
---

### Post by Black_Pirate on 2014-03-19
I'm new to ubuntu and I'm learning how to deal with iptables yet, so I'm using GUFW.

I want to hide my IP from sites using a VPN service.

In GUFW I have allowed the port 1194 UDP(in and out) to the Openvpn but when I try to connect I recive a mensage saying that "the connection attempt timed out". When the GUFW is off I can connect normally to the VPN.



I have looked in the forum search but found nothig that can help me.

What I have to do?:confused::confused::confused:

---

### Post by TheFu on 2014-03-19
You do not need to open any ports inbound and for most people leaving all outbound ports open is common. 
First - get the VPN service working.
Second - lock down the outbound ports while allowing it to keep working.

It is possible that your network provider blocks all UDP. This is extremely common for company and university networks.

---

### Post by Lars Noodén on 2014-03-19
According to the FAQ, you need outbound TCP 443, TCP 943, UDP 1194.  But generally, with a client firewall, one restricts all incoming connections and allows all outgoing connections.  So in GUFW that would be Status: ON, Incoming: Reject, Outgoing: Allow.  If you want it more locked down than that, which isn't exactly recommended or advantageous, then you'll have to work on the Advanced GUFW rules.

---

### Post by Black_Pirate on 2014-03-19
Thanks for the answer! :D
       
      Reject all incoming and allow just TCP 443, TCP 943, UDP 1194 does not work.
    I have tryed to watch var/log/syslog but I don't know how to discover what port is blocking openvpn to function.
    
    
    Reject all incoming and allow all outgoing make it function.\\:D/
    If it is secure I can let it like that for now but if someone have any ideas I will try it.

---

### Post by TheFu on 2014-03-19
You could watch the logs for all outbound connections, then only allow those that you want.
There is a LOG mode in most firewalls.

---

### Post by sammiev on 2014-03-19
This is what I'm using, you can pick and choose but it works with openvpn.

```
[fwBasic]
status = enabled
incoming = deny
outgoing = deny

[Rule0]
ufw_rule = 80/tcp ALLOW OUT Anywhere (out)
description = 
command = ufw allow out 80/tcp
policy = allow
direction = out
protocol = tcp
from_ip = 
from_port = 
to_ip = 
to_port = 80
iface = 
logging = 

[Rule1]
ufw_rule = 443/tcp ALLOW OUT Anywhere (out)
description = 
command = ufw allow out 443/tcp
policy = allow
direction = out
protocol = tcp
from_ip = 
from_port = 
to_ip = 
to_port = 443
iface = 
logging = 

[Rule2]
ufw_rule = 25/tcp ALLOW OUT Anywhere (out)
description = 
command = ufw allow out 25/tcp
policy = allow
direction = out
protocol = tcp
from_ip = 
from_port = 
to_ip = 
to_port = 25
iface = 
logging = 

[Rule3]
ufw_rule = 110/tcp ALLOW OUT Anywhere (out)
description = 
command = ufw allow out 110/tcp
policy = allow
direction = out
protocol = tcp
from_ip = 
from_port = 
to_ip = 
to_port = 110
iface = 
logging = 

[Rule4]
ufw_rule = 143/tcp ALLOW OUT Anywhere (out)
description = 
command = ufw allow out 143/tcp
policy = allow
direction = out
protocol = tcp
from_ip = 
from_port = 
to_ip = 
to_port = 143
iface = 
logging = 

[Rule5]
ufw_rule = 67:68/udp ALLOW OUT Anywhere (out)
description = 
command = ufw allow out 67:68/udp
policy = allow
direction = out
protocol = udp
from_ip = 
from_port = 
to_ip = 
to_port = 67:68
iface = 
logging = 

[Rule6]
ufw_rule = 123/udp ALLOW OUT Anywhere (out)
description = 
command = ufw allow out 123/udp
policy = allow
direction = out
protocol = udp
from_ip = 
from_port = 
to_ip = 
to_port = 123
iface = 
logging = 

[Rule7]
ufw_rule = 1194/udp ALLOW OUT Anywhere (out)
description = 
command = ufw allow out 1194/udp
policy = allow
direction = out
protocol = udp
from_ip = 
from_port = 
to_ip = 
to_port = 1194
iface = 
logging = 

[Rule8]
ufw_rule = 53 ALLOW OUT Anywhere (out)
description = 
command = ufw allow out 53
policy = allow
direction = out
protocol = 
from_ip = 
from_port = 
to_ip = 
to_port = 53
iface = 
logging = 

[Rule9]
ufw_rule = 1723 ALLOW OUT Anywhere (out)
description = 
command = ufw allow out 1723
policy = allow
direction = out
protocol = 
from_ip = 
from_port = 
to_ip = 
to_port = 1723
iface = 
logging = 

[Rule10]
ufw_rule = 631 ALLOW OUT Anywhere (out)
description = 
command = ufw allow out 631
policy = allow
direction = out
protocol = 
from_ip = 
from_port = 
to_ip = 
to_port = 631
iface = 
logging = 

[Rule11]
ufw_rule = 515 ALLOW OUT Anywhere (out)
description = 
command = ufw allow out 515
policy = allow
direction = out
protocol = 
from_ip = 
from_port = 
to_ip = 
to_port = 515
iface = 
logging =
```

---

### Post by james114 on 2014-03-26
> **Black_Pirate said:**
> 

    Reject all incoming and allow all outgoing make it function.\\:D/
    If it is secure I can let it like that for now but if someone have any ideas I will try it.

I have a web server that only allows port 80 incoming and VPN works good. (other ports are rejected) 
I think it is secure.

---

