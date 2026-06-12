---
title: "NFS Mount Problems - cannot create RPC client"
date: 2009-10-28
forum: Server Platforms
---

### Post by y@w on 2009-10-28
Hello,

I'm struggling with a problematic NFS client and can't seem to figure out what's going on.

First, some history: I logged in to one of our web servers this morning to discover that it was swapping big time. After looking into it, it looks like the memory was being used for a whole bunch of copies of our python scripts that monitor the server trying to check the disk space usage on one of the NFS mounts. I also discovered that the MySQL dumps that we dump to this particular NFS mount were still running (they start at midnight and were running well after 8). I killed off all these processes and managed to get the NFS mount point unmounted. Now, I can't seem to get it mounted again.



Mount requests just throw "server not responding, timed out" in /var/log/syslog. If I run mount with -v I get 
```
mount.nfs: internal error

```

I've checked the logs on the "server-side" and it says that the request is authenticated (this worked for months before!). 

In dmesg, it throws this:
```
[7087238.697609] ------------[ cut here ]------------
[7087238.697836] kernel BUG at /build/buildd/linux-2.6.24/net/sunrpc/rpcb_clnt.c:322!
[7087238.698128] invalid opcode: 0000 [8] SMP 
[7087238.698357] CPU 0 
[7087238.698530] Modules linked in: vmmemctl iptable_filter ip_tables x_tables quota_v2 ipv6 vmhgfs reiserfs lp loop nfs lockd nfs_acl sunrpc parport_pc parport psmouse serio_raw evdev container button shpchp pcspkr ac i2c_piix4 i2c_core pci_hotplug intel_agp ext3 jbd mbcache sr_mod cdrom ata_generic pata_acpi sg sd_mod floppy ata_piix e1000 mptspi mptscsih mptbase scsi_transport_spi libata scsi_mod dm_mirror dm_snapshot dm_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse vmxnet
[7087238.702041] Pid: 2097, comm: mount.nfs Tainted: G      D 2.6.24-23-server #1
[7087238.702376] RIP: 0010:[<ffffffff882668b2>]  [<ffffffff882668b2>] :sunrpc:rpcb_getport_async+0x272/0x3c0
[7087238.702807] RSP: 0018:ffff8101005b3848  EFLAGS: 00010287
[7087238.703020] RAX: ffffffff882845c0 RBX: ffff8101e91eae00 RCX: ffffffff802884a3
[7087238.703357] RDX: ffffffff882845c0 RSI: 0000000000011200 RDI: ffff81005aecca80
[7087238.703693] RBP: ffff8100dcd72000 R08: 0000000000000000 R09: ffff81005aecca80
[7087238.704034] R10: 0000000000000000 R11: ffffffff88266640 R12: ffff8100838bb200
[7087238.704370] R13: ffff81005aecca80 R14: ffff8101005b3b28 R15: ffff8101e91a3400
[7087238.704708] FS:  00007f5530de36e0(0000) GS:ffffffff805c5000(0000) knlGS:0000000000000000
[7087238.705109] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[7087238.705329] CR2: 0000000000619000 CR3: 0000000141cef000 CR4: 00000000000006e0
[7087238.705668] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[7087238.706014] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[7087238.706355] Process mount.nfs (pid: 2097, threadinfo ffff8101005b2000, task ffff8100dccf57d0)
[7087238.706712] Stack:  ffff81005aecca80 ffffffff88284460 ffff8100d24c33b0 ffffffff882578c0
[7087238.707262]  0000000000000000 ffff81005aecca80 ffffffff8826c390 ffff81005aeccb70
[7087238.707758]  ffff8101005b3b28 ffffffff8825db3b ffffffff8826c390 ffff81005aecca80
[7087238.708316] Call Trace:
[7087238.708634]  [<ffffffff882578c0>] :sunrpc:call_allocate+0xc0/0x1b0
[7087238.708875]  [<ffffffff8825db3b>] :sunrpc:__rpc_execute+0x6b/0x290
[7087238.709110]  [<ffffffff88256f86>] :sunrpc:rpc_do_run_task+0x76/0xd0
[7087238.709346]  [<ffffffff88257045>] :sunrpc:rpc_call_sync+0x15/0x40
[7087238.709578]  [<ffffffff882570bd>] :sunrpc:rpc_ping+0x4d/0x70
[7087238.709806]  [<ffffffff88258449>] :sunrpc:rpc_bind_new_program+0x69/0x90
[7087238.710058]  [<ffffffff882a8414>] :nfs:nfs_init_server_aclclient+0x34/0x50
[7087238.710278]  [<ffffffff882a9705>] :nfs:nfs_create_server+0x195/0x540
[7087238.710278]  [<ffffffff8825d459>] :sunrpc:rpc_put_task+0x99/0xc0
[7087238.710278]  [<ffffffff882baa6b>] :nfs:nfs_mount+0x10b/0x200
[7087238.711022]  [<ffffffff882b2513>] :nfs:nfs_get_sb+0x233/0x790
[7087238.711251]  [<ffffffff8028c2cd>] __alloc_pages+0x9d/0x3d0
[7087238.711468]  [<ffffffff802ce328>] alloc_vfsmnt+0xd8/0x110
[7087238.711527]  [<ffffffff802b765c>] vfs_kern_mount+0xcc/0x160
[7087238.711919]  [<ffffffff802b7753>] do_kern_mount+0x53/0x110
[7087238.712138]  [<ffffffff802ceec6>] do_mount+0x546/0x810
[7087238.712351]  [<ffffffff80296c7b>] handle_mm_fault+0x3db/0x800
[7087238.712572]  [<ffffffff80287f38>] filemap_fault+0x188/0x390
[7087238.712775]  [<ffffffff80352351>] __up_read+0x21/0xb0
[7087238.713016]  [<ffffffff80473890>] do_page_fault+0x1d0/0x840
[7087238.713239]  [<ffffffff80471c69>] error_exit+0x0/0x51
[7087238.713452]  [<ffffffff802cd7ca>] copy_mount_options+0x10a/0x180
[7087238.713677]  [<ffffffff802cf8db>] sys_mount+0x9b/0x100
[7087238.713891]  [<ffffffff8020c39e>] system_call+0x7e/0x83
[7087238.714110] 
[7087238.714268] 
[7087238.714268] Code: 0f 0b eb fe 8b 85 b8 00 00 00 0f b7 b7 48 01 00 00 48 c7 c2 
[7087238.715573] RIP  [<ffffffff882668b2>] :sunrpc:rpcb_getport_async+0x272/0x3c0
[7087238.715954]  RSP <ffff8101005b3848>
[7087238.716163] ---[ end trace 70677383d762dfdd ]---

```


Searching for some text out of the stack trace, I found [this thread]("http://osdir.com/ml/linux-kernel/2009-08/msg06762.html") which suggested turning on debug for nfs_client and running the mount again. When I did that, I found this in /var/log/messages:

```
Oct 28 15:31:44 host kernel: [7088246.601415] --> nfs_init_server()
Oct 28 15:31:44 host kernel: [7088246.601597] --> nfs_get_client(172.16.0.141,172.16.0.141:0,3)
Oct 28 15:31:44 host kernel: [7088246.601766] --> nfs_get_client() = ffff81002bf2d600 [new]
Oct 28 15:31:50 host kernel: [7088252.424210] --> nfs_init_server()
Oct 28 15:31:50 host kernel: [7088252.424419] --> nfs_get_client(172.16.0.141,172.16.0.141:0,3)
Oct 28 15:34:44 host kernel: [7088426.400271] nfs: server 172.16.0.141 not responding, timed out
Oct 28 15:34:44 host kernel: [7088426.400564] nfs_create_rpc_client: cannot create RPC client. Error = -5
Oct 28 15:34:44 host kernel: [7088426.400833] <-- nfs_init_client() = xerror -5
Oct 28 15:34:44 host kernel: [7088426.401035] --> nfs_put_client({2})
Oct 28 15:34:44 host kernel: [7088426.401219] <-- nfs_init_server() = xerror -5
Oct 28 15:34:44 host kernel: [7088426.401418] --> nfs_free_server()
Oct 28 15:34:44 host kernel: [7088426.401808] <-- nfs_free_server()
Oct 28 15:34:44 host kernel: [7088426.402006] --> nfs_put_client({1})
Oct 28 15:34:44 host kernel: [7088426.402216] --> nfs_free_client(3)
Oct 28 15:34:44 host kernel: [7088426.402349] <-- nfs_free_client()
Oct 28 15:34:44 host kernel: [7088426.402478] <-- nfs_init_server() = error -5
Oct 28 15:34:44 host kernel: [7088426.402622] --> nfs_free_server()
Oct 28 15:34:44 host kernel: [7088426.402754] <-- nfs_free_server()

```

I also tried this to a different NFS server on our network with the same result.

I'm pretty well convinced that it's a client-side rpc problem, but bouncing nfs-common and portmap does nothing for me. I also tried to bounce the nfs services on the server.

Anybody else know of something that I can try? I'm stumped..

---

### Post by y@w on 2009-10-28
I also found something else.. /proc/mounts contains something somewhat curious. Not sure if this is normal, but it contains this at the end:

```
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0

```

I don't think that's normal.. :(

Both client and server are Ubuntu 8.04, btw.

---

