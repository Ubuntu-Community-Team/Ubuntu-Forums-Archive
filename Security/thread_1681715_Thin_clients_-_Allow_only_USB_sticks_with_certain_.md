---
title: "Thin clients - Allow only USB sticks with certain serial number"
date: 2011-02-04
forum: Security
---

### Post by thade on 2011-02-04
Hi,
I am currently intall a LTSP server with about 10 clients. I'm using as a server Ubuntu 10.04 LTS. Everything works without problems. Now I would like to restrict the thin clients in the use of USB storage media. I try to use udev. On the thin clients a USB stick is mounted as ltspfs. I have allowed on the clients with LOCALEV = True, the use of local storage media. When I plug in a stick to the thin client that will be mounted automatically. I would like to prevent from any auto mount up on sticks with a specific serial number. Does anyone have any idea how I could do this best? Because I get the point to udev not. I also have the udev.rules in / etc experimented / udev / rules.d. But the stick is still mounted. Someone knows a solution?

Greetings
Rene

---

