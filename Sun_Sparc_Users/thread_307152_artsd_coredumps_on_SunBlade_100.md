---
title: "artsd coredumps on SunBlade 100"
date: 2006-11-26
forum: Sun Sparc Users
---

### Post by pakman on 2006-11-26
Hi all,

I cannot get artsd to start (dapper, on a sunblade 100). Does anyone have any tips? Audio in general seems to work (I can play a CD, and play a WAV file using aplay).

Trying 
```
artsd -l0 -A
```
gives:
```
artsd version is 1.5.2
Bus error (core dumped)
```

The gdb trace from the core file is:

```
#0  0xf74850b8 in pthread_cond_init@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
(gdb) where
#0  0xf74850b8 in pthread_cond_init@@GLIBC_2.3.2 () from /lib/libpthread.so.0
#1  0xf7aee07c in pthread_cond_init () from /lib/libc.so.6
#2  0xf7dae990 in _gsl_init_data_caches () from /usr/lib/libartsflow.so.1
#3  0xf7dbfb9c in gsl_init () from /usr/lib/libartsflow.so.1
#4  0xf7d90178 in Arts::StdFlowSystem::StdFlowSystem () from /usr/lib/libartsflow.so.1
#5  0xf7d9eb58 in Arts::SetFlowSystem::startup () from /usr/lib/libartsflow.so.1
#6  0xf7853150 in Arts::StartupManager::startup () from /usr/lib/libmcop.so.1
#7  0xf7879f4c in Arts::Dispatcher::Dispatcher () from /usr/lib/libmcop.so.1
#8  0x000239a0 in ?? ()
#9  0x000239a0 in ?? ()
Previous frame identical to this frame (corrupt stack?)
```

Many thanks for any suggestions,
P.

---

