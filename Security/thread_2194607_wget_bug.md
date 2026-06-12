---
title: "wget bug"
date: 2013-12-19
forum: Security
---

### Post by heap1 on 2013-12-19
Hi,

I downloaded directory with few files, one of them was 18G, then I interruped wget download. After a while when my inet connection get restored I wanted to continue to download missing files so I typed wget with -c opt.

Wget was checking previously downloaded files and while checking file with size 18G it crashed. Strace output is bellow. Do you have any idea?



Thanks


Strace output:


    The file is already fully retrieved; nothing to do.

wget: memory exhausted
[{WIFEXITED(s) && WEXITSTATUS(s) == 1}], 0, NULL) = 7346
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, 0x7fff96f1aa58, WNOHANG, NULL) = -1 ECHILD (No child processes)
rt_sigreturn(0xffffffffffffffff)        = 0
rt_sigaction(SIGINT, {SIG_DFL, [], SA_RESTORER, 0x7fb9cd27b4a0}, {0x43f1e0, [], SA_RESTORER, 0x7fb9cd27b4a0}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
read(255, "", 272)                      = 0
exit_group(1)                           = ?

---

### Post by Lars Noodén on 2013-12-19
If it's repeatable, then you might file a bug with ubuntu-bug.

```

ubuntu-bug wget

```

If you are looking for a work-around then you might look at curl.

---

### Post by tgalati4 on 2013-12-20
Watch your RAM and swap using *free* while downloading large wget jobs.  See if it is repeatable.  My guess is you ran out of RAM and swap and init had no choice but to kill it.

---

