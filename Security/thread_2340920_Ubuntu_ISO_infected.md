---
title: "Ubuntu ISO infected?"
date: 2016-10-23
forum: Security
---

### Post by buntuluxx on 2016-10-23
Hi!

Yesterday I installed Lubuntu 16.04 to my HDD and discovered  some very  strange traffic both incoming and outgoing from the ntp port,  listed  under 123/udp. 

After researching the connecting IPs I found out that most of them correspond to local software businesses and IT firms.

I  checked the traffic with iftop, which showed that multiple bytes, in   some cases even +1KB, was sent and received to and from those IPs.

Screenshot: [https://s12.postimg.org/w647skop9/screen.png](https://s12.postimg.org/w647skop9/screen.png)


.)Do I have to be worried, that those services transmitted malware or other harmful code?

.)How can I permanently block those connections or port?

I have tried using the following, unsuccessfully.

-->with the built in firewall
```
sudo ufw deny 123/udp
```
```
sudo ufw deny ntp
```

-->with iptables
```
sudo iptables -A OUTPUT -p udp --dport 123 -j DROP

```

```
sudo iptables -A INPUT -p udp --sport 123 -j DROP

```

Thank you!

---

### Post by howefield on 2016-10-23
Duplicate thread closed.

[https://ubuntuforums.org/showthread.php?t=2340919](https://ubuntuforums.org/showthread.php?t=2340919)

---

