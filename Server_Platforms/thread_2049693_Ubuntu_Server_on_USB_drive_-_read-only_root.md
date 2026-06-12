---
title: "Ubuntu Server on USB drive - read-only root"
date: 2012-08-29
forum: Server Platforms
---

### Post by richbayliss on 2012-08-29
Guys.

I haven't posted here in a long while - so please excuse any forum faux pas :)

I am setting up a series of machines to run as a MongoDB pool - one master, multiple replicated slaves. As such, I want to have a simple Ubuntu 12.04 server install - as small as possible, without getting silly - and a standard MongoDB install on that. I would like to make the whole thing run from a USB flash drive in Read-Only mode to preserve the drives integrity over time, and I will use a fixed HDD to store my MongoDB data. I would also like a seperate partition to store any configuration files on - maybe mount this using UnionFS/AuFS over the top of the R/O root...?

Does anybody know of any recent tutorials on creating a Read-Only Ubuntu install?

---

### Post by richbayliss on 2012-08-29
I worked it out people - sorry to bother you all :)

I used the following article - [https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash](https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash)

And you will need the "aa-complain" mechanism to make DHCP work on 12.04

Peace out!

---

