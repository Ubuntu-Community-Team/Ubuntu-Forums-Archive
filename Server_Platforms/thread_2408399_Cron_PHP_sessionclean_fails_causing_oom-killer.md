---
title: "Cron PHP sessionclean fails causing oom-killer"
date: 2018-12-18
forum: Server Platforms
---

### Post by travisbotello on 2018-12-18
We are running multiple Ubuntu 18.04.1 servers with the same LEMP setup. Over the weekend one of our machines ran out of memory and locked up. We had to manually reboot to get it working again. In the syslog I can see that around 40 hours before the system collapsed cron PHP sessionclean started causing kernel errors:

```

Dec 15 22:09:01 server CRON[32294]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi)
Dec 15 22:09:01 server systemd[1]: Starting Clean php session files...
Dec 15 22:09:01 server systemd[1]: Started Clean php session files.

Dec 15 23:09:01 server systemd[1]: Starting Clean php session files...
Dec 15 23:09:01 server CRON[506]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi)
Dec 15 23:12:46 server kernel: [2456147.547283] INFO: task sessionclean:479 blocked for more than 120 seconds.
Dec 15 23:12:46 server kernel: [2456147.548953]       Not tainted 4.18.16-x86_64-linode118 #1
Dec 15 23:12:46 server kernel: [2456147.550155] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Dec 15 23:12:46 server kernel: [2456147.552176] sessionclean    D    0   479      1 0x80000002
Dec 15 23:12:46 server kernel: [2456147.552179] Call Trace:
Dec 15 23:12:46 server kernel: [2456147.552212]  ? __schedule+0x3be/0x8b0
Dec 15 23:12:46 server kernel: [2456147.552216]  ? uncharge_batch+0x2e9/0x3a0
Dec 15 23:12:46 server kernel: [2456147.552218]  schedule+0x3c/0x90
Dec 15 23:12:46 server kernel: [2456147.552220]  schedule_timeout+0x1f7/0x420
Dec 15 23:12:46 server kernel: [2456147.552225]  ? release_pages+0x2d2/0x3e0
Dec 15 23:12:46 server kernel: [2456147.552226]  wait_for_common+0xcd/0x190
Dec 15 23:12:46 server kernel: [2456147.552230]  ? wake_up_q+0x60/0x60
Dec 15 23:12:46 server kernel: [2456147.552235]  __wait_rcu_gp+0x11b/0x150
Dec 15 23:12:46 server kernel: [2456147.552238]  synchronize_rcu+0x7c/0x90
Dec 15 23:12:46 server kernel: [2456147.552241]  ? kfree_call_rcu+0x20/0x20
Dec 15 23:12:46 server kernel: [2456147.552243]  ? __bpf_trace_rcu_utilization+0x10/0x10
Dec 15 23:12:46 server kernel: [2456147.552246]  namespace_unlock+0x67/0x80
Dec 15 23:12:46 server kernel: [2456147.552249]  put_mnt_ns+0x1c/0x30
Dec 15 23:12:46 server kernel: [2456147.552253]  free_nsproxy+0x17/0x90
Dec 15 23:12:46 server kernel: [2456147.552256]  do_exit+0x3f0/0xc40
Dec 15 23:12:46 server kernel: [2456147.552259]  do_group_exit+0x39/0xb0
Dec 15 23:12:46 server kernel: [2456147.552261]  __x64_sys_exit_group+0x14/0x20
Dec 15 23:12:46 server kernel: [2456147.552265]  do_syscall_64+0x5b/0x190
Dec 15 23:12:46 server kernel: [2456147.552269]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
Dec 15 23:12:46 server kernel: [2456147.552272] RIP: 0033:0x7faf2120fe06
Dec 15 23:12:46 server kernel: [2456147.552272] Code: Bad RIP value.
Dec 15 23:12:46 server kernel: [2456147.552279] RSP: 002b:00007ffda594cd08 EFLAGS: 00000246 ORIG_RAX: 00000000000000e7
Dec 15 23:12:46 server kernel: [2456147.552281] RAX: ffffffffffffffda RBX: 0000000000000004 RCX: 00007faf2120fe06
Dec 15 23:12:46 server kernel: [2456147.552281] RDX: 0000000000000000 RSI: 000000000000003c RDI: 0000000000000000
Dec 15 23:12:46 server kernel: [2456147.552282] RBP: 0000556f16cd1a90 R08: 00000000000000e7 R09: ffffffffffffff80
Dec 15 23:12:46 server kernel: [2456147.552283] R10: 00007faf212c9cc0 R11: 0000000000000246 R12: 0000556f16cc0a20
Dec 15 23:12:46 server kernel: [2456147.552284] R13: 00007ffda594cff0 R14: 0000000000000000 R15: 0000000000000000

```

After that cron failed with:

```
Dec 16 14:25:01 server cron[644]: (CRON) error (can't fork)

```

By the end of the day our external backup service was no longer able to SSH into the machine but websites were still working fine until Monday morning everything went down. Syslog shows oom killer:

```
Dec 17 05:05:04 server kernel: [2563686.476314] systemd invoked oom-killer: gfp_mask=0x6200ca(GFP_HIGHUSER_MOVABLE), nodemask=(null), order=0, oom_score_adj=0
Dec 17 05:05:05 server kernel: [2563686.476319] systemd cpuset=/ mems_allowed=0

```

Any ideas on how to debug this/extract the root cause of this error. I'd like to make sure that this won't happen again since we are using the same setup on multiple machines. This being said we never had any similar issues in the past.

Timeline:

[COLOR=#333333][FONT=arial]12/15 23:12 => PHP Session cleanup task fails with kernel error[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]12/16 09:00 => Cron stopped working with " (CRON) error (can't fork)"[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]12/16 21:00 => Daily Backup service can't connnect via SSH[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]12/17 05:05 => Websites not working anymore (system invoking oom-killer)[/FONT][/COLOR]

---

