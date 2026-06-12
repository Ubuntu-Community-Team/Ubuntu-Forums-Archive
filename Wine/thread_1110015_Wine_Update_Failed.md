---
title: "Wine Update Failed"
date: 2009-03-29
forum: Wine
---

### Post by SuperNapalm on 2009-03-29
Trying to install latest version of Wine, getting this error message

```
W: Failed to fetch http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_1.1.18~winehq0~ubuntu~8.10-0ubuntu1_i386.deb
  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)
```

Any idea whats gone wrong?

---

### Post by Alethenorio on 2009-03-29
Getting the exact same problem. Repositorie must be down, guess we just have to wait.

---

### Post by jpmelos on 2009-03-29
I'm having this issue as well. The repositories must be down, maybe they are updating to the latest development version, released two days ago, the 1.1.18.

---

### Post by Reiger on 2009-03-29
Altough the server is up and running:
```
ping 81.171.111.184
PING 81.171.111.184 (81.171.111.184) 56(84) bytes of data.
64 bytes from 81.171.111.184: icmp_seq=1 ttl=57 time=797 ms
64 bytes from 81.171.111.184: icmp_seq=2 ttl=57 time=209 ms
64 bytes from 81.171.111.184: icmp_seq=3 ttl=57 time=708 ms
64 bytes from 81.171.111.184: icmp_seq=4 ttl=57 time=30.0 ms
64 bytes from 81.171.111.184: icmp_seq=5 ttl=57 time=52.3 ms
64 bytes from 81.171.111.184: icmp_seq=6 ttl=57 time=95.5 ms
64 bytes from 81.171.111.184: icmp_seq=7 ttl=57 time=521 ms
64 bytes from 81.171.111.184: icmp_seq=8 ttl=57 time=112 ms
64 bytes from 81.171.111.184: icmp_seq=9 ttl=57 time=361 ms
^C
--- 81.171.111.184 ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 8013ms
rtt min/avg/max/mdev = 30.082/320.901/797.465/275.326 ms

```

---

### Post by SuperNapalm on 2009-03-29
Nah still not working :/

---

### Post by cogadh on 2009-03-29
> **Reiger said:**
> Altough the server is up and running:

The server itself may be physically up and running, but the Wine repository on it is currently not. This happens every once in a while, no biggie. It will be back up eventually.

---

### Post by notmatt on 2009-03-30
Still down for me at least.

---

### Post by Devilman13 on 2009-03-30
This is driving me NUTTTZZZ!!!!

Nice to know I'm not the only one though, although I'm sure you all wish it were otherwise :lolflag:

---

### Post by Mehall on 2009-03-31
> **Devilman13 said:**
> This is driving me NUTTTZZZ!!!!

Nice to know I'm not the only one though, although I'm sure you all wish it were otherwise :lolflag:

Lol, +1 to that and still having the same issue

---

