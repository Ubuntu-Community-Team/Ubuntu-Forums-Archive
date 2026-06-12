---
title: "need to add to bandwith limiter using tc"
date: 2006-08-24
forum: Server Platforms
---

### Post by mrweirdo on 2006-08-24
Hello I have a script that limits outgoing bandwith for apache2 on my server which works great however I would like add anouther service or port to the limited list for openvpn(1194) and proftp(21). How can that be done by modifying this script? 

```

#!/bin/bash
# change these values to suit your needs
ETHERNET_DEVICE="eth0"
LINK_SPEED="384Kbit"
UPLOAD_SPEED="35Kbit"
PORT="80"

# delete previous root node
tc qdisc del dev $ETHERNET_DEVICE root

# create root node
tc qdisc add dev $ETHERNET_DEVICE root handle 1: htb default 11

# create LINK class
tc class add dev $ETHERNET_DEVICE parent 1: classid 1:1 htb rate $LINK_SPEED

# create our HTTP shaping class
tc class add dev $ETHERNET_DEVICE parent 1:1 classid 1:10 htb rate $UPLOAD_SPEED

# create our REST class for unutilized bandwidth
tc class add dev $ETHERNET_DEVICE parent 1:1 classid 1:11 htb rate $LINK_SPEED

# create the filter for the HTTP class, we filter on source port 80 (http)
tc filter add dev $ETHERNET_DEVICE protocol ip parent 1:0 prio 1 u32 match ip sport $PORT 0xffff flowid 1:10

```

Thanks :)

---

