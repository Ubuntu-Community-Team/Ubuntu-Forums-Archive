---
title: "Git kernel (no YAMA) == can't strace"
date: 2011-10-27
forum: Security
---

### Post by Embedded Linux Guy on 2011-10-27
Hi folks, I am using 3.1 kernel built directly from Linus' git. It works great EXCEPT I can't use strace as provided by 4.5.20-2ubuntu2. The problem is this strace binary refuses to run unless kernel.yama.ptrace_scope=0 and I don't have this sysctl variable!

```
$ strings /usr/bin/strace
attach: ptrace(PTRACE_ATTACH, ...)
Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf

```

So:rolleyes: do I understand correctly that the Ubuntu userspace cannot be used with a stock kernel? Is it the case that I now need to build my own strace from source, or try to use one from another distro such as debian unstable? Inquiring minds want to know!

Thanks in advance.

---

