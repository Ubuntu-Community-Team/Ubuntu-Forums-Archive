---
title: "Ping for No reason"
date: 2010-01-29
forum: Security
---

### Post by dashpilot79 on 2010-01-29
I was wondering is there any thing that would be running on a server edition that would be pinging items on its own?

The reason I ask this is, the server doesn't ever have any one log on to it but myself and there isnt even a remote access avenue built into it and while i was checking the logs I noticed that that the server sent out two pings to computers on my internal network while I was asleep.  

Was curious is there is something that would be generating it on its own or evidence that some how the server is being compromised.


Thank You,

---

### Post by cariboo on 2010-01-29
That's normal network activity, the server is just checking to see which computers are alive on the network. You can use wireshark to see what kind of packages are sent back and forth, when there is no other activity.

---

### Post by myth1914 on 2010-01-29
Beyond normal discovery, things like backuppc or similar apps will query to log what time machines are on the network and when it can best schedule backups.

Backuppc is not installed by default, but to provide you with an example/direction

---

