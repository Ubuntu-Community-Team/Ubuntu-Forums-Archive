---
title: "Cassandra node seems to freeze after some period of time"
date: 2012-10-29
forum: Server Platforms
---

### Post by Crafty Kisses on 2012-10-29
Hey guys, so basically my node freezes (using Cassandra) after a period of time, I've checked the logs from GCInspector, GCInspector was indicating that ParNew + ConcurrentMarkSweep collectors were taking longer than 20 seconds which makes me think some of the JVM is being swapped out by the OS. Any thoughts?

---

