---
title: "Openstack Compute-node down in Ubuntu"
date: 2011-11-17
forum: Server Platforms
---

### Post by mclok on 2011-11-17
The server which is installed **_one of compute-node of Openstac_**k, it was down and cannot be boot into Ubuntu.  The following messages which captured from the screen are:

-init: /sbin/init: I/O error
kernel panic - not syncing: attempted to kill init!
Pid: 1, com: run-init Not tainted 2.6.35-22-server #35-Ubuntu
Call Trace:
[<ffffffff8159baf6>] panic+0x90/0x111
[<ffffffff810637ed>]forget_original_parent+0x33d/0x350
[<ffffffff81062c14>]? put_files_struct+0xc4/0xf0
[<ffffffff8106381b>]exit_notify+0x1b/0x190
[<ffffffff81065125>]do_exit+0x1c5/0x3f0
[<ffffffff81153711>]? sys_write+0+51/0x80
[<ffffffff81065457>]sys_exit+0x17/0x20
[<ffffffff8100a0f2>]system_call_fastpath+0x16/0x1b

Does anyone understand the above error messages?
Thank you!!

---

