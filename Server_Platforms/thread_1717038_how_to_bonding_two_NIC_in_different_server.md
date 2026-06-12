---
title: "how to bonding two NIC in different server?"
date: 2011-03-29
forum: Server Platforms
---

### Post by gendit on 2011-03-29
i planning to install two transparent proxy server in a LAN.the two transparent will be install ubuntu server (operating system) and squid as transparent software.so i will have two server that will connect to one LAN..how can i bond the two NIC at the two server to be one??..so that i can provide DHCP in the LAN without any ip address conflict??..can you give any suggestons or it is posibble?..please advice

regards 
gendit

---

### Post by rokabear on 2011-04-21
Do you want one server to be a failover server for the other?  That is one server will be active and the other will be a backup.  Then if the active goes offline the backup will start advertising the mac and IP of the main box?  

This is a high availability scenario.  Take a look at [http://www.linux-ha.org/](http://www.linux-ha.org/) for the linux high availability docs, and look at setting up heartbeat.
This will not bond your nics on the two servers but I think this is what you are asking for.


If you want to bond two nics on the same server in ubuntu look at [https://clients.rokabear.com/knowledgebase.php?action=displayarticle&id=1](https://clients.rokabear.com/knowledgebase.php?action=displayarticle&id=1).

With intel cards we have had good luck with mode 1 (failover) or mode 5 (requests in on active, and send response out both cards.).   There are other modes available that may meet your needs more.

Too if you are looking for the transparent proxies to communicate together to help each other out, check out [http://en.wikipedia.org/wiki/Internet_Cache_Protocol](http://en.wikipedia.org/wiki/Internet_Cache_Protocol).

---

