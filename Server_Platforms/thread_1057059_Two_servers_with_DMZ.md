---
title: "Two servers with DMZ?"
date: 2009-02-01
forum: Server Platforms
---

### Post by linuxisevolution on 2009-02-01
I have an apache server that is running, serving the websites in my signature below. The problem is, I need to setup a second server, that will serve some different things. The first server is connected to the world via DMZ ( all ports are open ). The problem is, I need to setup this second server, but I can't figure out how :( . If I set the mac to use port 70 and try [http://24.3.84.251:70/](http://24.3.84.251:70/) it doesn't work... How do I make both machines accessible to the network by using the same WAN? Thanks, I hope your up for a challenge :D

---

### Post by skunkbad on 2009-02-01
If you took both servers off DMZ, and instead port forwarded each port that was needed to each server, then server #1 and #2 could have their own specific ports forwarded, and there would be no same-port # conflicts.

---

