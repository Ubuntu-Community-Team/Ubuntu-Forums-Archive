---
title: "DNS failure?"
date: 2005-03-03
forum: Server Platforms
---

### Post by askreet on 2005-03-03
First off I have no KVM access to my server, just SSH.

I set up a static ip using the interfaces file located at /etc/network/interfaces

Heres what I did:
```

iface eth0 inet static
address 192.168.0.6
netmask 255.255.255.0
up flush-mail   ( <-- This line was shown in the man file and I'm sure sure what it does.. )

```

Now I can connect to the server via FTP or SSH without any difficulties, but I cannot ping the outside world from the server, or rather i cant resolve DNS's

Using ping yahoo.com for example yields me "unknown host: yahoo.com"

Any idea why this would be happening? If I recall when it was in DHCP mode it worked better.

The nameserver lines are in resolv.conf.

---

### Post by alastair on 2005-03-04
So - you can ping [www.yahoo.com](www.yahoo.com) by IP address? But not by name?

What is in the resolv.conf?

Can you ping the nameserver IP address?

Can you query it e.g.

dig @<IP address of nameserver> yahoo.com

---

### Post by askreet on 2005-03-04
```
skreet@k-cubed:~ $ cat /etc/resolv.conf
nameserver 204.127.202.19
nameserver 216.148.227.204
skreet@k-cubed:~ $ ping 204.127.202.19
connect: Network is unreachable
skreet@k-cubed:~ $ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=1.26 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=1.27 ms

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.264/1.271/1.278/0.007 ms
skreet@k-cubed:~ $ ping yahoo.com
ping: unknown host yahoo.com
```

^^ I'm so lost. Anyone have any ideas?!

EDIT: I tried adding valid gateway and broadcast lines to my interfaces file then restarting eth0, same result.

---

### Post by askreet on 2005-03-04
SOLVED!

Apparently when making changes to the interface file doing ifconfig eth0 down && ifconfig eth0 up didnt re-apply them. I needed to do /etc/init.d/networking restart

Thanks for the reply though.

- askreet

---

