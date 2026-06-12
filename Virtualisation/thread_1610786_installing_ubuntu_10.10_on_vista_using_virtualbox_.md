---
title: "installing ubuntu 10.10 on vista using virtualbox 3.2.10"
date: 2010-11-01
forum: Virtualisation
---

### Post by spring07 on 2010-11-01
Hi,

I am trying to install ubuntu 10.10 using virtualbox 3.2.10.66523 on vista homepremium.

While installing it shows following error and hangs afterwhich i need to manually close the virtualbox window.

Error:
Kernel panic - not syncing: Attempted to kill init.

Pid: 1, comm: run init Not tainted 2.62.35 -22 -generic #33-ubuntu
call trace:
? print K+ 0x2d / 0x35
panic + 0x5a/0xd2
forget_original_parent+0x2e4/0x2f0
? call_rcu+0xd/0x10
exit_notify + 0x13/0x170
do_exit + 0x17c /0x340
? redirected _tty_write +0x0 /0x90
sys_exit +0x18/0x20
syscall _call +0x7/0xb

could someone please throw some light on this? 

Thanks in advance.

---

