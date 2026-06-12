---
title: "Mount iscsi on"
date: 2011-07-23
forum: Server Platforms
---

### Post by bakegoodz on 2011-07-23
How would I mount a iscsi volume on the Target (server) too?

 I would think people do this all the time with Clusters. I'm not using a cluster filesystem, I just mount it read-write on one system and read-only on the other. I do with VMware and AOE all the time, it is perfectly safe if you only mount with write access on 1 system or 1 VM.
I had everything working the way I wanted it with ATA over Ethernet, but then I discovered that iscsi was twice as fast and could max out 1 Gb Ethernet. So I converted everything over to iscsi. Then I discovered iscsi got exclusive access to the volume and wouldn't allow local mount access. I Googled how to do a localhost iscsi connection and I got several reports of it not working.  I can explain why I'm doing this if people get really hung up on why.

---

### Post by bakegoodz on 2011-07-24
OK, I figured it out. You can't do a normal local mount on a iscsi volume, but the Target can be an Initiator too. I made the mistake using 127.0.0.1 in the discover command, that somehow made two scsi volumes show up for the one LUN. I wasn't sure how to fix it so I purge the open-scsi package and started over with the normal interface IP address. It works great now, and has the same great speed with the same LUN mounted read-only on one system and mounted read-write on the other. I don't what speed issue is with AOE.

---

