---
title: "Network Interface"
date: 2009-04-25
forum: Server Platforms
---

### Post by midnightriderz on 2009-04-25
I am using Ubuntu 8.10 on a Compaq DL360 server. The server has two network interfaces. To do updates, I have to turn down eth0 and use eth1 for downloading updates. The last download I performed, when I brought eth0 back up, no one can connect to the server except users inside the building where the server resides. I have individuals outside the building using eth1 until I can determine what is wrong. Users outside the building are unable to ping the static IP address on eth0. I can ping that IP address since I sit in the building where the server resides.
 
I used ifconfig and ethtool to verify both ports are active, set at 100mbps. I noticed the speed was half duplex on both ports so I figure it's not a duplex mismatch.
 
Any suggestions would be appreciated. Thanks

---

### Post by HermanAB on 2009-04-25
You probably disabled IP forwarding.

---

