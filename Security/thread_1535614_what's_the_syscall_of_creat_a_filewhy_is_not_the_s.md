---
title: "what's the syscall of creat a file?why is not the sys_creat?"
date: 2010-07-21
forum: Security
---

### Post by zonelight on 2010-07-21
Hi,recently i did a work of intercept syscalls,but i found that i could not catch the syscall of creat a file(whatever use the "touch" command or mouse by right-click in GUI).
This is the strace report when i use the "touch" command to creat a file:

% time     seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
100.00    0.000046           2        26           mmap2
  0.00    0.000000           0         5           read
  0.00    0.000000           0        33        13 open
  0.00    0.000000           0        23           close
  0.00    0.000000           0         1           execve
  0.00    0.000000           0         5         5 access
  0.00    0.000000           0         3           brk
  0.00    0.000000           0         1           dup2
  0.00    0.000000           0         2           munmap
  0.00    0.000000           0         1           uname
  0.00    0.000000           0         6           mprotect
  0.00    0.000000           0         2           rt_sigaction
  0.00    0.000000           0         1           rt_sigprocmask
  0.00    0.000000           0         1           getrlimit
  0.00    0.000000           0        19           fstat64
  0.00    0.000000           0         3         1 futex
  0.00    0.000000           0         1           set_thread_area
  0.00    0.000000           0         1           set_tid_address
  0.00    0.000000           0         1           set_robust_list
  0.00    0.000000           0         1           utimensat
------ ----------- ----------- --------- --------- ----------------
100.00    0.000046                   136        19 total

No creat,why?

---

