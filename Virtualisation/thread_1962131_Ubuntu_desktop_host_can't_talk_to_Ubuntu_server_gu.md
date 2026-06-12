---
title: "Ubuntu desktop host can't talk to Ubuntu server guest in Virtualbox"
date: 2012-04-20
forum: Virtualisation
---

### Post by AlanQ on 2012-04-20
Vitualbox 4.1.12
Host: Ubuntu 10.04LTS 64bit desktop
Guest: Ubuntu 10.04LTS 64bit server

ifconfig on each system shows 
host as 192.168.0.2 on eth1
vboxnet0 is 10.0.2.1
guest is 10.0.2.15 on eth0

```
[COLOR="Blue"]**host**[/COLOR]$ ping 10.0.2.1
PING 10.0.2.1 (10.0.2.1) 56(84) bytes of data.
64 bytes from 10.0.2.1: icmp_seq=1 ttl=64 time=0.095 ms
64 bytes from 10.0.2.1: icmp_seq=2 ttl=64 time=0.070 ms
64 bytes from 10.0.2.1: icmp_seq=3 ttl=64 time=0.073 ms
^C
--- 10.0.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.070/0.079/0.095/0.013 ms
```

```
[COLOR="Blue"]**host**[/COLOR]$ ping 10.0.2.15
PING 10.0.2.15 (10.0.2.15) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
^C
--- 10.0.2.15 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2007ms
```

```
[COLOR="Red"]**guest**[/COLOR]$ ping 192.168.0.2
PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
64 bytes from 192.168.0.2 icmp_seq=1 ttl=63 time=0.440 ms
64 bytes from 192.168.0.2 icmp_seq=2 ttl=63 time=1.26 ms
64 bytes from 192.168.0.2 icmp_seq=3 ttl=63 time=0.548 ms
^C
--- 192.168.0.2 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 0.440/0.750/1.264/0.367 ms
```

I have lost count of the number of web pages and forum posts I have read to try to solve this. I am experienced with Ubuntu but know very little about networking and firewalls, so most of what I've tried I don't understand (and it hasn't worked anyway).

Eventually I want to host a web server on the guest to be accessed by the host only (no connection to Internet wanted or desirable).

I would post various other details but I don't know what's relevant, so I'll wait for the usual "*post the output of ...*" in any replies.

Can someone take pity on me? :(

---

### Post by CharlesA on 2012-04-20
Set the guest's network to bridged instead and NAT and you will be set.

---

### Post by AlanQ on 2012-04-21
Thank you, CharlesA, that works!

Indeed, host-only is perhaps even better for my purposes. If I can get it to work just right...
[I'll hold off marking this thread SOLVED until then]

My mistake (although I don't quite understand why this is a problem) was to keep adding Adapters to try to fix the problem.
So I had
Adapter1 NAT
Adapter2 Bridged
Adapter3 Host-Only

With only
Adapter 1 Bridged (or Host-only?) it works.
Your reply was the prompt I needed to try this.

Cheers
Alan

---

### Post by CharlesA on 2012-04-21
host-only lets the VMs talk to each other but not the host iirc.

[http://www.virtualbox.org/manual/ch06.html#network_hostonly](http://www.virtualbox.org/manual/ch06.html#network_hostonly)

---

