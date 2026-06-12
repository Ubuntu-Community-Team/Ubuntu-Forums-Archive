---
title: "blocked processes"
date: 2010-05-10
forum: Server Platforms
---

### Post by ub007 on 2010-05-10
my hp proliant DL185 server doesn't boot properly.

i've managed to capture blocked processes in kernel space  

>  SysRq -w

SysRq : Show Blocked State
f7ad1e40 00203082 f7853b90 e54af7f0 e54af948 cba30e00 00000001 00000020
e5ad2250 00000000 000000ff e5ad2250 00000000 00000000 00000000 7fffffff
e55afe00 e55afd44 e55afe04 c05ab1c5 256e2000 00000000 e56e2000 00000000
Call Trace:
[<c05ab1c5>] schedule_timeout+0x13/0x86
[<c05ab095>] wait_for_common+0xb9/0x103
[<c021a4b6>] default_wake_function+0x0/0x8
[<c0409473>] cciss_ioctl+0x6fb/0xd1e
[<c0207852>] read_tsc+0x6/0x22
[<c02335a6>] getnstimeofday+0x4a/0xca
[<c023618a>] tick_dev_program_event+0x1e/0x8c
[<c026c316>] dput+0x31/0xf7
[<c026570c>] __link_path_walk+0x9fd/0xb2b
[<c038442f>] blkdev_driver_ioctl+0x4b/0x5b
[<c054420b>] igmp_rcv+0x38f/0x496
[<c0384ad6>] blkdev_ioctl+0x697/0x6e5
[<c054420b>] igmp_rcv+0x38f/0x496
[<c054420b>] igmp_rcv+0x38f/0x496
[<c027e02d>] do_open+0x1d9/0x258
[<c027e21a>] blkdev_open+0x0/0x4d
[<c027e23f>] blkdev_open+0x25/0x4d
[<c025c3a5>] __dentry_open+0x13b/0x212
[<c025c498>] nameidata_to_filp+0x1c/0x2c
[<c02667c3>] do_filp_open+0x350/0x64d
[<c023786c>] do_futex+0x8a/0x6ee
[<c024feaa>] handle_mm_fault+0x4e0/0x4ea
[<c054420b>] igmp_rcv+0x38f/0x496
[<c027d871>] block_ioctl+0x13/0x16
[<c027d85e>] block_ioctl+0x0/0x16
[<c026744c>] vfs_ioctl+0x1c/0x5d
[<c02676c6>] do_vfs_ioctl+0x239/0x247
[<c025c203>] do_sys_open+0xae/0xb6
[<c0267715>] sys_ioctl+0x41/0x58
[<c0203759>] sysenter_do_call+0x12/0x25
[<c054420b>] igmp_rcv+0x38f/0x496 

can any kernel guru point me to whats faulty here???

Thanks in advance,
David

---

