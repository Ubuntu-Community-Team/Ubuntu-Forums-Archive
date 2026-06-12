---
title: "Hundreds of entries in ufw.log - internal IP ?"
date: 2018-08-27
forum: Security
---

### Post by oygle on 2018-08-27
The connection to the internet went off the air for about 10 mins tonight. I went looking in ufw.log and found the following entries ..

> 
Aug 27 19:50:11 oygle kernel: [ 2176.600166] [UFW BLOCK] IN=enp7s0 OUT= MAC=********** SRC=192.168.20.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2


No less than 644 entries like this, in 44 minutes. These are the only rules ..

```
 sudo ufw status
```

> Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       192.168.1.102             
Anywhere                   ALLOW       192.168.1.102/tcp          (log-all)
Anywhere                   ALLOW       192.168.1.103/tcp          (log-all)

---

### Post by Doug S on 2018-08-27
As far as I know, it is O.K. to block such local multicast addresses. UFW is just a front end for iptables. Show us your entire resulting iptables rule set, as perhaps the log entries you are observing are a UFW default. Show us the output from:
```
sudo iptables -v -x -n -L
```

---

### Post by oygle on 2018-08-27
Thanks, the output is at [https://paste.ubuntu.com/p/pnSP4FMgbz/](https://paste.ubuntu.com/p/pnSP4FMgbz/)

---

### Post by Doug S on 2018-08-27
One thing I do not like about UFW is that is uses the same logging comment in multiple places. Very annoying when trying to debug. Anyway, yes it doesn't seems to like broadcast IP addresses. I do not think this was the source of your problems.

---

### Post by oygle on 2018-08-30
Okay thanks 'Doug S'  :)

---

