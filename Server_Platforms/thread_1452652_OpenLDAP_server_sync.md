---
title: "OpenLDAP server sync"
date: 2010-04-12
forum: Server Platforms
---

### Post by vdpollm on 2010-04-12
Hi there,

I followed this howto:
[https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html)

the part in question is: LDAP Replication.

I originally had 3 servers that i did the n-way sync with, i.e. server1, server2 and server4. the syncing worked well, and i was happy. however, i kinda broke server2, and had to kill it.

I redid server2 and followed the above guide but can't get sync to work. how do i remove reference to this in config, etc. so that i can start over, or how do i remove sync repl from all the servers, and then start over, with out loosing my data from server1 as this is my pri ldap server?

regards
Marc

---

### Post by vdpollm on 2010-04-13
Or if somebody could point me in the right direction to go an read up on how to do this, i will appreciate it.

regards

Marc

---

