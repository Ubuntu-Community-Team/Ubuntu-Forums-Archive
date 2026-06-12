---
title: "VFS: file-max limit 205258 reached"
date: 2007-03-28
forum: Server Platforms
---

### Post by Chronus on 2007-03-28
I've recently provisioned a new server for the task of running a few Counter-Strike: Source game servers.

I did a base install of Dapper Drake, installed the CS:S server, did a vanilla config and opened it for testing. Aside from the CS:S server, *nothing* else was running on the box.

After a few hours, I get the following error when attemping to login via SSH:
/bin/bash: Too many open files in system

Hit the reset button on the server, reboots and I explore the syslogs. Up until the time of reboot, the logs were full of this message:
Mar 27 16:20:29 csbox09 kernel: [43646739.160000] VFS: file-max limit 205258 reached
Mar 27 16:20:31 csbox09 kernel: [43646740.810000] VFS: file-max limit 205258 reached
Mar 27 16:20:31 csbox09 kernel: [43646741.190000] VFS: file-max limit 205258 reached
Mar 27 16:20:34 csbox09 kernel: [43646744.260000] VFS: file-max limit 205258 reached

There's nothing else of note in the logs apart from cron.

Does anyone have any thoughts on what could be causing this issue, and how to resolve it? It doesn't appear to be a problem with the CS server, since I very much doubt this would open 205,000+ files.

Thanks,
-C.

---

### Post by Chronus on 2007-03-29
No one had this issue before? :(

-C.

---

### Post by Mr. C. on 2007-03-29
The *nix kernels have limits as to the number of files a process or the system as a whole may have open.

Either the program is leaking file descriptors, or you will need to increase the number of file descriptors for the process / system.

That's a lot of file descriptors - I suspect a leak (bug in the source, not closing some file it has opened).  If so, someone will have to fix the bug, or the CS server needs to be restarted.

MrC

---

