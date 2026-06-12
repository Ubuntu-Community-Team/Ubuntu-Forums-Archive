---
title: "How to enable CONFIG_COMPAT on Ubuntu 16.04 LTS"
date: 2018-02-01
forum: Ubuntu, Linux and OS Chat
---

### Post by bhatja on 2018-02-01
Hi All,

We are using Ubuntu 16.04 LTS on 64 bit Linux. However our application is 32 bit application. I am facing issues when I am trying to use netlink socket to communicate with XFRM. struct msghdr is the structure used in sendmsg. This is 28 bytes in 32 bit application space and 56 bytes in 64 bit kernel space. While looking for the fix, I found that there compat layer already available. This can be enabled for CONFIG_COMPAT.  In our case this is not enabled. I wanted to know how to enable this option. We are using x86_64 platform.

Any help is well appreciated.

Regards
Jayalakshmi

---

### Post by coffeecat on 2018-02-01
Duplicate thread. Please do not post duplicates in different parts of the forum. And this is not the correct section for technical support.

Closed.

---

