---
title: "traceroute results greatly differ from mtr/ping/traceroute-nanog...?"
date: 2008-07-16
forum: Server Platforms
---

### Post by fragtion on 2008-07-16
Hey guys,
I recently installed ubuntu hardy 8.04 64bit server edition standard iso on my AMD64 3400+ with a gig of ddr400. Everything was going great until I decided to perform a standard traceroute...

Here's what happens: with the original traceroute utility I get latencies which aren't accurate. I normally ping around 2-5ms to the host, but with traceroute it shows as 35-75ms. I've checked pretty much everything (tried -I, -In, udp, etc); I thought perhaps it could have been async routing or something to that effect, but it isn't.
I did try other hosts as well which route through another interface/gw, same problem.

The box isnt running a firewall - in fact everything is pretty much stock besides for IPv4 forwarding being enabled. I've eliminated that sort of thing as a possible cause anyway because mtr, tracepath, ping, traceroute-nanog & paris-traceroute all give the correct results - so does my windows box's tracert, and tracerouting from my wrt54g. They both route through the ubuntu box.

I tried compiling the latest 2.6 kernel with a migrated .config although I upped the mm clock Hz to 1000 thinking maybe that could have played a role, but it didn't make a difference. I also downloaded traceroute 2.0.11 source, compiled that, and the problem persists.

As you can see it's a very strange one indeed...
My guess is it's something to do with x86_64, or some kind of bug in traceroute itself, or something related there. If anyone knows what could be causing this problem please let me know - I'd much rather fix it than just switch back to 32bit.

Thanks for any help in advance! ;)

EDIT: Here's a sample:

> root@demsfw:~# traceroute 172.16.1.1
traceroute to 172.16.1.1 (172.16.1.1), 30 hops max, 40 byte packets
 1  eth0.sc-gw.fragtion.jawug (172.16.6.10)  0.684 ms  1.062 ms  2.186 ms
 2  wlan-gw.sc2-65.sc.Jawug (172.16.26.65)  9.732 ms  9.933 ms  10.103 ms
 3  nc.sc.jawug (172.16.253.9)  12.365 ms  12.796 ms  14.608 ms
 4  wugbox.jawug (172.16.1.1)  25.789 ms  26.897 ms  34.364 ms
root@demsfw:~# traceroute-nanog 172.16.1.1
traceroute to 172.16.1.1 (172.16.1.1), 64 hops max, 52 byte packets
 1  eth0.sc-gw.fragtion.jawug (172.16.6.10)  1 ms  1 ms  1 ms
 2  wlan-gw.sc2-65.sc.Jawug (172.16.26.65)  3 ms (TOS=8!)  3 ms  4 ms
 3  nc.sc.jawug (172.16.253.9)  12 ms  4 ms  2 ms
 4  wugbox.jawug (172.16.1.1)  7 ms  5 ms  9 ms
root@demsfw:~#

> 
root@demsfw:~# traceroute 196.35.68.1
traceroute to 196.35.68.1 (196.35.68.1), 30 hops max, 40 byte packets
 1  eth0.24-7online-gw.fragtion.jawug (172.16.6.11)  1.244 ms  1.952 ms  2.561 ms
 2  192.168.0.1 (192.168.0.1)  14.416 ms  15.261 ms  16.307 ms
 3  10.50.4.1 (10.50.4.1)  18.582 ms  19.583 ms  20.349 ms
 4  10.50.2.1 (10.50.2.1)  25.221 ms  26.342 ms  27.844 ms
 5  10.50.1.1 (10.50.1.1)  29.753 ms  30.873 ms  31.917 ms
 6  196.35.68.1 (196.35.68.1)  37.278 ms  36.251 ms  35.782 ms
root@demsfw:~# traceroute-nanog 196.35.68.1
traceroute to 196.35.68.1 (196.35.68.1), 64 hops max, 52 byte packets
 1  eth0.24-7online-gw.fragtion.jawug (172.16.6.11)  1 ms  1 ms  1 ms
 2  192.168.0.1 (192.168.0.1)  3 ms  4 ms  3 ms
 3  10.50.4.1 (10.50.4.1)  3 ms  3 ms  4 ms
 4  10.50.2.1 (10.50.2.1)  7 ms  4 ms  5 ms
 5  10.50.1.1 (10.50.1.1)  4 ms  4 ms  5 ms
 6  196.35.68.1 (196.35.68.1)  5 ms 4 ms  5 ms
root@demsfw:~#

> 
--- 196.35.68.1 ping statistics ---
23 packets transmitted, 23 received, 0% packet loss, time 22022ms
rtt min/avg/max/mdev = 4.785/5.880/11.404/1.483 ms
If I leave a ping running, it rarely goes above 10ms, if i do a traceroute at ANY time from the same box, however, it reports it as 35+ ms ? Very peculiar . i'm baffled :(

---

### Post by fragtion on 2008-07-17
bump...
I just switched to i386, and the problem still persists.
This is a definite bug of some sort that if not resolved here, will likely cause the same problem for someone else later on who does not have access to these forums.
Could it be a driver problem?

---

### Post by grapegrower on 2008-07-18
Not sure if this is the same issue I have, but when I ping the local router I get 1 to 2 ms, however if I do a traceroute to anything on the net I get 10ms to 15ms on the first hop :( 

```

tim@q6600:~$ ping -c 5 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.23 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.00 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.01 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=1.00 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.998 ms
--- 192.168.1.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4001ms
rtt min/avg/max/mdev = 0.998/1.051/1.234/0.093 ms

```


```

tim@q6600:~$ traceroute www.sbcglobal.net
traceroute to www.sbcglobal.net (216.77.188.41), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  11.859 ms  12.221 ms  12.543 ms

```


It doesn't seem to cause any performance issues, just weird to see a 10ms spike on the router.

Tim

---

### Post by MJN on 2008-07-18
Grapegrower,
 
It might be worth you trying traceroute with the -I flag as, by default, it uses UDP packets instead of ICMP ECHO requests (as ping does) hence 'poor-quality' home routers with weak UDP support in the stack could result in differing response times.
 
The OP already tried this with no difference hence it was of no relevence in their case.
 
Mathew

---

### Post by fragtion on 2008-09-12
sorry to be bumping the thread, just incase anyone else has this problem too, here's the bugreport to follow: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=515978](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=515978)

---

