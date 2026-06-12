---
title: "Dansguardian is not  following Squid ACL rules"
date: 2014-11-05
forum: Server Platforms
---

### Post by sububtu on 2014-11-05
Im having squid and dansguardian running successfully. But I had noticed that my squid acl rules are not working correctly.
Here is the scenario::
Server 192.168.1.1
Port:3128

Dansguardian port:8080
I hav some acl rules ::
acl internet_center 192.168.1.0/24
acl staff 192.168.2.0/24
acl hostel 192.168.3.0/24


And a time restriction entry meant for hostel (from 16:00 to 21:00 hrs)

The web content filtering is working fine with dansguardian using 8080 port.
But  the time restriction is not working as expected with this port.but when I change the port to 3128
The time restriction is working fine..
I dont know how to achieve this.. pls help

---

