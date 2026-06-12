---
title: "ubuntu.datahop.it"
date: 2007-07-27
forum: Server Platforms
---

### Post by craigtyson on 2007-07-27
seems to be trying to connect to my laptop when I connect to the internet.

Firestarter reports 194.169.254.10 protocol TCP
on Ports
41984 
41939

the IP address resolves to ubuntu.datahop.it

First time I have seen it, is this a somthing I (we) should be worried about?

---

### Post by bmathis on 2007-07-27
its the update manager checking the Great Britain repositories... try the following: ```
ping -c 5 gb.archive.ubuntu.com
``` and you should see it resolve to the same IP and hostname.

---

