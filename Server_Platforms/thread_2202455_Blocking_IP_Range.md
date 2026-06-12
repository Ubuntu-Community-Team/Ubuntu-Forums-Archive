---
title: "Blocking IP Range?"
date: 2014-01-29
forum: Server Platforms
---

### Post by sunshinedude on 2014-01-29
Hello,

I need some help.. I want to block Owner IP Range which is 213.228.128.0 - 213.228.131.255 (1,024 ip), How can i block it using iptables or any other way? I'm using ubuntu 12.x 64bit.

PS: i've tried this 
> sudo iptables -A INPUT -m iprange --src-range 213.228.128.0-213.228.131.255 -j DROP
But getting this error: 
> iptables v1.4.12: Couldn't load match `iptables':No such file or directory
Try `iptables -h' or 'iptables --help' for more information.

I'm new to ubuntu :)

Please reply as soon as possible.

Thank you.

---

### Post by TheFu on 2014-01-29
The format is: ```
sudo /sbin/iptables -I INPUT -s  213.228.128.0/22   -j DROP
```
but I didn't look up the netmask (22) for you.  that is just a guess.

---

