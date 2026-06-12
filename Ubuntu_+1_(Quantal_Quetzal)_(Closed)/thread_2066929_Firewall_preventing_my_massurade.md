---
title: "Firewall preventing my massurade"
date: 2012-10-05
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pqwoerituytrueiwoq on 2012-10-05
in gufw i need have it allow this to work
when i enable the firewall this breaks, but i need to keep the some stuff local only so i need the firewall, this worked on 12.04
```
echo 1 > /proc/sys/net/ipv4/ip_forward
while [ 0`pidof NetworkManager` -eq 0 ]; do
    sleep 1
done
while [ "`ifconfig eth0 | grep 'inet addr:'`" = "" ]; do
    sleep 2
done
while [ "`ifconfig eth0:1 | grep 'inet addr:'`" = "" ]; do
    sleep 2
    ifconfig eth0:1 10.0.0.1 netmask 255.255.0.0
done
#iptables -t nat -A PREROUTING -o eth0 -p tcp -m tcp --dport 80 -j DNAT --to-destination 10.0.0.75:80
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -P FORWARD ACCEPT
service isc-dhcp-server start

```

---

### Post by pqwoerituytrueiwoq on 2012-10-06
i figured out port 80 udp allows the dns server to work
also seems my script needs to run after the firewall starts

---

### Post by alphacrucis2 on 2012-10-06
> **pqwoerituytrueiwoq said:**
> i figured out port 80 udp allows the dns server to work
also seems my script needs to run after the firewall starts


Odd. DNS should be using udp port 53.

---

### Post by pqwoerituytrueiwoq on 2012-10-06
for some reason doing that got it working knew dhcp's port was in the 50s
as long as it works

---

