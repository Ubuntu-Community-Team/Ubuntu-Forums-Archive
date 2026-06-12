---
title: "MoBlock Does Not Prevent Browsing To Blocked IPs"
date: 2010-03-11
forum: Security
---

### Post by a_pedestrian on 2010-03-11
Thanks a lot for your time.

I have installed MoBlock as instructed here: [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

After installation I created my own list file in /etc/blockcontrol/custom-blocklist.p2p and have the following uncommented at the bottom of /etc/blockcontrol/blocklists.list:

```
locallist /etc/blockcontrol/custom-blocklist.p2p
```

The list contains the following 2 entries:

```
Yahoo:98.137.149.56
Google:74.125.47.147
```

When I do:

```
$sudo blockcontrol start
$ping 98.137.149.56
```

I get:

```
From 192.168.x.y icmp_seq=1 Destination Port Unreachable
```

But when I do:

```
$sudo blockcontrol stop
$ping 98.137.149.56
```

I then get:

```
64 bytes from 98.137.149.56: icmp_seq=1 ttl=57 time=114 ms
```

So moblock is certainly doing something.

*Recently I just noticed that the locallist rules seem to have no effect.  I will always get "destination port unreachable" even if the locallist entry in blocklists.list is commented out.*

**However, whenever I try to browse to that IP, even when blockcontrol is on, even by typing the IP into Konqueror (not the domain name), it lets me go there every time.  How can I know that my other applications will not to do the same thing?  How can I lock this down and test it empirically to be sure?**

Thank you!

---

### Post by lovinglinux on 2010-03-11
Your custom blocklist should be like this:

```
Yahoo:98.137.149.56-98.137.149.56
Google:74.125.47.147-74.125.47.147
```

The format of blocklist should have a IP range, not only the IP number.

You can browse those web sites probably because you have allowed http in blockcontrol.conf. Comment the line below to avoid this:

```
WHITE_TCP_OUT="http https"
```

---

