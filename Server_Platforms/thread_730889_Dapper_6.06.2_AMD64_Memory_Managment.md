---
title: "Dapper 6.06.2 AMD64 Memory Managment"
date: 2008-03-21
forum: Server Platforms
---

### Post by ScatterBrain on 2008-03-21
I just upgraded a Dell Poweredge 1950 running Dapper 6.06.2 AMD64 from 4GB of RAM to 8GB. I did this because the machine is running vmWare Server 1.04 with 4 virtual machines which was comsuming all of the host's RAM and actually made it SWAP a bit.
 
So after installing the RAM, booting the hosts and starting all of the guests, I'm *very* shocked to see the host only consuming a bit over 1GB of RAM.
 
Here's a snapshot of the top lines in TOP:
 
```
top - 11:27:24 up 15 min,  1 user,  load average: 0.12, 0.44, 0.35
Tasks: 103 total,   1 running, 102 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0% us,  0.0% sy,  0.0% ni, 100.0% id,  0.0% wa,  0.0% hi,  0.0% si
[COLOR=red]Mem:   8179832k total,  1116124k used,  7063708k free,    11132k buffers[/COLOR]
Swap:  3911788k total,        0k used,  3911788k free,   914572k cached
```
 
The guests are working with the same load as before. In fact, I actually bumped the available RAM on a per-machine basis up a bit. And now the host only needs 1GB instead of 4GB to run?
 
The only thing I can think of is something going on with the memory management scheme in the kernel when a machine has 4GB or less. That or vmWare is doing something special now that it has the additional RAM.
 
**Can somone explain it?**

---

### Post by ScatterBrain on 2008-03-24
Anyone???

*BUMP*

---

