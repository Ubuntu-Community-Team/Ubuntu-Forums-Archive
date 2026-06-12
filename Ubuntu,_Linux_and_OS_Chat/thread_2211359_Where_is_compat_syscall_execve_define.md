---
title: "Where is compat_syscall_execve define?"
date: 2014-03-15
forum: Ubuntu, Linux and OS Chat
---

### Post by sharyshary on 2014-03-15
Hi,

I am looking to find out where are the system calls define in the source code? I have found out that if I search SYSCALL_DEFINE%d or COMPAT_SYSCALL_DEFINE%d macro then I can find out the definition of system calls in the kernel. However, in some cases, in Ubuntu 14.04, I could not find out the COMPAT_SYSCALL_DEFINE for some system calls. For example, compat_syscall_execve,compat_sys_sendmsg, compat_sys_reccvfrom and so on. I am wondering how can I locate the definition of these compat system calls in the source code?

Regards,
Shary

---

