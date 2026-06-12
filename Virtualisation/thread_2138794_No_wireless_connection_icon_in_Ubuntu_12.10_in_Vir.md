---
title: "No wireless connection icon in Ubuntu 12.10 in Virtualbox"
date: 2013-04-25
forum: Virtualisation
---

### Post by groundnut on 2013-04-25
I am using Virtualbox with Ubuntu 12.10 both as a host and as a guest os.
The guest Ubuntu does have an icon for wired connections.
However there is no icon for wireless connections.

How can I connect wirelessly?


As it turned out later in this thread I don't need a wireless icon. A wired icon is enough.
Probably my problem has occurred because my host machine is connected via WiFi.
To remedy that I changed the network setting NAT into Network Bridge Adapter.

---

### Post by Bucky Ball on 2013-04-25
*Thread moved to **Virtualisation**.*

---

### Post by groundnut on 2013-04-26
Found the answer!

In the network settings of the VM I changed NAT to Network Bridge Adapter

---

### Post by Bucky Ball on 2013-04-26
Excellent news. To mark thread as solved and help others please edit first post, click Go Advanced and change the [ubuntu] prefix to [solved]. Cheers.

---

