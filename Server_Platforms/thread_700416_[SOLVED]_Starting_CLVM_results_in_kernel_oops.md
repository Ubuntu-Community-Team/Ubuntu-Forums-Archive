---
title: "[SOLVED] Starting CLVM results in kernel oops"
date: 2008-02-18
forum: Server Platforms
---

### Post by drzero on 2008-02-18
I am setting up a cluster which will use DRBD in an active/active configuration and CLVM to divide up the block device in a cluster aware fashion. I have a fairly minimal gutsy server installation on both machines with drbd8, heartbeat and clvm installed. I have heartbeat working with a single fallover IP and a working cluster.conf for cman (which clvm uses). The problem is that when I try to start clvm on either machine I get the following error:

```
root@storage1:~# /etc/init.d/clvm start
Starting Cluster LVM Daemon clvmd failed in initialisation
 storage1 kernel: [  144.749683] Oops: 0000 [#1]
 storage1 kernel: [  144.749739] SMP
 storage1 kernel: [  144.749812] CPU:    0
 storage1 kernel: [  144.749813] EIP:    0060:[<c027d5cd>]    Not tainted VLI
 storage1 kernel: [  144.749814] EFLAGS: 00010286   (2.6.22-14-server #1)
 storage1 kernel: [  144.749820] EIP is at sock_release+0xd/0x80
 storage1 kernel: [  144.749822] eax: 000081ed   ebx: dfd05000   ecx: 00000000   edx: 00000000
 storage1 kernel: [  144.749825] esi: 000081ed   edi: dfd05008   ebp: f7bfde00   esp: f7bfdd50
 storage1 kernel: [  144.749827] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
 storage1 kernel: [  144.749830] Process clvmd (pid: 4712, ti=f7bfc000 task=c23f2530 task.ti=f7bfc000)
 storage1 kernel: [  144.749832] Stack: f8aac59f dfd05000 00000000 f8aac527 dfd05000 ffffff9e f787f580 f8aacba8
 storage1 kernel: [  144.749838]        f8ab32f4 00000000 00000000 00000000 c23f26f0 c200a000 c010320a c23f2530
 storage1 kernel: [  144.749843]        00000000 c23f26f0 c200a000 c010320a c23f2530 df7c26f0 df7c2530 c23f2530
 storage1 kernel: [  144.749848] Call Trace:
 storage1 kernel: [  144.749851]  [<f8aac59f>] __nodeid2con+0x1f/0x140 [dlm]
 storage1 kernel: [  144.749866]  [<f8aac527>] close_connection+0x27/0x80 [dlm]
 storage1 kernel: [  144.749877]  [<f8aacba8>] dlm_lowcomms_start+0x138/0x640 [dlm]
 storage1 kernel: [  144.749889]  [<c010320a>] __switch_to+0xaa/0x1d0
 storage1 kernel: [  144.749895]  [<c010320a>] __switch_to+0xaa/0x1d0
 storage1 kernel: [  144.749899]  [<c02f9ebe>] schedule+0x2ce/0x8c0
 storage1 kernel: [  144.749918]  [<f8aaa864>] dlm_new_lockspace+0xd4/0x7c0 [dlm]
 storage1 kernel: [  144.749926]  [<f8aab120>] dlm_scand+0x0/0x80 [dlm]
 storage1 kernel: [  144.749938]  [<c018ab32>] may_open+0x72/0x290
 storage1 kernel: [  144.749947]  [<f882cee3>] apparmor_capable+0x13/0x50 [apparmor]
 storage1 kernel: [  144.749955]  [<f8ab128c>] device_write+0x43c/0x560 [dlm]
 storage1 kernel: [  144.749972]  [<c01825ee>] vfs_write+0xbe/0x160
 storage1 kernel: [  144.749976]  [<f8ab0e50>] device_write+0x0/0x560 [dlm]
 storage1 kernel: [  144.749988]  [<c0182cf1>] sys_write+0x41/0x70
 storage1 kernel: [  144.749992]  [<c010418a>] sysenter_past_esp+0x6b/0xa1
 storage1 kernel: [  144.750000]  =======================
 storage1 kernel: [  144.750001] Code: e8 49 17 ec ff 89 c1 89 d3 eb ae 8d 76 00 e8 3b 17 ec ff 89 c1 89 d3 e9 50 ff ff ff 66 90 83 ec 0c 89 74 24 08 89 c6 89 5c 24 04 <8b> 50 08 85 d2 74 14 8b 5a 04 ff 52 08 c7 46 08 00 00 00 00 89
 storage1 kernel: [  144.750026] EIP: [<c027d5cd>] sock_release+0xd/0x80 SS:ESP 0068:f7bfdd50
```

I have tried reinstalling the machines but I get the same error. The machines are both HP Proliant DL320S models. I am running x86, not x86_64. I tried replicating the error in a VMWare with only CLVM (not DRBD and heartbeat) but here it starts up fine.

Can anybody help? Perhaps by interpreting the kernel oops?

---

### Post by drzero on 2008-02-19
Okay, I found the problem - even though it was definitely NOT evident from any of the errormessages I found, it turns out the cluster did not have quorum (I found out about this through cman_tool). The reason for this was that the hostname resolves not to the real IP (which is listed in my DNS) but to 127.0.1.1. After removing the 127.0.1.1 line from /etc/hosts and restarting cman, clvmd starts up without any problems.

---

