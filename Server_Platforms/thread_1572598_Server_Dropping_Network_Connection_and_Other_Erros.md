---
title: "Server Dropping Network Connection and Other Erros"
date: 2010-09-11
forum: Server Platforms
---

### Post by rmccarri on 2010-09-11
Hi Everyone,
I set up the web/backup server for our department and I'm having some major issues.  Firstly, the server seems to be dropping the network connection periodically.  I checked all of the logs and it appeared to be an IP6 issue as the only message that seemed to correlate with it was "eth0: no IPv6 routers present" in syslog.  I added "ipv6.disable=1" to my boot options in menu.lst and this seemed to take care of the problem.

However, I woke up this morning and the server was back down.  This didn't seem to take care of the problem.  It seems to occur when my automatic backup scripts go through.  I have several BASH backup scripts that use rysnc over SSH to backup several computers to the server and the server to my desktop at home.  I was able to trigger the problem a couple of times running the backup script this morning.

Now, I'm getting the following error when running the script, instead of losing the network connection:

```
Sep 11 10:22:40 chemistry kernel: [  396.892699] BUG: unable to handle kernel NULL pointer dereference at 0000000000000118
Sep 11 10:22:40 chemistry kernel: [  396.892715] IP: [<ffffffff811426c0>] __dentry_open+0x240/0x370
Sep 11 10:22:40 chemistry kernel: [  396.892728] PGD 1113d5067 PUD 11458c067 PMD 0 
Sep 11 10:22:40 chemistry kernel: [  396.892737] Oops: 0000 [#1] SMP 
Sep 11 10:22:40 chemistry kernel: [  396.892743] last sysfs file: /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
Sep 11 10:22:40 chemistry kernel: [  396.892750] CPU 1 
Sep 11 10:22:40 chemistry kernel: [  396.892754] Modules linked in: ipt_REJECT ipt_LOG xt_limit xt_tcpudp ipt_addrtype fbcon tileblit font xt_state bitblit softcursor vga16fb vgastate snd_hda_codec_analog ip6_tables tpm_infineon nf_nat_irc nf_conntrack_irc nf_nat_ftp nf_nat nouveau snd_hda_intel nf_conntrack_ipv4 snd_hda_codec nf_defrag_ipv4 ttm nf_conntrack_ftp nf_conntrack drm_kms_helper snd_hwdep drm snd_pcm snd_timer snd iptable_filter i2c_algo_bit soundcore ip_tables snd_page_alloc x_tables tpm_tis ppdev parport_pc psmouse tpm lp parport serio_raw tpm_bios intel_agp joydev hid_logitech ff_memless floppy usbhid hid e1000e
Sep 11 10:22:40 chemistry kernel: [  396.892858] Pid: 2539, comm: rsync Not tainted 2.6.32-24-server #39-Ubuntu HP Compaq dc7800p Convertible Minitower
Sep 11 10:22:40 chemistry kernel: [  396.892865] RIP: 0010:[<ffffffff811426c0>]  [<ffffffff811426c0>] __dentry_open+0x240/0x370
Sep 11 10:22:40 chemistry kernel: [  396.892873] RSP: 0018:ffff880100fb3d58  EFLAGS: 00010206
Sep 11 10:22:40 chemistry kernel: [  396.892878] RAX: 0000000000000000 RBX: ffff88011581e300 RCX: 0000000000000001
Sep 11 10:22:40 chemistry kernel: [  396.892885] RDX: ffff88011581e300 RSI: ffff880037982780 RDI: ffff8800379827f0
Sep 11 10:22:40 chemistry kernel: [  396.892890] RBP: ffff880100fb3da8 R08: 0000000000000000 R09: ffff880114f94180
Sep 11 10:22:40 chemistry kernel: [  396.892895] R10: ffff8800dea6b780 R11: 0000000000000000 R12: ffff880037982780
Sep 11 10:22:40 chemistry kernel: [  396.892901] R13: ffff8800dea6b780 R14: ffffffff811d8260 R15: ffff8800dead9020
Sep 11 10:22:40 chemistry kernel: [  396.892907] FS:  00007f24d31f0700(0000) GS:ffff880005880000(0000) knlGS:0000000000000000
Sep 11 10:22:40 chemistry kernel: [  396.892913] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Sep 11 10:22:40 chemistry kernel: [  396.892917] CR2: 0000000000000118 CR3: 0000000114583000 CR4: 00000000000006e0
Sep 11 10:22:40 chemistry kernel: [  396.892923] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Sep 11 10:22:40 chemistry kernel: [  396.892928] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Sep 11 10:22:40 chemistry kernel: [  396.892934] Process rsync (pid: 2539, threadinfo ffff880100fb2000, task ffff8800379cc4d0)
Sep 11 10:22:40 chemistry kernel: [  396.892940] Stack:
Sep 11 10:22:40 chemistry kernel: [  396.892943]  ffff880100fb3d68 ffffffff81253dbf ffff880114f94180 ffffffff8114e90f
Sep 11 10:22:40 chemistry kernel: [  396.892952] <0> ffff8800dead9020 ffff880037982780 0000000000008001 0000000000000024
Sep 11 10:22:40 chemistry kernel: [  396.892962] <0> ffff880100fb3e28 0000000000000000 ffff880100fb3dc8 ffffffff81142907
Sep 11 10:22:40 chemistry kernel: [  396.892974] Call Trace:
Sep 11 10:22:40 chemistry kernel: [  396.892981]  [<ffffffff81253dbf>] ? security_inode_permission+0x1f/0x30
Sep 11 10:22:40 chemistry kernel: [  396.892988]  [<ffffffff8114e90f>] ? inode_permission+0xaf/0xd0
Sep 11 10:22:40 chemistry kernel: [  396.892994]  [<ffffffff81142907>] nameidata_to_filp+0x57/0x70
Sep 11 10:22:40 chemistry kernel: [  396.893000]  [<ffffffff81152b4a>] do_filp_open+0x2da/0xba0
Sep 11 10:22:40 chemistry kernel: [  396.893006]  [<ffffffff81148b94>] ? cp_new_stat+0xe4/0x100
Sep 11 10:22:40 chemistry kernel: [  396.893012]  [<ffffffff8115e5ba>] ? alloc_fd+0x10a/0x150
Sep 11 10:22:40 chemistry kernel: [  396.893017]  [<ffffffff81142309>] do_sys_open+0x69/0x170
Sep 11 10:22:40 chemistry kernel: [  396.893023]  [<ffffffff81142450>] sys_open+0x20/0x30
Sep 11 10:22:40 chemistry kernel: [  396.893030]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
Sep 11 10:22:40 chemistry kernel: [  396.893034] Code: 48 85 c0 74 0d 4c 8b 70 60 4d 85 f6 0f 85 e0 fe ff ff 49 8b 84 24 b8 00 00 00 41 81 64 24 38 3f fc ff ff 49 8d 7c 24 70 48 8b 00 <48> 8b b0 18 01 00 00 e8 84 b9 fb ff 41 f6 44 24 39 40 0f 84 36 
Sep 11 10:22:40 chemistry kernel: [  396.893121] RIP  [<ffffffff811426c0>] __dentry_open+0x240/0x370
Sep 11 10:22:40 chemistry kernel: [  396.893128]  RSP <ffff880100fb3d58>
Sep 11 10:22:40 chemistry kernel: [  396.893131] CR2: 0000000000000118
Sep 11 10:22:40 chemistry kernel: [  396.893179] ---[ end trace 0c3cde63a7663c43
```

I tried booting with a previous kernel to see if that was the problem and I'm still getting this error.

I've searched through all of the logs that I could think of to try to track down any software based problems and I just don't see anything.  In the past, whenever I've run into such serious with a Linux box that popped up out of nowhere, it's always been a hardware failure.  Does anyone have any troubleshooting suggestions?  I've currently disabled all of the backup scripts and I'm going to see if it lasts through the weekend.

Thanks in advanced for any help!
Rob

---

### Post by rmccarri on 2010-09-11
Just to give some more information, I just found this error that seems that it might correspond to the other issues:

```
Sep 11 10:28:45 chemistry kernel: [    0.385644] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 11 10:28:45 chemistry kernel: [    0.385750] ACPI Error (dsfield-0143): [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS
Sep 11 10:28:45 chemistry kernel: [    0.385755] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff880117a3eb20), AE_ALREADY_EXISTS
Sep 11 10:28:45 chemistry kernel: [    0.385779] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
Sep 11 10:28:45 chemistry kernel: [    0.385859] ACPI Error (dsfield-0143): [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS
Sep 11 10:28:45 chemistry kernel: [    0.385864] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff880117a3eb20), AE_ALREADY_EXISTS
Sep 11 10:28:45 chemistry kernel: [    0.385884] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
Sep 11 10:28:45 chemistry kernel: [    0.385973] ACPI Error (dsfield-0143): [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS
Sep 11 10:28:45 chemistry kernel: [    0.385978] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff880117a3eb20), AE_ALREADY_EXISTS
Sep 11 10:28:45 chemistry kernel: [    0.385997] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
Sep 11 10:28:45 chemistry kernel: [    0.386072] ACPI Error (dsfield-0143): [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS
Sep 11 10:28:45 chemistry kernel: [    0.386076] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff880117a3eb20), AE_ALREADY_EXISTS
Sep 11 10:28:45 chemistry kernel: [    0.386095] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)

```

---

### Post by rmccarri on 2010-10-22
I ended up figuring this out.  It was a hardware issue.  One of the ram chips had gone bad and when the server was really crunching a lot of data, it would get all kinds of errors.

---

