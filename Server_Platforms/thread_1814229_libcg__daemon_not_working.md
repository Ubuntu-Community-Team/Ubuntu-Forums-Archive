---
title: "libcg / daemon not working"
date: 2011-07-29
forum: Server Platforms
---

### Post by metalfan_ on 2011-07-29
hi,


i would like to test the following:
the process bzip2 for user testuser goes into the group cpuhungry
the group is only allowed to use core 1, not core 0.

```

/etc/cgrules.conf
testuser:bzip2   cpuset   cpuhungry/;


/etc/cgconfig.conf
mount {
   cpuset = /mnt/cgroups/cpuset;
}

group cpuhungry {
   cpuset {
       cpuset.cpus = 1
   }
}

```


first, a question: why do cpu/cpuset/memory mounts not show up in mount?


ive tried the init skript some times, but i guess it is broken.
looks like you need to run 
```

cgconfigparser -l /etc/cgconfig.conf

```
to setup the mounts in the first place, the init script misses this step.

starting the daemon via:
```

sudo cgrulesengd -d

```

results in:
```

CGroup Rules Engine Daemon log started
Current time: Fri Jul 29 11:32:53 2011

Opened log file: -, log facility: 0, log level: 7
Proceeding with PID 9527
Rule: testuser:bzip2
  UID: 1000
  GID: N/A
  DEST: cpuhungry/
  CONTROLLERS:
    cpuset

Started the CGroup Rules Engine Daemon.
.
.
.
Cgroup change for PID: 9528, UID: 1000, GID: 1000, PROCNAME: /bin/bzip2 FAILED! (Error Code: 50016)
GID Event: PID = 1950, tGID = 1950, rGID = 0, eGID = 122

```

the error code 50016 is of course not documented nor does something pop up in a google search.

any ideas how to fix this?

---

