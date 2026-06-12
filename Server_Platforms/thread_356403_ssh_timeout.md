---
title: "ssh timeout"
date: 2007-02-08
forum: Server Platforms
---

### Post by Aberrix on 2007-02-08
how can I increase the ssh timeout time? my sessions seem to timeout within just a couple minutes and its rather annoying. Thanks in advance.

---

### Post by jtc on 2007-02-08
Try looking at these two sshd settings.

ClientAliveInterval and ClientAliveCountMax

---

### Post by toddpedlar on 2007-08-16
> **jtc said:**
> Try looking at these two sshd settings.

ClientAliveInterval and ClientAliveCountMax

Those are host-side, though, right?  I assume this is the only way to solve the problem.  I'm having the same timeout issue ssh'ing to particular remote hosts from my machines. 

Todd

---

