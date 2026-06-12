---
title: "ncpfs problem ubuntu 10.04"
date: 2012-05-18
forum: Server Platforms
---

### Post by arestas on 2012-05-18
Hey, hey,

I have a Ubuntu Server x86_64 10.04 kernel 2.6.32-28-server. On him i have a few novell mounts made with ncpfs (2.2.6-7).
The problem im encountering is that one of the mounts hangs for some reason and i cant do an ls inside that mount cause it freezes the console from where im doing it and i cant kill that process. 
i would like to know if there`s a way to know whats happening since the logs don't help me much... (Will post syslog anyway)

Call Trace:
[<ffffffff8155a367>] __mutex_lock_slowpath+0x107/0x190
[<ffffffff81559d63>] mutex_lock+0x23/0x50
[<ffffffff8114dfbe>] real_lookup+0x3e/0x160
[<ffffffff81150008>] do_lookup+0xb8/0xf0
[<ffffffff81150b35>] __link_path_walk+0x765/0xf80
[<ffffffff811de3ef>] ? ext4_dirty_inode+0x4f/0x60
[<ffffffff8155b5ce>] ? _spin_lock+0xe/0x20
[<ffffffff81150a03>] __link_path_walk+0x633/0xf80
[<ffffffff8155b5ce>] ? _spin_lock+0xe/0x20
[<ffffffff811515ca>] path_walk+0x6a/0xe0
[<ffffffff8115179b>] do_path_lookup+0x5b/0xa0
[<ffffffff81152467>] user_path_at+0x57/0xa0
[<ffffffff8155b799>] ? _spin_unlock_bh+0x19/0x20
[<ffffffff8146388b>] ? sys_recvfrom+0x16b/0x180
[<ffffffff81148b8c>] vfs_fstatat+0x3c/0x80
[<ffffffff81148cfb>] vfs_stat+0x1b/0x20
[<ffffffff81148d24>] sys_newstat+0x24/0x50
[<ffffffff810121b2>] system_call_fastpath+0x16/0x1b


Tks in advance

:guitar:

---

