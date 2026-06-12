---
title: "Java consuming boatloads of resources"
date: 2015-06-17
forum: Server Platforms
---

### Post by Seawhy on 2015-06-17
Our main production server is now fully updated, as far as can be done with Ubuntu Server 12.04 LTS. We seem stable now, and haven't even had a hiccup in the past week since getting everything fixed up with our raid controller firmware. ([http://ubuntuforums.org/showthread.php?t=2281896](http://ubuntuforums.org/showthread.php?t=2281896))

We're now experiencing really high system load, and it looks like java is to blame. If we stop our services that run java, system load drops down below 1. As I write this, server has a 5 minute load average of 26.02 with java running.

This has only been a problem in the past week, since we brought everything current. Early this month, our load averages at the busiest times of the day might have reached 6 or 7. Now we're suffering.

Any tips on how to troubleshoot this?

---

