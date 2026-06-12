---
title: "Scanrand Problem HELP"
date: 2007-10-20
forum: Server Platforms
---

### Post by paneas13 on 2007-10-20
I 've installed scanrand via Synaptic:
```

sudo apt-get install paketto

```

I cannot scan an entire class C network. This is where scanrand really shows its power. But I cannot...

> 
root@blackslash13-desktop:~# scanrand -b10M 10.0.1.1-254:80,20-25,139
Destination required.
scanrand 1.10: Stateless TCP Scanner w/ Inverse SYN Cookies(HMAC-SHA1/32 in SEQ)
Component of:  Paketto Keiretsu 1.10;    Dan Kaminsky  (dan@doxpara.com)
     Example:  scanrand -b10M 10.0.1.1-254:80,20-25,139
  Def. Ports:  Use  [quick/squick/known/all] instead of explicitly naming ports
     Options:  -S/-L:    Only send requests      / Only listen for responses
               -e/-E:    Show negative responses / Only show negative responses
               -t  [timeout]: Wait n full seconds for the last response   (10s)
               -b[bandwidth]: Limit bandwidth consumption to n b/k/m/g bytes(0)
                              (0 supresses timeouts or maximizes bw utilization)
               -N/-NN       : Enable name resolution (Prefer Source/Dest)
               -v           : Mark packets being sent, as well as received
               -vv          : Output full packet traces to stderr
  Addressing:  -d   [device]: Send requests from this L2 hardware device
               -i   [source]: Send requests from this L3 IP address
               -p   [  port]: Send requests from this L4 TCP Port
               -s   [  seed]: Use prespecified seed for scan verification
               -f   [  file]: Read list of targets from file
 Experiments:  -l  [ttl-ttl]: Statelessly TCP Traceroute
               -D           : Distco (Distance Discover) via forced RSTs
               -c           : Try checking Inverse SYN Cookie on Traceroute
       Notes:                 Use Control-C to exit before scanrand times out.
                              Be sure to use a longer timeout for slow scans!
                              [n]: estimated network distance from target host.
                              Be careful about available bandwidth -- use -b!


How to solve this ?

---

### Post by paneas13 on 2007-11-07
No one ??????????????????????????????????????

---

### Post by paneas13 on 2007-12-13
No one ??????:lolflag:

How on Earth can I install scanrad ?

---

### Post by kububa on 2008-02-01
Hi.
I think there may be some bug in paketto.
I had the same problem in Gutsy, and just forced to version to 1.10-6 in Synaptic (from 1.10-7).
Now it works fine.

---

