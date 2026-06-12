---
title: "Diagnose &quot;received packet with own address as source address&quot;"
date: 2017-10-24
forum: Server Platforms
---

### Post by iandickerson on 2017-10-24
[SIZE=3]Every few minutes I'm getting kernel messages
```
br1: received packet on eth4 with own address as source address (addr:##.##.##.##.##.##)
```
and intermittent poor network performance.

I thought there must be a loop but I don't see where.

This is my home office set up
[ATTACH=CONFIG]277244[/ATTACH]
[/SIZE][SIZE=4][SIZE=3]
The server is a Gateway GT350 F1 running Ubuntu 17.10
**br1** bridges a hardware port **eth4** and virtual ports for a couple of containers.
The IPMI management interface is on separate hardware that the server kernel doesn't see.

[LIST]
[*]I've run wireshark to look for these packets but I haven't seen anything with the same source and destination address, either IP or MAC.
[*]I've disabled lxd but that didn't help.
[*]Neither did turning on STP on **br1**&#8203;.
[/LIST]

Any advice for diagnosing this much appreciated.

[/SIZE]
[/SIZE]

---

