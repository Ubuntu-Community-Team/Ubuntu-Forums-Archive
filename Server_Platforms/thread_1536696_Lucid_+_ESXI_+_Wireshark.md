---
title: "Lucid + ESXI + Wireshark"
date: 2010-07-22
forum: Server Platforms
---

### Post by terazen on 2010-07-22
I have an esxi server at a remote site that I installed lucid desktop on for the purpose of using wireshark on an otherwise unused physical nic.  For whatever reason all I'm seeing in wireshark are broadcasts, no unicasts.  Does anyone have experience with this?  I assume the virtual nic is causing the issue, but I'm not sure how to proceed.

---

### Post by terazen on 2010-07-22
Promiscuous mode was turned off by default.
[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1004099](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1004099)

Now I get to be lazier and have to leave my desk even less.:D

---

