---
title: "Eucalyptus 2.0 Ubuntu 10.10 instance not pinging public network unless iptables"
date: 2011-06-28
forum: Server Platforms
---

### Post by m4ci3k on 2011-06-28
Hello,
I'm have a following problem:
CLC - with eth0 - public IP from ISP and eth1 with 192.168.10.1
than on  nc-s i have eth0 with 192.168.10.2-7

When i start the instance it gets public ip from the range of
192.168.10.150-200 and private ip 17.16.1.2-100 .
The problem is when i start the instance and ssh to it i cannot ping
the outside world. So after reading alot of posts i put
iptables -t nat -I POSTROUTING -s 172.19.1.0/27 -o eth0 -j MASQUERADE
rule on clc than this instance start pinging.
Everything would be great if that would be permament state. If i turn
off instance and start another one it doesn't ping outside world as
long as i put again iptables -t nat -I POSTROUTING -s 172.19.1.0/27 -o
eth0 -j MASQUERADE.

And now the funniest part:
I have checked iptables -L and the rule stays there all the time.
Another weird thing is i can start one instance and insert the
iptables -t nat -I POSTROUTING -s 172.19.1.0/27 -o eth0 -j MASQUERADE
, than start pinging outside world. While i'm pinging the outside
world from the first instance i start second instance and while the
first one is pinging the outside world the second doesn't unless i
insert iptables -t nat -I POSTROUTING -s 172.19.1.0/27 -o eth0 -j
MASQUERADE again on the CLC.

Any Idea whats the problem? I'll be really grateful as i play with it
for over the week now.

---

