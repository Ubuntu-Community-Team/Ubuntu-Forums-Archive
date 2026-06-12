---
title: "ubuntu 10.x preseed trouble with choose_interface"
date: 2011-03-31
forum: Server Platforms
---

### Post by eclay on 2011-03-31
Hello,

I've been trying to get a preseed install of ubuntu 10.04 and 10.10 where I specify which nic to use during the install using the following preseed line.

d-i netcfg/choose_interface select eth0
[LEFT]When the install starts it prompts me to choose an interface.  If I hit 
enter on eth0 it will sometimes fail to get a dhcp address on the first 
attempt then succeeds.  Other times after hiting enter while eth0 is 
selected it continues the automated install as expected.  Either way It
never automatically continues the install.

The system is setup with both NICs connected to the network.  DHCP 
configured on the subnet that eth0 is connected to.

Any ideas on how to troubleshoot or solve this problem would be greatly
appreciated.
[/LEFT]

---

