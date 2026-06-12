---
title: "multiple ip's, same interface"
date: 2007-07-26
forum: Server Platforms
---

### Post by tocleora on 2007-07-26
Can someone tell me how to add an additional ip to eth0?  I have two servers that have that but I didn't set it up (and don't have access to the person that did) and I need to do it to a 3rd server. Thanks in advance.

---

### Post by jtc on 2007-07-26
Assuming your real interface is eth0 your virtual interfaces will be named eth0:N (eth0:0, eth0:1, etc)

You set them up basicly the same way you as real interfaces, ie by using ifconfig or by defining them in /etc/network/interfaces

---

