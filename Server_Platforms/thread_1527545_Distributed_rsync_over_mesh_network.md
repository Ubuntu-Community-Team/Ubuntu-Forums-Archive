---
title: "Distributed rsync over mesh network"
date: 2010-07-09
forum: Server Platforms
---

### Post by genjix on 2010-07-09
A bunch of hosts all connected to each other.

I'd like to have a directory where a group of hosts can dump files and all access, synchronising with each other their changes automatically and transparent to the user.

How can I have it so that rsync updates both ways?

* host A asks host B for a list of files, modification dates, checksums
* then applies the rules to select which files it will fetch from B
    --> if A owns the file then do not get modifications from B
    --> files differ, then select newer file
* then fetches them
* and so on for each host...

Any ideas?

---

