---
title: "High Load Avg when CIFS Share unavailable"
date: 2012-04-17
forum: Server Platforms
---

### Post by simpic on 2012-04-17
Hi, 

I seem to be suffering from high load average when one of my shares that I connect to is not available due to the machine being powered off.

The drive is mounted in fstab like so...

```
//192.168.1.60/movies /mnt/windows_mount cifs rw,_netdev,credentials=/home/sp/.smbcredentials,uid=10000,gid=100 0 0
```

The load graph is attached.

Any ideas as to how I can sort this?

Regards, 

Simpic

---

### Post by Doug S on 2012-04-17
As a starting point, my suggestion is to use the "top" command to observe and identify the process(es) that are heavily using the system resources.
Attached is an example (I always type the "1" key in top to view each CPU), where the system load is shown as 1.77 (it is actually ~1.98, but the filter delay had not fully flushed when I took the screen shot) and you can see that two occurences of a program called "waiter" are taking a lot of cpu time.

---

### Post by simpic on 2012-04-17
Hi,

CPU is doing nothing whilst this is happening. I have run a few commands to investigate. I'll post them up tomorrow. The results indicated a CIFS process that was a problem which lead me to investigate my shares. That in turn lead to the correlation of the issue occurring when one of the shares is not available. Namely the one shown above. 

Command...

top -b -n 1 | awk '{if (NR <=7) print; else if ($8 == "D") {print; count++} } END {print "Total status D (I/O wait probably): "count}' > topsave.txt

Is the a CIFS issue on Ubuntu or something about the way I have mounted it?

Regards,

Simpic

---

