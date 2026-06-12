---
title: "Question about UFW log entries"
date: 2013-12-23
forum: Security
---

### Post by donsy on 2013-12-23
I turned on UFW logging and starting getting the following messages repeating about every 2 minutes. Since I'm not familiar with the syntax, can someone please interpret these for me? I'm especially puzzled about the MAC address? It doesn't  match anything in ifconfig nor the router. Also, what is the number between the [ ... ] ? 

```

Dec 23 11:06:59 BSWZ1S1 kernel: [ 9513.006290] [UFW BLOCK] IN=wlan0 OUT= MAC=(removed) SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2
Dec 23 11:07:00 BSWZ1S1 kernel: [ 9514.498086] [UFW BLOCK] IN=wlan0 OUT= MAC=(removed) SRC=192.168.1.1 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2
Dec 23 11:09:05 BSWZ1S1 kernel: [ 9638.842029] [UFW BLOCK] IN=wlan0 OUT= MAC=(removed) SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2
Dec 23 11:09:12 BSWZ1S1 kernel: [ 9646.132083] [UFW BLOCK] IN=wlan0 OUT= MAC=(removed) SRC=192.168.1.1 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2
Dec 23 11:11:11 BSWZ1S1 kernel: [ 9764.680088] [UFW BLOCK] IN=wlan0 OUT= MAC=(removed) SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2
Dec 23 11:11:18 BSWZ1S1 kernel: [ 9772.607784] [UFW BLOCK] IN=wlan0 OUT= MAC=(removed) SRC=192.168.1.1 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2
Dec 23 11:13:17 BSWZ1S1 kernel: [ 9890.523280] [UFW BLOCK] IN=wlan0 OUT= MAC=(removed) SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2
Dec 23 11:13:18 BSWZ1S1 kernel: [ 9891.799692] [UFW BLOCK] IN=wlan0 OUT= MAC=(removed) SRC=192.168.1.1 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2
Dec 23 11:15:23 BSWZ1S1 kernel: [10016.350605] [UFW BLOCK] IN=wlan0 OUT= MAC=(removed) SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2
Dec 23 11:15:32 BSWZ1S1 kernel: [10025.947912] [UFW BLOCK] IN=wlan0 OUT= MAC=(removed) SRC=192.168.1.1 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2
Dec 23 11:17:29 BSWZ1S1 kernel: [10142.193201] [UFW BLOCK] IN=wlan0 OUT= MAC=(removed) SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2
Dec 23 11:19:35 BSWZ1S1 kernel: [10268.029660] [UFW BLOCK] IN=wlan0 OUT= MAC=(removed) SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2
Dec 23 11:19:42 BSWZ1S1 kernel: [10275.959050] [UFW BLOCK] IN=wlan0 OUT= MAC=(removed) SRC=192.168.1.1 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 

```

---

### Post by bashiergui on 2013-12-23
Those are multicast messages your router is sending to all devices on your LAN. This describes multicasting in general [http://en.m.wikipedia.org/wiki/Multicast_address](http://en.m.wikipedia.org/wiki/Multicast_address)


Basically they are packets your router is using to manage addressing the devices on its network. 


The MAC address is actually two MAC addresses mashed together. One half is probably the router and the other half is probably the device it's trying to communicate with.


The numbers between the brackets aren't really important. I think they're just numbers the OS assigns to each event.

I don't see the value in blocking multicast internally like you're doing (i.e. on your Ubuntu client). There might be value in blocking multicast coming in from the internet (i.e. on the router).

---

### Post by donsy on 2013-12-24
I tried adding this rule:
```
sudo ufw allow from 192.168.1.0/24
```
and still getting:
```
Dec 24 09:18:25 BSWZ1S1 kernel: [ 5241.910715] [UFW BLOCK] IN=  OUT=wlan0 SRC=192.168.1.147 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0  TTL=1 ID=0 DF PROTO=2
```
What rule(s) should I add that won't pose a security risk?

---

### Post by bashiergui on 2013-12-24
I believe you need this rule to allow multicasting
```
sudo ufw allow out proto udp to 224.0.0.0/24
sudo ufw allow in proto udp to 224.0.0.0/24
```

Are you blocking all in and out by default on the computer? What are your rules?

---

### Post by donsy on 2013-12-24
Here are my rules:
```
$ sudo ufw status verbose
Status: active
Logging: off
Default: deny (incoming), deny (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
25,53,80,110,443/tcp       ALLOW OUT   Anywhere
53,67,68/udp               ALLOW OUT   Anywhere
6969/tcp                   ALLOW OUT   Anywhere
123/udp                    ALLOW OUT   Anywhere
21/tcp                     ALLOW OUT   Anywhere
43/tcp                     ALLOW OUT   Anywhere
2083/tcp                   ALLOW OUT   Anywhere
11371/tcp                  ALLOW OUT   Anywhere
465,993/tcp                ALLOW OUT   Anywhere
2096/tcp                   ALLOW OUT   Anywhere
3306/tcp                   ALLOW OUT   Anywhere
5353/udp                   ALLOW OUT   Anywhere
31.13.64.0/18              REJECT OUT  Anywhere
66.220.144.0/20            REJECT OUT  Anywhere
69.171.224.0/19            REJECT OUT  Anywhere
69.63.176.0/20             REJECT OUT  Anywhere
22                         ALLOW OUT   Anywhere
23/tcp                     ALLOW OUT   Anywhere
2087                       ALLOW OUT   Anywhere
25,53,80,110,443/tcp       ALLOW OUT   Anywhere (v6)
53,67,68/udp               ALLOW OUT   Anywhere (v6)
6969/tcp                   ALLOW OUT   Anywhere (v6)
123/udp                    ALLOW OUT   Anywhere (v6)
21/tcp                     ALLOW OUT   Anywhere (v6)
43/tcp                     ALLOW OUT   Anywhere (v6)
2083/tcp                   ALLOW OUT   Anywhere (v6)
11371/tcp                  ALLOW OUT   Anywhere (v6)
465,993/tcp                ALLOW OUT   Anywhere (v6)
2096/tcp                   ALLOW OUT   Anywhere (v6)
3306/tcp                   ALLOW OUT   Anywhere (v6)
5353/udp                   ALLOW OUT   Anywhere (v6)
22                         ALLOW OUT   Anywhere (v6)
23/tcp                     ALLOW OUT   Anywhere (v6)
2087                       ALLOW OUT   Anywhere (v6)

```

The rules you suggested didn't work, so I deleted them.

---

### Post by bashiergui on 2013-12-24
> **donsy said:**
> I tried adding this rule:
```
sudo ufw allow from 192.168.1.0/24
```
and still getting:
```
Dec 24 09:18:25 BSWZ1S1 kernel: [ 5241.910715] [UFW BLOCK] IN=  OUT=wlan0 SRC=192.168.1.147 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0  TTL=1 ID=0 DF PROTO=2
```
That should have worked. Did you stop and restart ufw before testing?```
sudo ufw disable && sudo ufw enable
```

---

### Post by bashiergui on 2013-12-24
Also did you modify the /etc/ufw/before.rules file? If you want to allow multicasting make sure the line isn't commented out.
See part 3 of this thread [http://ubuntuforums.org/showthread.php?t=1893751&p=11529111&highlight=Multicast#post11529111](http://ubuntuforums.org/showthread.php?t=1893751&p=11529111&highlight=Multicast#post11529111)

---

### Post by donsy on 2013-12-24
It looks like it's working now. Thanks for the tip on stopping and restarting UFW.

---

