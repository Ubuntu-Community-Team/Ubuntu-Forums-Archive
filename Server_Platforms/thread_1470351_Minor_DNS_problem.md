---
title: "Minor DNS problem"
date: 2010-05-02
forum: Server Platforms
---

### Post by wvw on 2010-05-02
Hello

I have configured DNS on ubuntu server 8.10 and it is working fine. There is one question I have though. Everytime I ping a LAN device by name I get the reply from the server with only the IP Address.

What is wrong in my bind config to cause this?

TIA
wvw

---

### Post by CharlesA on 2010-05-02
Like this?

```

charles@thor:~$ ping router
PING router.asgard.lcl (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.297 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.270 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.282 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.282 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.294 ms
^C
--- router.asgard.lcl ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4003ms
rtt min/avg/max/mdev = 0.270/0.285/0.297/0.009 ms

```

It's normal.

---

### Post by wvw on 2010-05-03
Hi Charles

Thanks for that. I wasn't sure about it as I saw from pings the name is normally returned. But at least you've put my mind at ease.

Thanks muchly
wvw

---

