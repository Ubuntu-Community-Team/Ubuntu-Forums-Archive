---
title: "mdadm RAID 5 issue"
date: 2012-10-19
forum: Server Platforms
---

### Post by ranger3 on 2012-10-19
Hello,

I have just upgraded my server to Ubuntu 12.04.1 LTS and created a 4 disk RAID 5 array using mdadm (separate from the system disk).

Everything works well - except for one issue. The status of the raid changes continuously from 'clean' to 'active'  every 5 seconds or so, and the drive status LED blinks accordingly.

Each individual drive shows 'active - sync'.

Any suggestions?

---

### Post by Drew Woodard on 2012-10-20
Clean and active and normal healthy states for the array to be in.
The state of "active" means there is current or pending disk io (reading/writing). "Clean" means nothing is going on at the moment.

[http://www.kernel.org/doc/Documentation/md.txt](http://www.kernel.org/doc/Documentation/md.txt)

---

