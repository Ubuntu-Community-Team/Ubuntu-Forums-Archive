---
title: "sxid segmentation fault"
date: 2009-03-23
forum: Security
---

### Post by NickD-NLUG on 2009-03-23
If I run /usr/bin/sxid I get a segmentation fault.

If I run "strace /usr/bin/sxid" the program runs fine.

If I run "strace /etc/cron.daily/sxid" I get a segmentation fault:

rt_sigaction(SIGINT, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGINT, {0x40f810, ~[RTMIN RT_1], SA_RESTORER, 0x7f65e206e0a0}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL}, NULL, 8) = 0
read(10, "#!/bin/sh\n\nSXID_OPTS=\n\nif [ -x /"..., 8192) = 84
stat("/usr/bin/sxid", {st_mode=S_IFREG|0755, st_size=27792, ...}) = 0
geteuid()                               = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f65e25af770) = 2213
wait4(4294967295, [{WIFSIGNALED(s) && WTERMSIG(s) == SIGSEGV}], 0, NULL) = 2213
--- SIGCHLD (Child exited) @ 0 (0) ---
write(2, "Segmentation fault\n", 19Segmentation fault
)    = 19
read(10, "", 8192)                      = 0
exit_group(139)                         = ?

Any ideas where I should start with this one?

---

### Post by NickD-NLUG on 2009-05-16
Anyone?

I'd like to poke around with this a bit more before I submit it as a bug, especially as there seems to be a "sxid dumps on amd64" bug in there already...

---

### Post by sahabcse on 2009-05-16
Try below url this may be help

[http://sahabm.blogspot.com/2009/04/segmentation-fault-unable-to-login.html](http://sahabm.blogspot.com/2009/04/segmentation-fault-unable-to-login.html)

---

### Post by NickD-NLUG on 2009-06-10
> **sahabcse said:**
> Try below url this may be help

[http://sahabm.blogspot.com/2009/04/segmentation-fault-unable-to-login.html](http://sahabm.blogspot.com/2009/04/segmentation-fault-unable-to-login.html)

It doesn't.

It appears to be this problem...

[https://bugs.launchpad.net/ubuntu/+source/sxid/+bug/365940](https://bugs.launchpad.net/ubuntu/+source/sxid/+bug/365940)

---

