---
title: "wireless auto connect?"
date: 2010-12-14
forum: Server Platforms
---

### Post by Gareth_2007 on 2010-12-14
hello every one,

right i have the wireless working on my server fine the only problem is every time to router goes down or the system restarts i have to manually connect it again :(

this is the code im using to tell it to connect: 

```

sudo iwconfig wlan0 essid Pikeynet key open
sudo ifconfig wlan0 192.168.2.20 netmask 255.255.255.0
sudo route add default gw 192.168.2.1
sudo sh -c "echo "nameserver 192.168.2.1" >> /etc/resolve.conf" 
```

is there any way i could add it to a file or create a file so every time it disconnects or after a restart it auto connects? 

cheers

---

### Post by Gareth_2007 on 2010-12-16
any one have any ideas cheers

---

### Post by Gareth_2007 on 2011-09-30
could still do with some help...

thanks

---

### Post by cariboo on 2011-09-30
When I had wireless on my server, I just setup the connection info in /etc/network/interfaces. That was about 5 years ago, I found that using wireless on a server just didn't work for me, and found a way to get a wired connection to my stand-alone garage where my server is located.

---

### Post by volkswagner on 2011-09-30
Try [this ]("http://ubuntuforums.org/showpost.php?p=10700392&postcount=2")on for size.

Depending on your security protocol you mileage may vary.

---

### Post by Gareth_2007 on 2011-09-30
i came across this:

#!/bin/bash

IP_ADRESS=192.168.1.1
( ! ping -c1 $IP_ADRESS >/dev/null 2>&1 ) && service network restart >/dev/null 2>&1

will that be ok to run or will it become a resource hog?

---

### Post by Jonathan L on 2011-10-01
> **Gareth_2007 said:**
> i came across this:

#!/bin/bash

IP_ADRESS=192.168.1.1
( ! ping -c1 $IP_ADRESS >/dev/null 2>&1 ) && service network restart >/dev/null 2>&1

will that be ok to run or will it become a resource hog?

Hi Gareth

As an approach, (just like volkswagner) I'd recommend you follow the trail of "auto wlan0" in /etc/network/interfaces rather than recreating it.  This will certainly bring your network back up when your server restarts; are router restarts common for you?

Kind regards.

Jonathan.

---

### Post by Gareth_2007 on 2011-10-01
with the fresh install of server 11.04 the wireless was configured on install and it does connect on boot, but unfortunately some times the router crashed or the signal can drop for what ever reason and it doeent automatically reconnect unless rebooted or told to via cli. but thats no good if i'm else where. i know its a silly idea having a server using wireless but unfortunately its the way it has to be at the moment.

---

### Post by Jonathan L on 2011-10-01
> **Gareth_2007 said:**
> with the fresh install of server 11.04 the wireless was configured on install and it does connect on boot, but unfortunately some times the router crashed or the signal can drop for what ever reason and it doeent automatically reconnect unless rebooted or told to via cli. but thats no good if i'm else where. i know its a silly idea having a server using wireless but unfortunately its the way it has to be at the moment.

Hi Again

I'd take a look at ifplugd, which seems to address this kind of issue.  I'm afraid I've no experience of it myself, but a quick read seems to suggest it's what would help you.

Kind regards
Jonathan.

---

