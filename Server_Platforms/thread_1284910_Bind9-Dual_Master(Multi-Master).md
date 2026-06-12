---
title: "Bind9-Dual Master(Multi-Master)"
date: 2009-10-07
forum: Server Platforms
---

### Post by saggy00 on 2009-10-07
Hello everyone. 
I Have setup a master dns(bind). The server works fine,but i want to be sure that if it fails, there would be a second dns server to continue support the system. So i want to have 2 master dns servers and when the one goes down, the second will continue to serve. The servers will be in different locations(2 km away-not in the same subnet). 

The problem is that building a slave dns will support me until i finally fix the master.

BUT i want the second dns to be capable of making new records.
It will be like having a clone of the first master(any change to the first will be transfered to the second and if one goes down, i can create new records in the working server).

Is that possible and how can i do this???

Thanx in advance!

---

