---
title: "bandwith limiting to ip?"
date: 2005-07-17
forum: Server Platforms
---

### Post by mrweirdo on 2005-07-17
Im trying to use traffic shaping to limit the upload links from my Ubuntu box to the ip 192.168.10 on the same LAN as the Ubuntu box. Basicaly I want the box assigned the IP to only be able to download files off the ubuntu box at 512kpbs. Anyways here is the script I came up with. Is this correct? Thanks.

shaper.sh
```

#!/bin/bash
# change these values to suit your needs
DEV=eth0
UPLINK=512
IP=192.168.0.10

tc qdisc add dev $DEV root handle 1: cbq avpkt 10000 bandwidth 100mbit 

tc class add dev $DEV parent 1: classid 1:1 cbq rate ${UPLINK}kbit allot 1500 prio 5 bounded isolated 

tc filter add dev $DEV parent 1: protocol ip prio 16 u32 match ip dst ${IP} flowid 1:1

```

---

### Post by mrweirdo on 2005-07-17
hrm something does seem to be wrong with it. I took a chance and went ahead and ran it:

It produced the following errors
```

mrweirdo@ubuntu:~$ sudo sh /etc/shaper/shaper-script.sh
"?at is "
Usage: ... cbq bandwidth BPS avpkt BYTES [ mpu BYTES ]
               [ cell BYTES ] [ ewma LOG ]
Illegal "rate"
Illegal "match"
mrweirdo@ubuntu:~$

```

---

### Post by gruepig on 2005-07-18
Not sure ... but do you have support for traffic shaping in your kernel (or the necessary  modules loaded)?

---

