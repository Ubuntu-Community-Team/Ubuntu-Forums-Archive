---
title: "6 instances of apache2 running??"
date: 2008-08-10
forum: Server Platforms
---

### Post by itzfritz on 2008-08-10
I have 6 instances of apache2 running on my ubuntu box; 1 as root and 5 as www-data.  Does anyone know why this might be? Is there a fundamental concept that I am missing (i.e. 'these are child processes, dummy') or is there something in my apache configuration that specifies this?

Thanks!

---

### Post by SpaceTeddy on 2008-08-11
you should have a programm calles "pstree" installed. Run that one see where the apache processes go. I've just checked on my own servers, and they all show the same behaviour. On all servers the www-data processes are the spawned children, while the root process seems to be the master.

Also, this would make sense, as a non-root user cannot open port 80 (it is privileged). So holding the initial process as root, and spawning a few children to handle requests (which are not degraded to www-data because of security) would make perfect sense to me.

hope it helps :)

---

### Post by dmizer on 2008-08-11
Moved to Server platforms.

This is normal behavior.  Each Apache process spawns a new PID.  Just like what happens if you open several terminals.  The root owned PID is the actual server, and the www-data owned PIDs are the child processes.

---

