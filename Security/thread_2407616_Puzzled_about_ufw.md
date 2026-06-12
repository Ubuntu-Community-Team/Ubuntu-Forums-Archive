---
title: "Puzzled about ufw"
date: 2018-12-06
forum: Security
---

### Post by wimonlinux on 2018-12-06
Hello eveybody,

First off, my linux knowledge is rather limited, but I'm learning (or trying to).

The background: I'm trying to setup a system that is connected through 4G to the internet, for which I need to limit the internet traffic to the absolute minimum.  I need a service called "zerotier-one" on it, as well as access through ssh.  I'm trying to accomplish this by setting up ufw to block everything, except what I just mentioned.  For the zerotier service to work, it needs port 9993 open in- and outbound (udp).

The problem: ufw still seems to be blocking requests in/out on port 9993, and I have no clue why.

When I look at the config of ufw (default is deny both incoming and outgoing)
```
$ sudo ufw status numbered
Status: active
     To                         Action      From
     --                         ------      ----
[ 1] 22/tcp                     ALLOW IN    Anywhere
[ 2] 80                         ALLOW IN    Anywhere
[ 3] 9993/udp                   ALLOW IN    Anywhere
[ 4] 9993/udp (v6)              ALLOW IN    Anywhere (v6)

```

However when I look at the ufw.log, I still see occurences like this:
```
[UFW BLOCK] IN= OUT=wlan0 SRC=192.168.1.3 DST=45.32.248.87 LEN=165 TOS=0x00 PREC=0x00 TTL=64 ID=33643 PROTO=UDP SPT=9993 DPT=9993 LEN=145
```

Can anyone assist on where I'm going wrong?
Thank you in advance,
Wim

---

### Post by wimonlinux on 2018-12-06
Ok, i must have been going blind... I must have misread somehwere that 'sudo ufw allow 9993' allowed both in and out traffic on port 9993, while in the action above it clearly states "Allow IN".

Adding 'sudo ufw allow out 9993' solved the problem!

Wim

---

